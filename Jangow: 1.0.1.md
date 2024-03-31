# Machine-2
**1.** Target-ын мэдэээл авах netdiscover командыг хийснээр бидний зорилтот IP гэж юу болохыг харах боломжтой
![image](https://github.com/Bultuush/Machine-2/assets/129934501/c91537ea-317d-484d-9c30-94e2b75b857d)

Target-ын IP хаяг **192.168.56.118**
![image](https://github.com/Bultuush/Machine-2/assets/129934501/2b2bfd83-cc86-4cc8-9e23-6a512ff02fe2)

Үндсэн хайгуул дууссан. Одоо бид **FTP(21)** ба **HTTP(80)** гэсэн 2 нээлттэй порттой боллоо.
Би анхдагч нэргүй итгэмжлэлүүдийг **(anonymous:anonymous)**. ашиглан FTP руу нэвтрэхийг оролдсон.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/cf5a4ff9-7465-4285-927a-595038d74479)

Харамсалтай нь вэб сервер нь FTP-г өгөгдмөл итгэмжлэлээр тохируулаагүй байна. Одоо бид HTTP порттой үлдсэн тул түүнийг ашиглая.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/cc2fcdb0-ee88-48a8-8da8-404d96dfa9a4)

Бид энэ вэб сайтаас **dirb** болон **common.txt wordlist** ашиглан лавлах хайлт хийх болно.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/2fb6569f-c322-45bf-ac4a-82b54d293237)

10.0.2.5/site/wordpress/index.html нь биднийг сайтын HTML рүү хөтөлж байна.

![image](https://github.com/Bultuush/Machine-2/assets/129934501/119c3b22-e863-4a5b-9ee7-5964079f29f3)

Холбоосууд дээр дарж хаашаа чиглүүлж байгааг шалгах нь бидэнд сонирхолтой олдвор авчирдаг. Та Buscar дээр дарахад ERROR 404 гэсэн хуудас гарч ирэх бөгөөд "Not Found" гэж бичнэ.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/95f46df4-2a97-4da8-b650-bdba12ddbaa3)

# Command-Line Injection
Гэхдээ энэ бол сонирхолтой олдвор биш юм. Хэрэв та URL-г харвал энэ нь = тэмдгээр төгсдөг. Энэ нь командын мөрийн тарилгын эмзэг байдлын шинж тэмдэг юм.

Хэрэв та бүх сангуудыг жагсаахын тулд **ls -all** гэж бичвэл энэ нь ямар ч алдаа гаргахгүй байхыг харах болно. Үүний оронд энэ нь үр дүнг өгдөг. Илүү цэгцтэй үр дүнг хуудасны эх сурвалжаас харна уу.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/6fd5ef5c-ee41-4f56-8aa3-33748b2dcf33)

**cd** гэж бичээд нэг лавлахыг буцаана.. командуудыг -аар тусгаарлана; **ls -all** ашиглан бүх сангуудыг жагсаана уу. Та лавлах дунд жагсаасан .backup файлыг харна уу. cat командыг ашиглан **.backup** файлыг нээнэ үү.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/b25bedb5-4dee-40bb-9819-fd8eac311af3)

**Энэ бол миний ашигласан эцсийн URL юм:**
**view-source:http://192.168.56.118/site/busque.php?buscar=ls -all;cd ..;ls -all;cat .backup.**

