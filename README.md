# Market Talk V10 — React + Vite

เกมฝึกภาษาจีนพร้อม Pinyin และภาษาอังกฤษ ผ่านร้านค้า 7 ประเภท ร้านละ 50 รายการ (350 รายการ) แสดงสินค้า 6 รายการต่อหน้า พร้อมภาพพื้นหลังร้านค้าแยกตามประเภท

## ใช้งานบนคอมพิวเตอร์

ต้องมี Node.js 20.19+ หรือ 22+

```bash
npm install
npm run dev
```

เปิด URL ที่ Vite แสดง (ปกติ http://localhost:5173)

ทดสอบ build:

```bash
npm run build
npm run preview
```

## อัปโหลด GitHub Pages

1. สร้าง GitHub repository ใหม่ เช่น `market-talk-react` และเลือก Public
2. แตกไฟล์ ZIP แล้ว **อัปโหลดไฟล์และโฟลเดอร์ภายใน** ไปที่ root ของ repository (รวม `.github`, `src`, `public`, `package.json`, `vite.config.js` และ `index.html`)
3. ตรวจสอบว่า branch ชื่อ `main`
4. ไปที่ **Settings → Pages → Build and deployment → Source: GitHub Actions**
5. Push หรือ commit โค้ดแล้วรอ workflow **Deploy Market Talk React to GitHub Pages** ทำงาน
6. เปิด `https://USERNAME.github.io/REPOSITORY/`

`vite.config.js` ตั้ง `base: './'` เพื่อรองรับ GitHub Pages ทั้งแบบ repository site และ custom domain

**หมายเหตุ:** ไม่สามารถอัปโหลด `index.html` ของโปรเจกต์ React ไป GitHub Pages เพียงไฟล์เดียวได้ ต้องผ่าน `npm run build` หรือ GitHub Actions ที่ให้มาด้วย

## โครงสร้าง

- `src/App.jsx` เกม React และ logic
- `src/styles.css` ดีไซน์ responsive
- `src/data/catalogs.json` ข้อมูลสินค้า 350 รายการจาก Market Talk V9
- `public/backgrounds/*.svg` ภาพพื้นหลังแต่ละร้าน (ไม่ต้องต่ออินเทอร์เน็ตเพื่อโหลดภาพ)
- `.github/workflows/deploy.yml` workflow สำหรับ GitHub Pages

เสียงอ่านใช้ Web Speech API ของเบราว์เซอร์ เสียงภาษาจีน/อังกฤษขึ้นกับ voice ที่ติดตั้งในอุปกรณ์ และฟอนต์จะ fallback เป็นฟอนต์เครื่องหากไม่มีอินเทอร์เน็ต
