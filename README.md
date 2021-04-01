# กลุ่มที่ 1 : Tong J w/ Artizy

## สิ่งที่ต้องใช้ทำ
* server: ubuntu 18
* database: sqlite3
* PHP 7.2
* Webapp: server nginx  

## dummy id สำหรับเข้า wedsite ตาม role

* admin 
   * ID: adummy.coe01@gmail.com
   * Password: CoeWeb001
* user ทั่วไป (อาจาร์ บุคลสกร)
   * ID: dummy.coe01@gmail.com
   * Password: CoeWeb001

## Requiment Specification

### Scenarios
1. Admin 
   * Initial Assumption: กำหนดหัวข้อ OKR, ดู report ที่ละเอียดได้, กำหนดเวลาให้สามารถเลือก-เปลี่ยน OKR ได้, กำหนดสิทธิ์และ role ให้ user อื่นๆ, เปิดปิดระบบต่างๆตามตารางวัน, ลง เปลี่ยน และ รายงานผล OKR ได้
   * Normal: แอดมินสามารถใส่ OKR ของแต่ละปะเข้าสู่ระบบเพื่อให้ user ได้เลือก OKR ตรวจสอบเอกสารก่อนจะส่งไปให้กับผู้บริหาร โดยเข้ามาตรวจ อนุมัติการของ OKR ของ user คนอื่น ต้องทำการเปิด/ปิดระบบเป็นช่วงเวลา เช่น ช่วงที่ให้เลือก OKR ก็จะเปิดระะบบเลือก OKR ถ้าเลยช่วงเวลาดังกล่าวต้องไปปิดระบบเลือก OKR ด้วยตัวเอง โดย admin เองต้องเลือก OKR เองได้ด้วย และต้องกำหนด role ให้ user คนอื่นๆ และสามารถดูกราฟ report แบบระเอียดว่า OKR หัวข้อนี้มีใครที่เลือกบ้าง แล้วแต่ละคนทำได้เท่าไหร่แล้ว สัญญาไว้เท่าไหร่ และ ผ่านหรือไม่ผ่าน
   * What can go wrong: admin อาจจะลืมกำหนดเวลาปิดระบบ, กำหนด role ให้ user อิ่นผิด
   * System state on completion: admin จะกำหนดงานวนไปทุกๆปี ดังนั้นไม่มี state ที่หยุดได้
2. ผู้บริหาร
   * Initial Assumption: ดู report ที่ละเอียดได้,อนุมัติ OKR ที่ได้ต่อมาจาก admin อีกที, ลง เปลี่ยน และ รายงานผล OKR ได้
   * Normal: ผู้บริหารรับเอกสารที่ผ่านการตรวจสอบจาก Admin แล้วทำการอนุมัติ โดยที่ผู้บริหารจะสามารถมองภาพรวมของ report ได้เป็นแบบ กราฟแบบระเอียดว่า OKR หัวข้อนี้มีใครที่เลือกบ้าง แล้วแต่ละคนทำได้เท่าไหร่แล้ว สัญญาไว้เท่าไหร่ 
   *	What can go wrong: อาจมีความล่าช้าเกิดขึ้นถ้าผู้บริหารไม่อนุมัติเอกสารสักที
   *	System state on completion: เมื่อผู้บริหารอนุมัติเอกสารจาก user อื่นๆเสร็จแล้วก็จะส่งคืนเข้าระบบต่อไปให้เพื่อแสดงสถานะกับ user อื่นๆ
3. อาจารย์
   *	Initial Assumption: กรอกข้อมูล เลือก OKR สำหรับอาจารย์ พร้อมกับจำนวน, เปลี่ยน และรายงานผล OKR ได้, ดูกราฟ report ได้แบบคร่าวๆ
   *	Normal: อาจารย์กรอกข้อมูล OKR เมื่อกรอก OKR เสร็จแล้วจะถูกเก็บเป็น pdf และส่งเข้าสู่ระบบเพื่อให้ admin และ ผู้บริหารอนุมัติต่อไป หลังจากได้รับการอนุมัติเสร็จตะสามารถรายงานความคืบหน้าของ OKR ที่ทำได้ลงเว็บ โดยเมื่อหมดระยะเวลารายงานผล OKR ก็จะได้สรุปผลว่าได้คะแนนกี่คะแนน ผ่านหรือไม่ผ่าน โดยจะสามารถดู report เป็นกราฟ OKR ว่าหัวข้อนั้นมีคนเลือกกี่คน ผ่านหรือไม่ผ่านกี่คน
   *	What can go wrong:  รายงานผลซ้ำซ้อนหรือรายงานผลผิดอาจจะเป็นปัญหาหรือ การรายงานผลที่เข้าใจไม่ตรงกันกับระบบ เช่น user รายงานผลโดยการคำนวณเองเช่นเคยทำไปแล้ว2ทำเพิ่มได้3เลยไปกรอกผลเป็น5 แต่ระบบเป็นการคำนวณให้เองคือใส่แค่สิ่งที่ทำเพิ่ม ทำให้ผลการรายงานผิดพลาด
   *	System state on completion: รออนุมัติจากผู้บริหารโดยสามารถเช็คได้ที่หน้าสถานะ
