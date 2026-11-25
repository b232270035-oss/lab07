# BUG-09: Жилийн хүрээ болон бүхэл тооны validation алга

Төрөл: API / validation
Орчин: Уншлагын жагсаалт v2.0, Debian GNU/Linux 13.7, Node.js v20.20.2; session-ийн browser: Codex in-app browser (engine version харагдаагүй), 2026-11-26.
Урьдчилсан нөхцөл: `node app.js`-ийг шинээр асааж, анхны 3 номтой төлөвөөс эхэлнэ.
## Дахин гаргах алхам
1. Серверийг асаана.
2. `curl -i -X POST http://localhost:3000/api/books -H 'Content-Type: application/json' --data-binary '{"title":"Boundary violation","author":"QA","year":2101}'` хүсэлт явуулна.
3. Нэмэлтээр `year`-ийг `999`, `2000.5`, `"abc"` эсвэл орхисон payload явуулж болно.

Хүлээгдэж байсан: Spec-ийн дагуу жил 1000–2100 хоорондох бүхэл тоо байх; бусад утгыг validation error-оор татгалзах.
Бодит үр дүн: Буруу утгууд HTTP 201 Created авч хадгалагдана; 2101 нь UI-д `2,101`, жилгүй утга `0`, текстэн утга `NaN` гэж харагдана.
Ноцтой байдал: Major — хүчингүй өгөгдөл бүртгэгдэж хамгийн шинэ жилийн статистикийг ч өөрчилнө.
Олдсон аялал: Couch Potato, Saboteur.

## `curl -i` нотолгоо
`../evidence/bug-09-curl.txt`, `../evidence/year-low.txt`, `../evidence/year-text.txt`, `../evidence/year-missing.txt`
