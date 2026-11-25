# BUG-13: JSON `null` POST server процессыг унагаана

Төрөл: API / тогтвортой ажиллагаа
Орчин: Уншлагын жагсаалт v2.0, Debian GNU/Linux 13.7, Node.js v20.20.2; session-ийн browser: Codex in-app browser (engine version харагдаагүй), 2026-11-26.
Урьдчилсан нөхцөл: `node app.js`-ийг шинээр асааж, анхны 3 номтой төлөвөөс эхэлнэ.
## Дахин гаргах алхам
1. `node app.js` ажиллуулна.
2. `curl -i -X POST http://localhost:3000/api/books -H 'Content-Type: application/json' --data-binary 'null'` ажиллуулна.
3. Дараа нь `curl -i http://localhost:3000/api/books` гэж GET явуулна.

Хүлээгдэж байсан: Объект хэлбэргүй JSON payload-д client error (400) буцааж, server ажилласаар байх.
Бодит үр дүн: POST `Empty reply from server` гэж дуусч, дараагийн GET connection refused болно. Шинээр асаахад анхны гурван ном буцна. Хоёр удаа давтагдсан.
Ноцтой байдал: Major — нэг хүсэлт server-ийг бүрэн зогсоож бүх хэрэглэгчийн request-ийг тасална.
Олдсон аялал: Saboteur (API payload type).

## `curl -i` нотолгоо
`../evidence/null-json.txt` (хоёр run; HTTP status header ирээгүй, server connection тасалсан).