Бидний .backup файлаас авсан итгэмжлэлүүд нь:
![image](https://github.com/Bultuush/Machine-2/assets/129934501/47b3d80f-c31e-4039-b64b-eb9c3bb55259)

Энэ машин дээр нээлттэй **MySQL** порт байхгүй. Итгэмжлэл **FTP** порт дээр ажиллаж байгаа эсэхийг ашиглая.
# FTP Port: Inputing the .Backup Credentials
![image](https://github.com/Bultuush/Machine-2/assets/129934501/bdc8ca47-e3d4-4f1e-b847-734d3b8b0c29)

Энэ болчихлоо!
Одоо лавлахыг home directory болгож, агуулгыг нь харцгаая.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/21b2f5d6-78cf-4820-9fe1-0044f0037a50)

CD jangow01 гэж бичээд directory-ыг jangow01 болгож өөрчилнө үү
![image](https://github.com/Bultuush/Machine-2/assets/129934501/426f9d43-57c2-4420-993a-89aebb539cb3)

user.txt файл байна. Үүнийг get командыг ашиглан татаж авцгаая.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/22936204-b03e-4a6a-9593-786b1c317d2e)

Миний home машин дээр user.txt файлыг нээхэд дараах зүйл гарч ирнэ: d41d8cd98f00b204e9800998ecf8427e
![image](https://github.com/Bultuush/Machine-2/assets/129934501/6a42b3d3-2d59-420e-85f6-951be1b801bb)

Бид хэрэглэгчийн flag оллоо. Би үүнийг decoding хийх оролдсон боловч энэ нь ямар ч үнэ цэнэтэй үр дүнд хүргэсэнгүй.
# Линукс хувилбарыг олж авах
Jangow хайрцаг руу ороод хэрэглэгчийн нэр:jangow01, нууц үг:abygurl69-оор нэвтэрнэ үү.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/3473864e-2959-4dce-ac35-8faf5a3ea288)

Uname-a командыг ашиглан Jangow хайрцагны ашиглаж буй үйлдлийн системийн хувилбарыг авна уу.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/b3a4451b-cbdb-4f75-b0d3-730b5caf9a20)

# Давуу эрх нэмэгдүүлэх
Jangow01-ээс root руу шилжихийн тулд давуу эрх нэмэгдүүлэх аргыг ашиглана уу.
Би Google-ээс Linux 4.4.0-31-ерөнхий хувилбарын ашиглалт байгаа эсэхийг шалгаад CVE:2017-16995-ыг олсон.

Энд ашиглах холбоос байна **https://www.exploit-db.com/exploits/45010**
Exploit кодыг .c файл руу хуулж буулгана уу. Би өөрийгөө jangow.c гэж хадгалсан
Энэ командыг ашиглан FTP үйлчилгээ рүү дахин нэвтэрнэ үү. ftp Your.IP.Address
CD /home/jangow01 ашиглан лавлах санг Jangow01 лавлах болгон өөрчил
Энэ командыг ашиглан өөрийн гэрийн машинаас exploit файлыг FTP руу байршуулна уу: jangow.c-г тавь
![image](https://github.com/Bultuush/Machine-2/assets/129934501/ae34a4af-27f9-495d-936e-17f3fcaf06b3)

Jangow машин руу очиж файлыг амжилттай байршуулсан эсэхийг шалгана уу.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/3b3fb851-2b75-4ce6-8244-7ce0467426e6)

Таны харж байгаагаар үүнийг байршуулсан байна.
Одоо **gcc** командыг ашиглан .c файлыг эмхэтгэж угсарцгаая: **gcc jangow.c -o jangow**
Одоо үүнийг гүйцэтгэх боломжтой болгохын тулд: **chmod +x jangow**
Дараа нь скриптийг ажиллуулна уу: ./jangow
Энэ нь бүрхүүлийг эхлүүлдэг.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/af2b30ba-a27a-4457-8d61-672956c5f748)

Одоогийн хэрэглэгчийн нэрийг харуулахын тулд `**whoami** командыг ашиглана уу.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/9f36c329-961a-4369-bd36-ad0ae9eda5a0)

Root дахь файлуудыг үзэхийн тулд **ls /root** командыг бичнэ үү
![image](https://github.com/Bultuush/Machine-2/assets/129934501/baf5c93b-3dbe-48d3-821b-1c581611aeea)

**cat proof.txt** файлыг ашиглан **flag**-ийг авна уу.
![image](https://github.com/Bultuush/Machine-2/assets/129934501/d8f823a3-3d23-4369-8a8c-0cd14ed38a28)

Та Jangow хайрцгийг амжилттай үндэслэв!