4. หัวหน้าบุคลากร
   *	Initial Assumption: กรอกข้อมูล, เลือก OKR สำหรับบุคลากร, เปลี่ยน และ รายงานผล OKR ได้, เลือก และ ป้อนข้อมูล OKR ของคนอื่น(ลูกน้อง)ได้, ดูกราฟ report ได้แบบคร่าวๆ
   *	Normal: มีสิทธิ์เช่นเดียวกับอาจารย์แต่จะมี OKR ที่ต่างกัน และสามารถแก้ไข, เปลี่ยน, ดูรายการ OKR ของคนอื่น(ลูกน้อง)ได้ หรือก็คือภายใน 1 ID จะมีลูกน้องให้กดเลือกได้หลายคนคือ ตอนหัวหน้า login เข้าสู่ระบบจะมีให้เลืกก่อนว่าจะไปจัดการกับคนไหน โดยจะมีให้เลือกคือ หัวหน้า และ ลูกน้องที่ตนคุม โดยพอกดเลือกคนไหนก็จะได้หน้าจอแบบบุคลากรปกติเลย
   *	What can go wrong: อาจจะเกิดข้อผิดพลาดในได้การจัดการกับลูกน้องแต่ละคนเพราะดูแลอยู่หลายคนทำให้สับสน และบางทีอาจจะมีลูกน้องมาใหม่ หรือมีลูกน้องเพิ่มเข้ามาแล้วไม่มีให้เลือก
   *	System state on completion: รออนุมัติจากผู้บริหารโดยสามารถเช็คได้ที่หน้าสถานะ แก้ไขตัวชี้วัดของลูกน้องเสร็จแล้วก็อัพเดตสู่ระบบต่อไป
5. บุคลากร
   *	Initial Assumption: กรอกข้อมูล, เลือก OKR เปลี่ยน OKR, รายงานผล, ดูกราฟ report ได้แบบคร่าวๆ
   *	Normal: มีสิทธิ์เช่นเดียวกับอาจารย์แต่จะมี OKR ที่ต่างกัน
   *	What can go wrong: รายงานผลซ้ำซ้อนหรือรายงานผลผิด เช่นการ การรายงานรายได้ที่ให้ user คำนวณเองหรือระบบเป็นตัวจัดการให้ 
   *	System state on completion: รออนุมัติจากผู้บริหารโดยสามารถเช็คได้ที่หน้าสถานะ
   *	
### Use case

<img src="https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/raw/master/document/paper_picture_design/usecase/use_case_v2.jpg" width="500">

> เป็นการออกแบบใหม่ครั้งที่2(ver.2) มีทั้งหมด 5 role

### Interface Design

<img src="https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/raw/master/document/paper_picture_design/interface_design/interface_v1.png" width="500">

> ออกแบบหน้า interface ว่าแค่แ่ละ role จะมีหน้าไหนบ้าง 

### ER diagram
<img src="https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/raw/master/document/paper_picture_design/ER_database/ER_diagram_v2.jpg" width="500">

> ออกแบบใหม่ครั้งที่2(ver.2) 

### Relational schema
<img src="https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/raw/master/document/paper_picture_design/ER_database/Relational_Schema_v2.jpg" width="450">

> ออกแบบใหม่ครั้งที่2(ver.2) เป็นการออกแบบ table ของ database ว่ามีอะไรบ้าง

### Link ที่เก็บเอกสารและรูป

[Link ของ Documnet ที่เก็บเอกสารไว้](https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/tree/master/document)

[Link ของ Documnet รูปภาพของ Design ต่างๆ](https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/tree/master/document/paper_picture_design)

