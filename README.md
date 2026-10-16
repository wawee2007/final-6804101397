# Playwright Final Exam

โปรเจกต์ทดสอบเว็บไซต์ https://www.saucedemo.com/ ตามโจทย์สอบ 6 ข้อ

## Test cases

- `tests/unit/UT-01.spec.ts` — Login Form Validation (3 test cases)
- `tests/unit/UT-02.spec.ts` — Add to Cart / Remove button state
- `tests/integration/IT-01.spec.ts` — Real Login + browser-level Inventory Stub
- `tests/integration/IT-02.spec.ts` — Driver login state + Real Inventory and Cart
- `tests/system/ST-01.spec.ts` — Complete purchase of two products
- `tests/system/ST-02.spec.ts` — Checkout validation and recovery

## Real and Stub/Driver explanation

- **IT-01 Real:** Login จริงผ่านหน้า SauceDemo และตรวจสอบว่าเข้าสู่ `inventory.html`
- **IT-01 Stub:** หลัง Login ใช้ `page.setContent()` สร้าง DOM จำลอง Inventory ที่มี `Mock Inventory Ready`, `Mock Backpack`, และ `Mock Bike Light` ไม่ได้ทดสอบ Inventory implementation ภายในเว็บจริง
- **IT-02 Driver:** ฟังก์ชัน `driverOpenInventory()` สร้าง BrowserContext, เพิ่ม Cookie `session-username` และเตรียม `sessionStorage` ที่ SauceDemo ใช้สำหรับสถานะผู้ใช้ ก่อนเปิด `inventory.html` โดยตรงโดยไม่กรอก Login Form
- **IT-02 Real:** หลัง Driver เตรียมสถานะแล้ว Inventory, ปุ่มเพิ่มสินค้า และ Cart เป็นหน้าเว็บจริง

## Install

```bash
npm install
npx playwright install chromium
```

## Run all tests

```bash
npx playwright test
```

## View HTML report

```bash
npx playwright show-report
```

## Reports

Playwright config สร้าง HTML report ใน `playwright-report/` และ JSON report ใน `reports/results.json` เมื่อรันทดสอบ
