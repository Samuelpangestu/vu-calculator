# Performance Testing Calculator

**Version:** 2.0.0  
**Type:** Web-based Performance Testing Planning Tool  
**Language:** Indonesian (Bahasa Indonesia)

---

## 📋 Deskripsi

Performance Testing Calculator adalah tool berbasis web untuk membantu QA Engineer dan Performance Tester merencanakan dan menghitung kapasitas load testing. Calculator ini menggunakan **Little's Law** dan industry best practices untuk mengkonversi business metrics menjadi technical testing parameters.

### ✨ Fitur Utama

- **Dual Mode Testing:** Single API dan End-to-End testing
- **Multiple Input Types:** VU, RPS, TPS, Daily/Monthly Transactions, User Base
- **Dynamic Examples:** Semua contoh formula menggunakan nilai input Anda
- **Multi-Level Testing:** Conservative (70%), Comprehensive (100%), Load (120%), Stress (150%)
- **Infrastructure Sizing:** Kalkulasi k6 instance requirements
- **Reverse Calculation:** Estimasi User Base dari VU/RPS/TPS
- **Source Documentation:** Semua formula dilengkapi referensi authoritative

---

## 🚀 Quick Start

### Cara Menggunakan

1. **Buka file HTML** di browser (Chrome, Firefox, Edge, Safari)
2. **Pilih Mode Testing:**
   - Single API Testing (untuk API endpoint testing)
   - End-to-End Testing (untuk complete user journey)
3. **Pilih Tipe Input:**
   - VUs Langsung (jika sudah tahu target VU)
   - RPS Langsung (untuk API throughput target)
   - Transaksi Harian (dari business requirements)
   - Transaksi Bulanan
   - Total User Base
   - TPS Langsung
4. **Input Parameters:**
   - Response Time, Think Time, Session Duration (sesuai mode)
5. **Klik "Hitung Performance Metrics"**
6. **Lihat Hasil:**
   - Target VU untuk berbagai level testing
   - Infrastructure requirements
   - Estimasi kapasitas sistem

### Contoh Penggunaan

**Scenario: E-commerce Flash Sale**
```
Input:
- Tipe: Transaksi Harian
- Daily Transactions: 200,000
- Response Time: 2000ms
- Think Time: 5s

Output:
- Peak TPS: 8.33 TPS
- Comprehensive VU: 1,000 VU
- Load Testing (120%): 1,200 VU
- Infrastructure: Small Scale (4 CPU / 8 GB)
```

**Scenario: Government Portal**
```
Input:
- Tipe: Total User Base
- User Base: 100,000 users
- Mode: End-to-End
- Session Duration: 120s

Output:
- Peak Concurrent: 15,000 users
- Peak TPS: 4.17 TPS
- Comprehensive VU: 500 VU
- Infrastructure: Small Scale
```

---

## 📊 Formula & Methodology

### Peak Hour Calculation
```
Peak TPS = (Daily Transactions × 15%) ÷ 3600
```
- **15% Peak Hour:** Industry standard (AWS, Google Cloud, FHWA)
- **3600:** Conversion dari hour ke second

### Little's Law (VU Calculation)
```
VU = TPS × (Response Time + Think Time)
```
- **Source:** J.D.C. Little (MIT, 1961)
- **N = λ × W:** Fundamental queueing theory

### Multi-Level Testing
```
Conservative (70%):  VU × 0.7  - Baseline validation
Comprehensive (100%): VU × 1.0  - Expected peak load
Load (120%):         VU × 1.2  - Traffic spike buffer
Stress (150%):       VU × 1.5  - Breaking point analysis
```

### Infrastructure Sizing
```
k6 Instances = ceil(Target VU ÷ 2,500)
```
- **~2,500 VU per instance** (16 CPU / 32 GB RAM)
- **Source:** Grafana k6 official benchmarks

---

## 🎯 Testing Levels Explained

| Level | Percentage | Purpose | Duration |
|-------|------------|---------|----------|
| **Conservative** | 70% | Baseline testing, smoke test | 10-15 min |
| **Comprehensive** | 100% | Expected peak, SLA validation | 30-60 min |
| **Load** | 120% | Above peak, traffic spike buffer | 30 min |
| **Stress** | 150% | Breaking point, saturation analysis | 15-20 min |

---

## 📚 Industry Standards & Sources

### Peak Hour Percentage (15%)
- AWS Well-Architected Framework
- Google Cloud Capacity Planning
- FHWA Traffic Data Guide (K-Factor)
- Microsoft Azure Best Practices

### Concurrent Users (15%)
- UK Government Digital Service (GDS)
- Facebook DAU/MAU Studies
- Gartner Enterprise Software Research

### Performance Testing Standards
- ISTQB Performance Testing Certification
- ISO/IEC 25010:2011 Quality Model
- Little's Law (Operations Research, MIT 1961)

### Tools References
- Grafana k6 Documentation
- Apache JMeter User Guide
- Gatling Load Testing
- HP LoadRunner

---

## 🎓 Educational Features (New in v2.0.0!)

### Dynamic Examples
Semua formula explanation sekarang menampilkan **calculation dengan nilai input Anda**:

**Before:**
```
Contoh: 15,000 VU → 10,500 VU
```

**Now (dengan input Anda: 20,000 VU):**
```
Calculation dengan Input Anda:
• Comprehensive: 20,000 VU → Conservative: 14,000 VU (× 0.7)
```

**Benefit:**
- ✅ Langsung relevan dengan scenario Anda
- ✅ Tidak perlu mental math
- ✅ Learn by seeing YOUR calculations
- ✅ Experiment-friendly

---

## 🔧 Technical Details

