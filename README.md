# IOT-Protocols---TCP-UDP---Https-https-






- مقدمة في بروتوكول MQTT 
- تطبيق ثلاث مشاريع مختصة في IOT 

 

 مقدمة 

    

 ويعرف بروتكول MQTT بأنه : Message Queue telemetry trasport وانه يستخدم TCP وأيضا يدعم M2M وأيضا Interact with Machines. 
 وتم تطويره من قبل شركة IBM . 
 يدعم الحماية على ثلاث مستويات : 
في البداية على مستوى الارسال وايضا على مستوى مصداقية الشهادة وايضا على مستوى Authontication. 

![](https://paper-attachments.dropbox.com/s_51D4B74E1E15B4A8DD2A824E39329518431ACBC50C4720496AE72BA41299FC5E_1641498955510_WhatsApp+Image+2022-01-06+at+22.49.18.jpeg)


معايير مشروع الانتهاء من المعسكر : 


-    قابل التطبيق.
-  إطار  : مواصلات - مباني - بيئة. 
- أستخدام بروتوكول MQTT.


بناء مشروع يطبق علية على الاقل : 

 ثلاث حساسات  و يستعمل HomeGetway: wireless - authn. 
وأيضا : يستخدم Protocol MQTT. 


التطبيق -  LAB 
المشروع الاول : مشروع حساس المويا

1- MCU 
2- Sensor 
3- Sprinkler


![](https://paper-attachments.dropbox.com/s_51D4B74E1E15B4A8DD2A824E39329518431ACBC50C4720496AE72BA41299FC5E_1641309258941_Screen+Shot+1443-06-01+at+10.01.45+AM.png)


التطبيق البرمجي 


    from gpio import *
    from time import *
    
    def main():
            pinMode(0, OUT)
            pinMode(A0, IN)
            waterLevel = (((analogRead(A0)-0)*(21.81- -0)) / (1023-0))+ 0
            while True:
                    waterLevel = (((analogRead(A0)-0)*(21.81- -0)) / (1023-0))+ 0
                    print waterLevel
                    if waterLevel < 2:
                            customWrite(0, '1');
                    elif waterLevel > 15:
                            customWrite(0, '0');
                    sleep(0.5)

نحول كمية الفولت إلى لتر  : analogRead(A0)-0)*(21.81- -0)) / (1023-0))+ 0. 
وبعدها نضيف الشرط 

                    print waterLevel
                    if waterLevel < 2:
                            customWrite(0, '1');
                    elif waterLevel > 15:
                            customWrite(0, '0');
                    sleep(0.5)


مشروع أشارة المرور 


![](https://paper-attachments.dropbox.com/s_51D4B74E1E15B4A8DD2A824E39329518431ACBC50C4720496AE72BA41299FC5E_1641309904472_Screen+Shot+1443-06-01+at+3.04.10+PM.png)


في حال ان الاشارة كانت خضراء توقف جميع الطرق بأشراة حمرا

![](https://paper-attachments.dropbox.com/s_51D4B74E1E15B4A8DD2A824E39329518431ACBC50C4720496AE72BA41299FC5E_1641310215081_Screen+Shot+1443-06-01+at+6.29.02+PM.png)

- في حال أن الاشارة خضراء توقف جميع الطرق باشارة حمراء . 

التطبيق البرمجي 


    from gpio import *
    from time import *
    
    def main():
    
            while True:
                    digitalWrite(0, HIGH);
                    digitalWrite(2, HIGH);
                    digitalWrite(4, HIGH);
                    digitalWrite(6, HIGH);
                    delay(1000)
                    digitalWrite(0,LOW);
                    digitalWrite(1,HIGH);
                    delay(3000)
                    digitalWrite(1,LOW);
                    digitalWrite(2,LOW);
                    digitalWrite(3,HIGH);
                    digitalWrite(0,HIGH);
                    delay(3000)
                    digitalWrite(3,LOW);
                    digitalWrite(4,LOW);
                    digitalWrite(5,HIGH);
                    digitalWrite(2,HIGH);
                    delay(3000)
                    digitalWrite(3,LOW);
                    digitalWrite(4,LOW);
                    digitalWrite(5,HIGH);
                    digitalWrite(2,HIGH);
                    delay(3000)
                    digitalWrite(5,LOW);
                    digitalWrite(6,LOW);
                    digitalWrite(7,HIGH);
                    digitalWrite(4,HIGH);
                    delay(1000)
                    digitalWrite(7,LOW);
    
    if __name__ == "__main__":
            main()
    


المشروع الرابع | Student LAB 

أتمت الاجهزة عن طريق ربطها HomeGetway. 


![](https://paper-attachments.dropbox.com/s_51D4B74E1E15B4A8DD2A824E39329518431ACBC50C4720496AE72BA41299FC5E_1641310913479_Screen+Shot+1443-06-01+at+6.41.14+PM.png)





المشروع  

هو عبارة عن alarm system : حساس في حال الاستشعار 
يصدر تبيه .
1- حساس 
٢- منبة صوت 
٣- منبة ضوئي 
٤- SBC 


![](https://paper-attachments.dropbox.com/s_51D4B74E1E15B4A8DD2A824E39329518431ACBC50C4720496AE72BA41299FC5E_1641216651337_Screen+Shot+1443-05-30+at+4.30.01+PM.png)


التشغيل البرمجي 


    from gpio import *
    from time import *
    
    def main():
            
            while True:
                    value = digitalRead(0)
                    if value == 0:
                            print(value)
                            digitalWrite(1,LOW)
                            digitalWrite(2,LOW)
                    else:
                            print(value)
                            digitalWrite(1,HIGH)
                            digitalWrite(2,HIGH)
                    delay(10)
    if __name__ == "__main__":
            main()
    



![](https://paper-attachments.dropbox.com/s_51D4B74E1E15B4A8DD2A824E39329518431ACBC50C4720496AE72BA41299FC5E_1641216844067_Screen+Shot+1443-05-30+at+4.33.14+PM.png)


التشغيل البرمجي 


    from gpio import *
    from time import *
    
    def main():
            while True:
                    Value = digitalRead(1)
                    if Value == 0:
                            customWrite(0,'0')
                    else:
                            customWrite(0,'1')
                    delay(10)
    if __name__ == "__main__":
            main()
    


في أنه analog 



![](https://paper-attachments.dropbox.com/s_51D4B74E1E15B4A8DD2A824E39329518431ACBC50C4720496AE72BA41299FC5E_1641216933227_Screen+Shot+1443-05-30+at+4.34.58+PM.png)


لو لاحظنا ان القيمية متغيرة غير ثابته في نزايد وهذا يفسر كونها analog. 
