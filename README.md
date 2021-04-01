# กลุ่มที่ 1 : Tong J w/ Artizy

## สิ่งที่ค้องใช้ทำ
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
   * Initial Assumption: กำหนดหัวข้อ OKR, ดู report ได้, กำหนดเวลาให้สามารถเลือก-เปลี่ยน OKR ได้, กำหนดสิทธิ์และ role ให้ user อื่นๆ
   * Normal: แอดมินกำหนด OKR เข้าสู่ระบบเพื่อให้ user ได้เลือก OKR, ตรวจสอบเอกสารก่อนจะส่งไปที่ผู้บริหาร 
   * What can go wrong: admin อาจจะลืมกำหนดเวลาปิดระบบ
   * System state on completion: -
2. ผู้บริหาร
   * Initial Assumption: ดู report, dashboard อนุมัติเอกสารและการแก้ไข OKR
   * Normal: ผู้บริหารรับเอกสารที่ผ่านการตรวจสอบจาก Admin แล้วทำการอนุมัติผู้บริหารจะมองภาพรวมจาก report, dashboard แต่ไม่สามารถแก้ไขได้ 
   *	What can go wrong: อาจมี delay เกิดขึ้นถ้าผู้บริหารไม่อนุมัติเอกสารสักที
   *	System state on completion: เมื่อผู้บริหารอนุมัติเอกสารจาก user อื่นๆเสร็จแล้วก็จะส่งคืนเข้าระบบต่อไปให้เพื่อแสดงสถานะกับ user อื่นๆ
3. อาจารย์
   *	Initial Assumption: กรอกข้อมูล เลือก OKR สำหรับอาจารย์ พร้อมกับจำนวน, เปลี่ยน OKR, รายงานผล 
   *	Normal: อาจารย์จะมีสิทธิ์เช่นเดียวกับบุคลากรแต่จะเป็น OKR ที่ต่างกัน
   *	What can go wrong:  รายงานผลซ้ำซ้อน เช่นการ การรายงานรายได้ที่ให้ user คำนวณเองหรือระบบเป็นตัวจัดการให้ 
   *	System state on completion: รออนุมัติจากผู้บริหารโดยสามารถเช็คได้ที่หน้าสถานะ
4. หัวหน้าบุคลากร
   *	Initial Assumption: กรอกข้อมูล, เลือก OKR สำหรับบุคลากร, เปลี่ยน OKR สำหรับบุคลากร, รายงานผล, ป้อนข้อมูล OKR ลูกน้องคนอื่นได้ 
   *	Normal: มีสิทธิ์เหมือนบุคลากรแต่จะสามารถแก้ไข, เปลี่ยน, ดูรายการ OKR ของบุคลากร, ลูกน้องได้ 
   *	What can go wrong: อาจจะเกิดข้อผิดพลาดในได้การจัดการกับลูกน้องแต่ละคนเพราะดูแลไม่ทั่วถึง
   *	System state on completion: รออนุมัติจากผู้บริหารโดยสามารถเช็คได้ที่หน้าสถานะ แก้ไขตัวชี้วัดของลูกน้องเสร็จแล้วก็อัพเดตสู่ระบบต่อไป
5. บุคลากร
   *	Initial Assumption: กรอกข้อมูล, เลือก OKR เปลี่ยน OKR, รายงานผล
   *	Normal: บุคลากรกรอกข้อมูล OKR เมื่อกรอก OKR เสร็จแล้วจะถูกเก็บเป็น pdf และส่งเข้าสู่ระบบเพื่อให้ผู้บริหารอนุมัติต่อไป
   *	What can go wrong: user อัพโหลด file type อื่นที่ไม่ใช่ pdf ก็จะ reject ทันที
   *	System state on completion: รออนุมัติจากผู้บริหารโดยสามารถเช็คได้ที่หน้าสถานะ
   *	
### Use case

<img src="https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/raw/master/document/paper_picture_design/usecase/use_case_v2.jpg" style="width:50%">
> เป็นการออกแบบใหม่ครั้งที่2(ver.2) มีทั้งหมด 5 role

### Interface Design
<img src="https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/raw/master/document/paper_picture_design/interface_design/interface_v1.png" style="width:50%">
> ออกแบบหน้า interface ว่าแค่แ่ละ role จะมีหน้าไหนบ้าง 

### ER diagram
<img src="https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/raw/master/document/paper_picture_design/ER_database/ER_diagram_v2.jpg" style="width:50%">
> ออกแบบใหม่ครั้งที่2(ver.2) 

### Relational schema
<img src="https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/raw/master/document/paper_picture_design/ER_database/Relational_Schema_v2.jpg" style="width:50%">
> ออกแบบใหม่ครั้งที่2(ver.2) เป็นการออกแบบ table ของ database ว่ามีอะไรบ้าง

### Link ที่เก็บเอกสารและรูป

[Documnet ที่เก็บเอกสารไว้](https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/tree/master/document)

[Documnet ของ Design ต่างๆ](https://gitlab.en.kku.ac.th/Nakharin/se-project-group1/-/tree/master/document/paper_picture_design)


