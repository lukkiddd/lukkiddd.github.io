---
title : Interleavd Experiments - Trustworthy online controlled experiments
notetype : feed
date : 2022-07-23
---


## Notes
- Interleaved experiment มักใช้ในการวัด ranking algorithm (e.g., search engines)
- ใน interleaved experiment เราจะมี ranking algorithm 2 ตัว A และ  B
	- Algorithm A โชว์ผล A1, A2, A3, A4
	- Algorithm B โชว์ผล B1, B2, B3, B4
	- เราจะเอา Algorithm A/B มา mixed กัน แล้วลบผลลัพธ์ที่ซ้ำกันทิ้ง
		- A1, B1, A2, B2, A3, B3, A4, B4
	- วิธีนึงที่ใช้วัดผลคือดู click-through rate จากผลลัพธ์ของสอง Algorithms
- Limitation
	- เนื่องจากผลลัพธ์เป็นผลลัพธ์รวมกัน (homogeneous)
	- ถ้าผลลัพธ์แรกใช้พื้นที่เยอะกว่า หรือ ส่งผลกระทบกับส่วนอื่นในหน้า UI นั้นๆ ความซับซ้อนในการสรุปผลก็จะยากขึ้น


## Reference
- [Trustworthy Online Controlled Experiments](https://www.amazon.com/Trustworthy-Online-Controlled-Experiments-Practical/dp/1108724264)

#ab-testing #interleaved-experiment