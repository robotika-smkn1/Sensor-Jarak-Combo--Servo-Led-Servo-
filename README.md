


# :pushpin: Sensor-Jarak-Combo-(Servo,Led,Servo)



<p align="center">
  <img src="https://i.postimg.cc/tRZw0xQ4/logo-removebg-preview.png" alt="robotika smkn1 kotabekasi logo"/ style="height:350px;" "width: 350px;">
</p>


[![Version](https://img.shields.io/badge/VENOM-1.0.17-brightgreen.svg?maxAge=259200)]()
[![Stage](https://img.shields.io/badge/Release-Stable-brightgreen.svg)]()
![licence](https://img.shields.io/badge/license-GPLv3-brightgreen.svg)
[![Coverity Scan Build Status](https://scan.coverity.com/projects/aircrack-ng/badge.svg)](##Link##)



## :inbox_tray: Media Social Instagram

To keep this collection up-to-date need contributors who can add more Program Arduino scripts
||
|--------------|
|:mailbox_with_mail: [artha_sa_](https://www.instagram.com/artha_sa_/)
|:mailbox_with_mail: [dicky_asqaelani26](https://www.instagram.com/dicky_asqaelani26/)
|:mailbox_with_mail: [rahmatnurraya](https://www.instagram.com/rahmatnurraya990/)
|:mailbox_with_mail: [applepi_fthur](https://www.instagram.com/applepi_fthur/)
|:mailbox_with_mail: [robotika-smkn1](https://www.instagram.com/robotika.smkn1kotabekasi/)


# :moneybag: [Donate](https://saweria.co/arthasyarif)


# :briefcase: Barang & Bahan
- Arduino Uno
- Kabel Male & Female
- Servo Sg/Mg
- Sensor Ultra Sonic ( Hc-sr04 )
- Led Green & Red
- Buzzer
- Resistor 220 Ohm


# :mag: Ilustrasi Arduino

<p align="center">
  <img src="https://i.postimg.cc/QtBtGPds/Watermak.png" style="height:205px;" "width:205px;"/>
</p>


# :clipboard: Source Code By Robotika SMKN 1

```bash
/*
 * 
 * All the resources for this project: smkn1kotabekasi.sch.id
 * Modified by Robotika smkn1 kotabekasi
 * 
 * Created by Robotika smkn1 kotabekasi
 * 
 */
 
 

// menambahkan lubrary Servo
#include <Servo.h>

// inialisasi variabel untuk servo
Servo servo1;

// inialisasi pin ultrasonic
const int pinTRIGGER = 8;
const int pinECHO = 9;
const int buzzer = 11;
const int ledPinHijau = 13;
const int ledPinRed = 12;

// inialisasi variabel pembacaan sensor ultrasonic
// gunakan "float" untuk angka dengan koma
// atau gunakan "int" untuk angka tanpa koma
float durasi, jarak;


// ======================= program pengaturan awal ====================== //
void setup()
{

// inialisasi pin servo
servo1.attach(10);

// menulis derajat awal servo (menutup)
servo1.write(0);

// inialisasi stauts I/O pin
pinMode(pinTRIGGER, OUTPUT);
pinMode(pinECHO, INPUT);
pinMode(buzzer, OUTPUT);
pinMode(ledPinHijau, OUTPUT);
pinMode(ledPinRed, OUTPUT);
Serial.begin(9600); // Starts the serial communication

delay(1000);
}


// ============================== program utama ============================= //
void loop()
{

  
//pembacaan sesnor ulrasonic
//Mengaktifak pin Trigger selama 10mikrodetik
//Lalu dia non aktif
digitalWrite(pinTRIGGER, HIGH);
delayMicroseconds(10);
digitalWrite(pinTRIGGER, LOW);

//Mengaktifkan pin Echo yang menerima pantulan gelombang ultrasonik
//pulseIn = Lama durasi pin Echo menerima pantulan gelombang
//Menghitung rumus jarak(Lama durasi dibagi dua)
durasi = pulseIn(pinECHO, HIGH);
jarak = ((durasi * 0.034) / 2);

// menulis data pembacaan ultrasonic pada serial monitor
// jadi kita tahu jarak obejak yang terbaca
Serial.print("Jarak: ");
Serial.println(jarak);


// program buka tutup servo otomatis
// jika jarak objek terbaca <= 7 cm
// ubah dan sesuaikan jarak objek saat buka di sini, satuan cm
if (jarak <= 20)
{
// servo membuka, mnuju derajat 90
// ubah dan asesuaikan derajat buka di sini
servo1.write(180);

// Buzzer Nyala
digitalWrite(buzzer, HIGH);

// Led Menyala
digitalWrite(ledPinHijau, HIGH);

digitalWrite(ledPinRed, LOW);


// delay membuka servo
// di sini disetting 3 detik membukanya
// ubah durasi buka di sini
delay(700);

// servo menutup kembali, menuju derajat 0
// ubah dan sesuaikan derajat tutup di sini
servo1.write(0);
}

// jika jarak objek terbaca lebih dari pernyataan di atas
else
{
// servo menutup, menuju derajat 0
// ubah dan sesuaikan derajat tutup di sini
servo1.write(0);

//Buzzer Mati
digitalWrite(buzzer, LOW);

//Led Mati
digitalWrite(ledPinHijau, LOW);

digitalWrite(ledPinRed, HIGH);

}


// delay program
delay(200);

}


```
