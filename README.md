# Assignment-2-Stacks-and-Queues

โค้ดนี้เป็นโค้ดทดสอบ (unit test) สำหรับฟังก์ชัน bracket_check ซึ่งเป็นฟังก์ชันที่มีการตรวจสอบว่าวงเล็บที่ปรากฏในสตริงที่กำหนดนั้นถูกปิดทุกตัวอย่างถูกต้องหรือไม่

ในโค้ดนี้มีการใช้ unittest ซึ่งเป็นโมดูลที่ใช้สร้างและรันเทสใน Python

โค้ดทดสอบมีรายละเอียดดังนี้:

test_no_error: ทดสอบสำหรับสตริง "[{(Hello)}]" ซึ่งคาดหวังว่าไม่มีข้อผิดพลาดในการปิดวงเล็บ ดังนั้น isError ควรจะเป็น False

test_error: ทดสอบสำหรับสตริง "[{(Hello})]" ซึ่งมีข้อผิดพลาดในการปิดวงเล็บ (มีวงเล็บที่ไม่ถูกปิด) ดังนั้น isError ควรจะเป็น True

test_error_unmatched_open: ทดสอบสำหรับสตริง "[{(Hello" ซึ่งมีวงเล็บที่เปิดแต่ไม่มีการปิด ดังนั้น isError ควรจะเป็น True

test_error_unmatched_close: ทดสอบสำหรับสตริง "Hello)(" ซึ่งมีวงเล็บที่ปิดแต่ไม่มีการเปิด ดังนั้น isError ควรจะเป็น True

จากรายละเอียดทั้งหมดนี้ เราสามารถเข้าใจว่า bracket_check ควรจะเป็นฟังก์ชันที่ตรวจสอบว่าวงเล็บในสตริงถูกปิดทุกตัวอย่างถูกต้องหรือไม่ และคืนค่า True ถ้ามีข้อผิดพลาดและ False ถ้าไม่มีข้อผิดพลาด

import unittest
from bracket_check import bracket_check


class MyTestCase(unittest.TestCase):
    def test_no_error(self):
        test_string = '[{(Hello)}]'
        isError, location = bracket_check(test_string)
        self.assertEqual(isError, False)

    def test_error_1(self):
        test_string = '[{(Hello})]'
        isError, location = bracket_check(test_string)
        self.assertEqual(isError, True)

    def test_error_2(self):
        test_string = '[{(Hello'
        isError, location = bracket_check(test_string)
        self.assertEqual(isError, True)

    def test_error_3(self):
        test_string = 'Hello)('
        isError, location = bracket_check(test_string)
        self.assertEqual(isError, True)

    def test_error_4(self):
        test_string = '{}{'
        isError, location = bracket_check(test_string)
        self.assertEqual(isError, True)
        self.assertEqual([2], location)


if __name__ == '__main__':
    unittest.main()
