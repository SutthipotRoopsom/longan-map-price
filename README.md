# 🍈 Longan Price Map - แผนที่ราคาลำไยภาคเหนือไทย

ระบบติดตามและบันทึกราคาลำไยแบบ Real-time บนแผนที่อินเทอร์แอกทีฟ

## 👨‍💻 ผู้พัฒนา

- **ชื่อ-นามสกุล:** สุทธิพจน์ รูปโสม
- **รหัสนักศึกษา:** 6604101391
- **วิชา:** Cloud Computing & DevOps

---

## 🎯 คุณสมบัติหลัก

### 1. แผนที่แบบอินเทอร์แอกทีฟ
- ใช้ **OpenStreetMap API** และ **Leaflet.js**
- โฟกัสพื้นที่ภาคเหนือของประเทศไทย
- Zoom level เริ่มต้นที่ 8 (แสดงภาคเหนือทั้งหมด)

### 2. ระบบจัดการข้อมูล
- ✅ เพิ่มข้อมูลราคาลำไยผ่านฟอร์ม
- ✅ ระบุตำแหน่งด้วยจังหวัด หรือพิกัด Latitude/Longitude
- ✅ Geocoding อัตโนมัติ (แปลงชื่อสถานที่เป็นพิกัด)
- ✅ แคชพิกัดใน Local Storage เพื่อประสิทธิภาพ

### 3. การแสดงผลบนแผนที่
- 📍 Multiple Markers ด้วยไอคอนสีเขียว
- 🏷️ Label แสดงชื่อผู้พัฒนาและรหัสนักศึกษาบนทุก Marker
- 💬 Pop-up แสดงรายละเอียดเมื่อคลิก (จังหวัด, สถานที่, ราคา, วันที่)
- 📊 Dashboard สถิติ (จำนวนจุด, ราคาเฉลี่ย, อัพเดทล่าสุด)

### 4. UI/UX สวยงาม
- 🎨 Tailwind CSS Framework
- 🌈 Gradient Design สีม่วง-น้ำเงิน
- ✨ Animations และ Hover Effects
- 📱 Responsive Design (รองรับมือถือ)
- 🇹🇭 ฟอนต์ Kanit สำหรับภาษาไทย

---

## 🛠️ เทคโนโลยีที่ใช้

| เทคโนโลジี | รายละเอียด |
|-----------|-----------|
| **Frontend** | HTML5, JavaScript (ES6+) |
| **CSS Framework** | Tailwind CSS |
| **Map Library** | Leaflet.js 1.9.4 |
| **Map Data** | OpenStreetMap API |
| **Geocoding** | Nominatim API |
| **Font** | Google Fonts (Kanit) |
| **Container** | Docker + Nginx |
| **CI/CD** | Docker Compose |

---

## 🚀 การติดตั้งและรัน

### วิธีที่ 1: รันด้วย Docker (แนะนำ)

#### Pull จาก Docker Hub
```bash
# Pull image
docker pull stawan15/longan-map:latest

# Run container
docker run -d -p 8081:80 --name longan-map stawan15/longan-map:latest

# เปิดเบราว์เซอร์
# http://localhost:8081
```

#### Build จาก Source
```bash
# Clone repository
git clone https://github.com/SutthipotRoopsom/my-quasar-express-app.git
cd my-quasar-express-app

# Build ด้วย Docker Compose
docker compose up -d --build longan-map

# เปิดเบราว์เซอร์
# http://localhost:8081
```

### วิธีที่ 2: รันแบบ Standalone (ไม่ใช้ Docker)

```bash
# ไปที่โฟลเดอร์ longan-map
cd longan-map

# เปิดไฟล์ HTML ด้วยเบราว์เซอร์
# หรือใช้ web server
python3 -m http.server 8000

# เปิดเบราว์เซอร์
# http://localhost:8000/longan_map.html
```

---

## 📖 วิธีใช้งาน

### 1. เพิ่มข้อมูลราคาลำไย

1. **เลือกจังหวัด** จาก dropdown (8 จังหวัดภาคเหนือ)
2. **ระบุสถานที่** (ตลาด/อำเภอ) - ไม่บังคับ
3. **กรอกราคา** (บาท/กก.)
4. **เลือกวันที่สำรวจ**
5. **(ทางเลือก)** ระบุพิกัด Latitude/Longitude ถ้าทราบ
6. คลิก **"เพิ่มข้อมูลลงแผนที่"**

### 2. ดูข้อมูลบนแผนที่

- **จุดสีเขียว** = ตำแหน่งที่มีข้อมูลราคาลำไย
- **Label บนจุด** = แสดงชื่อผู้พัฒนาและรหัสนักศึกษา
- **คลิกที่จุด** = แสดง Pop-up รายละเอียด (ราคา, วันที่, พิกัด)

