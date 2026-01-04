# Sample Expected Results - Rice Yield Prediction System

## ภาพรวม
เอกสารนี้อธิบายตัวอย่างผลลัพธ์ที่คาดหวังจากระบบ เพื่อใช้ในการวางแผนและบริหารความเสี่ยง

---

## 1. คาดการณ์ผลผลิต (รายแปลง)
**ไฟล์:** `01_yield_prediction_by_plot.csv`

### คำอธิบายคอลัมน์
| คอลัมน์ | คำอธิบาย |
|---------|----------|
| Plot_ID | รหัสแปลงนา |
| District | อำเภอ (Chau_Phu, Chau_Thanh, Thoai_Son) |
| Latitude/Longitude | พิกัดแปลง |
| Season | ฤดูกาล (WS=Winter-Spring, SA=Summer-Autumn) |
| Crop_Intensity | ความเข้มข้นการปลูก (Double/Triple) |
| Field_Size_Rai | ขนาดแปลง (ไร่) - แปลงจาก ha × 6.25 |
| Predicted_Yield_kg_per_Rai | ผลผลิตที่คาดการณ์ (กก./ไร่) |
| Total_Predicted_Yield_kg | ผลผลิตรวมทั้งแปลง (กก.) |
| Total_Predicted_Yield_Ton | ผลผลิตรวมทั้งแปลง (ตัน) |
| Confidence_Level | ระดับความเชื่อมั่น (High/Medium/Low) |

### ตัวอย่างการอ่านผล
> แปลง PLOT_001 ขนาด 21.25 ไร่ คาดการณ์ผลผลิตข้าวเปลือก **2.55 ตัน** (1,200 กก./ไร่)

---

## 2. ดัชนีความเสี่ยงภัยพิบัติ
**ไฟล์:** `02_disaster_risk_index.csv`

### คำอธิบายคอลัมน์
| คอลัมน์ | คำอธิบาย |
|---------|----------|
| Flood_Frequency_Score | คะแนนความถี่น้ำท่วม (1-6) |
| Drought_Risk_Score | คะแนนความเสี่ยงแล้ง (1-6) |
| Overall_Risk_Index | ดัชนีความเสี่ยงรวม |
| Risk_Category | ระดับความเสี่ยง (Low/Medium/High) |
| Historical_Flood_Events | จำนวนครั้งที่เกิดน้ำท่วมย้อนหลัง |
| Avg_Waterlog_Duration_Days | ระยะเวลาน้ำขังเฉลี่ย (วัน) |
| Last_Flood_Season | ฤดูกาลที่เกิดน้ำท่วมล่าสุด |
| Recommended_Action | คำแนะนำการดำเนินการ |

### วิธีการวิเคราะห์
- วิเคราะห์ข้อมูลดาวเทียม Sentinel-1 ย้อนหลัง
- ตรวจจับความถี่การเกิดน้ำขังในช่วงที่ไม่ควรท่วม
- ระบุพื้นที่เสี่ยงซ้ำซากเพื่อวางแผนรับมือล่วงหน้า

---

## 3. ข้อมูลเชิงเวลา (Temporal Vegetation Indices)
**ไฟล์:** `03_temporal_vegetation_indices.csv`

### คำอธิบายคอลัมน์
| คอลัมน์ | คำอธิบาย |
|---------|----------|
| Acquisition_Date | วันที่ถ่ายภาพดาวเทียม |
| Growth_Stage | ระยะการเจริญเติบโต |
| NDVI | ดัชนีพืชพรรณ (0-1) |
| NDWI | ดัชนีความชื้น |
| RVI | Radar Vegetation Index |
| VH_Mean/VV_Mean | ค่าเฉลี่ย Sentinel-1 |
| Vegetation_Health | สุขภาพพืช (Poor/Moderate/Good/Excellent) |
| Moisture_Status | สถานะความชื้น |
| Yield_Correlation_Check | การตรวจสอบความสอดคล้องกับผลผลิต |

### การใช้งาน
- ติดตามพัฒนาการของพืชผ่าน 2-3 ช่วงเวลา
- ตรวจสอบความสมเหตุสมผลของผลผลิตที่คาดการณ์
- ระบุแปลงที่มีปัญหา (Flag) เพื่อตรวจสอบเพิ่มเติม

---

## หมายเหตุ
- ข้อมูลนี้เป็นตัวอย่างเพื่อแสดงรูปแบบผลลัพธ์ที่คาดหวัง
- ค่าจริงจะคำนวณจากโมเดล ML และข้อมูลดาวเทียมปัจจุบัน
- หน่วย: 1 เฮกตาร์ = 6.25 ไร่
