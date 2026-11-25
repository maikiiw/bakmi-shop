# บะหมี่ซด ซด – แลนดิ้งเพจขายบะหมี่กึ่งสำเร็จรูป (โจทย์ 006)

## โครงสร้างไฟล์
```
index.html        แลนดิ้งเพจ + ฟอร์มสั่งซื้อ
pack.html         หน้าหลังบ้าน: หยิบสินค้า → แพ็ค → พิมพ์ใบจ่าหน้าพัสดุ
app.js            โหลดข้อมูลจาก Google Sheet (มีไฟล์ CSV สำรอง) + จัดการออเดอร์
style.css
data/products.csv ข้อมูลสำรอง (โครงสร้างเดียวกับ Google Sheet)
images/           โฟลเดอร์เก็บรูปสินค้า (แยกจากโค้ด) bkm-001.svg ... bkm-003.svg
```

## 1) ทำ Google Sheet
1. สร้าง Google Sheet ใหม่ แถวแรกใส่หัวคอลัมน์: `sku, name, desc, price, image, stock`
2. คัดลอกข้อมูลจาก `data/products.csv` ไปวาง (มี 3 SKU) – คอลัมน์ `image` คือ path รูปในโฟลเดอร์ `images/`
3. เมนู **ไฟล์ → แชร์ → เผยแพร่ไปยังเว็บ** → เลือกแผ่นงาน และรูปแบบ **ค่าที่คั่นด้วยเครื่องหมายจุลภาค (.csv)** → เผยแพร่ → คัดลอกลิงก์
4. เปิด `app.js` วางลิงก์ที่ `const SHEET_CSV_URL = "..."` แล้วบันทึก

## 2) ขึ้น GitHub
```bash
cd bakmi-shop
git init
git add .
git commit -m "bakmi landing page"
git branch -M main
git remote add origin https://github.com/<ชื่อผู้ใช้>/bakmi-shop.git
git push -u origin main
```
(หรือสร้าง repo บน github.com แล้วลากไฟล์ทั้งหมดอัปโหลดผ่านเว็บ **Add file → Upload files**)

## 3) ขึ้นโดเมน Vercel
1. เข้า vercel.com → Login with GitHub
2. **Add New → Project** → เลือก repo `bakmi-shop` → **Import**
3. Framework Preset = **Other** (ไม่ต้องตั้งค่า build) → **Deploy**
4. ได้โดเมน `https://bakmi-shop-xxxx.vercel.app` – ส่งลิงก์นี้เป็นคำตอบ

## หมายเหตุ
- ออเดอร์เก็บใน localStorage ของเบราว์เซอร์ (เหมาะกับงานตัวอย่าง) หน้า `pack.html` ต้องเปิดในเบราว์เซอร์เครื่องเดียวกับที่สั่ง
- เพิ่มสินค้าใหม่ = เพิ่มแถวใน Google Sheet + ใส่รูปในโฟลเดอร์ `images/`
