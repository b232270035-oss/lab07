# BUG-08: Malformed JSON-д HTTP 200 OK буцаана

Төрөл: API / алдаа боловсруулах
Орчин: Уншлагын жагсаалт v2.0, Debian GNU/Linux 13.7, Node.js v20.20.2; session-ийн browser: Codex in-app browser (engine version харагдаагүй), 2026-11-26.
Урьдчилсан нөхцөл: `node app.js`-ийг шинээр асааж, анхны 3 номтой төлөвөөс эхэлнэ.
## Дахин гаргах алхам
1. Серверийг асаана.
2. Терминалд дараах хүсэлтийг ажиллуулна: `curl -i -X POST http://localhost:3000/api/books -H 'Content-Type: application/json' --data-binary '{ invalid json'`

Хүлээгдэж байсан: Spec-ийн дагуу malformed JSON body-д HTTP 400 буцаах.
Бодит үр дүн: HTTP 200 OK, `{"result":"OK"}` буцаж байна.
Ноцтой байдал: Major — үйлчлүүлэгчийн буруу payload амжилттай болсон мэт харагдана.
Олдсон аялал: Saboteur (API).

## `curl -i` нотолгоо
`../evidence/bug-08-curl.txt`
