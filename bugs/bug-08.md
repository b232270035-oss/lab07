# BUG-08: POST /api/books буруу JSON-оор дуудахад 400 биш 200 OK буцаадаг

Орчин:  Уншлагын жагсаалт v2.0, curl.exe, Microsoft Windows 11 Pro, 2026-10-25
Урьдчилсан нөхцөл: node app.js-ийг шинээр асаасан (анхны 3 ном)

## Дахин гаргах алхам
1. Ажиллаж байгаа node app.js-ийг Ctrl+C-ээр зогсоогоод дахин `node app.js` гэж асаа.
2. Шинэ PowerShell цонх нээгээд, зориуд эвдэрсэн JSON-тэй файл үүсгэ:
   `Set-Content -Path body.json -Value 'buruu json {' -Encoding ascii`
3. Хүсэлт илгээ:
   `curl.exe -s -i -X POST http://localhost:3000/api/books -H "Content-Type: application/json" --data-binary "@body.json"`
4. Хариуны хамгийн эхний мөр (статус) болон биеийг хар.
5. Ном нэмэгдсэн эсэхийг шалгахдаа: `curl.exe -s http://localhost:3000/api/books`

Хүлээгдэж байсан: Спецификацид «буруу JSON биетэй POST хүсэлтэд 400 алдаа буцаана» гэсэн. Тэгэхээр `HTTP/1.1 400 Bad Request` гарах ёстой.
Бодит үр дүн:     `HTTP/1.1 200 OK`, бие нь `{"result":"OK"}`. Жагсаалтыг дахин татахад 3 ном хэвээр, юу ч нэмэгдээгүй.

Ноцтой байдал: Major. Ном нэмэгдээгүй мөртөө сервер "OK" гэж хэлж байгаа тул API ашиглагч хүсэлт амжилттай болсон гэж андуурна.
Хавсралт:      evidence/bug-08-curl.txt
Олдсон аялал:  Saboteur (API түвшний довтолгоо)