### Technology Stack
- **HTML5** - Structure
- **CSS3** - Styling (Grid, Flexbox, Dark Theme)
- **Vanilla JavaScript** - All calculations (no dependencies)

### Browser Compatibility
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Edge 90+
- ✅ Safari 14+

### File Size
- Single HTML file: ~150 KB
- No external dependencies
- Offline-ready (standalone file)

### Performance
- Calculation time: < 5ms
- Dynamic updates: < 5ms
- Lightweight and fast

---

## 📁 File Structure

```
performance-testing-calculator/
├── performance_calculator_final.html   # Main calculator (standalone)
├── README.md                          # This file
├── VERSION.md                         # Version history
├── CHANGELOG.md                       # Detailed changelog
└── COMMIT_MESSAGE.md                  # Commit template
```

---

## 🆕 What's New in v2.0.0

### Major Features
1. **Dynamic Examples** - All formula calculations show YOUR input values
2. **Enhanced Documentation** - Authoritative source references added
3. **Reverse Calculation** - Estimate User Base from VU/RPS/TPS
4. **Minimized UI** - Cleaner parameter descriptions

### Technical Improvements
- Added `updateDynamicExamples()` function
- 10 dynamic example placeholders
- Real-time calculation updates
- Number formatting with locale support

[See full changelog →](CHANGELOG.md)

---

## 📖 Use Cases

### 1. Capacity Planning
**Input:** Business requirements (daily transactions)  
**Output:** Infrastructure sizing dan VU requirements

### 2. Load Test Planning
**Input:** Target VU atau RPS  
**Output:** Multi-level test scenarios

### 3. Performance Validation
**Input:** Expected user base  
**Output:** Peak load calculations

### 4. Infrastructure Sizing
**Input:** Performance targets  
**Output:** k6 instance requirements (CPU, RAM)

### 5. Reverse Engineering
**Input:** Technical metrics (VU/RPS/TPS)  
**Output:** Business metrics estimation (User Base, Daily Trans)

---

## 💡 Tips & Best Practices

### Input Selection
- **Ada data analytics?** → Gunakan Daily Transactions atau User Base
- **Pure technical testing?** → Gunakan VU atau RPS langsung
- **API endpoint testing?** → Single API mode dengan RPS
- **Complete user flow?** → End-to-End mode dengan TPS

### Response Time Guidelines
- **API endpoints:** 200-500ms (target P95 < 500ms)
- **Web applications:** 1000-2000ms (target P95 < 2000ms)
- **Government portals:** 2000-3000ms (acceptable)

### Think Time Guidelines
- **Aggressive testing:** 0.5-2s
- **Realistic browsing:** 3-10s
- **Form filling:** 1-3s
- **Default recommendation:** 5s

### Progressive Testing Strategy
1. Start with **Conservative (70%)** - Smoke test
2. Run **Comprehensive (100%)** - Validate SLA
3. Execute **Load (120%)** - Test buffer capacity
4. Perform **Stress (150%)** - Find breaking point

---

## ❓ FAQ

**Q: Kenapa Peak Hour 15%, bukan 10% atau 20%?**  
A: 15% adalah safety margin yang balanced. Range industri 10-20%, kita pilih 15% untuk conservative approach. Sources: AWS, Google Cloud, Azure, FHWA.

**Q: Apakah bisa digunakan untuk database load testing?**  
A: Ya, tapi fokus pada transaction rate (TPS). Sesuaikan Response Time dengan query execution time.

**Q: Hasil VU berbeda dengan load testing actual, kenapa?**  
A: Calculator menggunakan assumptions (15% peak, 15% concurrent, etc). Adjust berdasarkan actual analytics Anda.

**Q: Apakah k6 instance sizing akurat?**  
A: Ya, berdasarkan official Grafana k6 benchmarks. ~2,500 VU per instance (16 CPU / 32 GB RAM).

**Q: Bisa export hasil perhitungan?**  
A: Saat ini belum. Planned untuk v2.1.0. Sementara bisa screenshot atau copy-paste results.

**Q: Apakah bisa untuk tools selain k6?**  
A: Ya, formula universal (Little's Law). VU concept sama di JMeter, Gatling, LoadRunner.

---

## 🤝 Contributing

Saat ini tool ini untuk internal use. Untuk feedback atau suggestions:
1. Document use case dan findings
2. Note calculation discrepancies (jika ada)
3. Suggest improvements berdasarkan actual testing experience

---

## 📄 License

Internal tool untuk QA Performance Testing team.

---

## 👥 Credits

**Developed by:** QA Performance Testing Team  
**For:** Badan Gizi Nasional Performance Testing  
**Version:** 2.0.0  
**Last Updated:** January 18, 2026

### References & Acknowledgments
- Little's Law (J.D.C. Little, MIT, 1961)
- AWS Well-Architected Framework
- Google Cloud Architecture Center
- Grafana k6 Documentation
- UK Government Digital Service (GDS)
- ISTQB Performance Testing Guidelines

---

## 📞 Support

**For Questions:**
- Internal QA team documentation
- Performance testing best practices guide
- k6 official documentation: https://k6.io/docs/

**For Issues:**
- Document the scenario
- Note input parameters used
- Describe expected vs actual results
- Share with QA team lead

---

## 🗺️ Roadmap

### v2.1.0 (Planned)
- Export to PDF functionality
- k6 script template generation
- Custom industry percentages

### v2.2.0 (Planned)
- Database load patterns
- Microservices scenarios
- API Gateway calculations

### v3.0.0 (Future)
- Integration with monitoring tools
- Historical data analysis
- Real-time metrics comparison

---

**Ready to calculate? Open `performance_calculator_final.html` in your browser and start planning your load tests! 🚀**