### 3. จัดการข้อมูล

- **ลบทั้งหมด:** คลิกปุ่ม "🗑️ ล้างทั้งหมด"
- **ดูสถิติ:** Dashboard ด้านบนแสดงจำนวนจุด, ราคาเฉลี่ย

---

## 🗂️ โครงสร้างโปรเจกต์

```
my-quasar-express-app/
├── frontend/                 # Quasar Frontend
├── backend/                  # Express API
├── longan-map/              # Longan Map Application
│   ├── longan_map.html      # Main HTML file
│   ├── Dockerfile           # Docker configuration
│   ├── .dockerignore        # Docker ignore rules
│   └── README.md            # Documentation
├── docker-compose.yml       # Docker Compose config
└── README.md               # Main documentation
```

---

## 🐳 Docker Commands

### Build & Run
```bash
# Build image
docker compose build longan-map

# Run container
docker compose up -d longan-map

# ดู logs
docker compose logs -f longan-map

# หยุด container
docker compose down
```

### Push to Docker Hub
```bash
# Tag image
docker tag my-quasar-express-app-longan-map:latest stawan15/longan-map:latest

# Login
docker login

# Push
docker push stawan15/longan-map:latest
```

### Manage Containers
```bash
# ดูสถานะ
docker compose ps

# Restart
docker compose restart longan-map

# ลบ container และ volume
docker compose down -v
```

---

## 📊 ตัวอย่างข้อมูล

เมื่อเปิดครั้งแรก จะมีข้อมูลตัวอย่าง 3 จุด:

| จังหวัด | สถานที่ | ราคา (บาท/กก.) | วันที่ |
|---------|---------|----------------|--------|
| เชียงใหม่ | ตลาดเมือง | 35.50 | 25 พ.ย. 2567 |
| ลำพูน | ตลาดสด | 32.00 | 26 พ.ย. 2567 |
| เชียงราย | ตลาดกลาง | 38.00 | 27 พ.ย. 2567 |

---

## 🌐 Links

- **Docker Hub:** https://hub.docker.com/r/stawan15/longan-map
- **GitHub Repository:** https://github.com/SutthipotRoopsom/my-quasar-express-app
- **Live Demo:** http://localhost:8081 (หลังรัน Docker)

---

## 🔧 การแก้ไขและพัฒนา

### แก้ไขโค้ด
```bash
# แก้ไข longan_map.html
cd longan-map
code longan_map.html

# Rebuild
cd ..
docker compose down
docker compose up -d --build longan-map
```

### เพิ่มจังหวัดใหม่
แก้ไขใน `longan_map.html` บรรทัด ~69:
```javascript
const provinceCoords = {
  'เชียงใหม่': [18.7883, 98.9853],
  'จังหวัดใหม่': [lat, lng],  // เพิ่มที่นี่
  // ...
};
```

---

## ⚙️ Configuration

### เปลี่ยน Port
แก้ไขใน `docker-compose.yml`:
```yaml
services:
  longan-map:
    ports:
      - "8082:80"  # เปลี่ยนจาก 8081 เป็น 8082
```

### เปลี่ยนสีธีม
แก้ไขใน `longan_map.html` section `<style>`:
```css
.gradient-bg {
  background: linear-gradient(135deg, #your-color-1 0%, #your-color-2 100%);
}
```

---

## 🐛 Troubleshooting

### ปัญหา: Port ชน
```bash
# เปลี่ยน port ใน docker-compose.yml หรือ
docker run -d -p 8082:80 stawan15/longan-map:latest
```

### ปัญหา: Geocoding ช้า
- ระบบใช้ Local Storage แคชพิกัดอัตโนมัติ
- ถ้าต้องการเคลียร์แคช: เปิด Browser DevTools → Application → Local Storage → ลบ `geoCache`

### ปัญหา: แผนที่ไม่แสดง
- ตรวจสอบ internet connection (ต้องโหลด OpenStreetMap tiles)
- เช็ค browser console (F12) หา error

---

## 📝 TODO / Features ในอนาคต

- [ ] Export ข้อมูลเป็น CSV/Excel
- [ ] Filter ข้อมูลตามวันที่และราคา
- [ ] กราฟแสดงแนวโน้มราคา
- [ ] Backend API สำหรับบันทึกข้อมูลถาวร
- [ ] Authentication และ Multi-user
- [ ] Mobile App version

---

## 📄 License

MIT License - ใช้งานได้อย่างอิสระเพื่อการศึกษา

---

## 🙏 Acknowledgments

- **OpenStreetMap** - ข้อมูลแผนที่
- **Leaflet.js** - Map library
- **Tailwind CSS** - CSS framework
- **Nominatim** - Geocoding service
- **อาจารย์ผู้สอน** - แนะนำและให้คำปรึกษา
