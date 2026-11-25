# Lab 07 — Exploratory Testing and SBTM

- **Оюутан:** Дэлгэрмаа
- **Оюутны код:** B232270035
- **Систем:** Debian GNU/Linux 13.7
- **Node.js:** `v20.20.2`
- **Браузер:** Codex in-app browser (engine version харагдаагүй); Mozilla Firefox `153.7.0esr` системд суусан боловч session-д ашиглаагүй.
- **Repository:** https://github.com/b232270035-oss/lab07

## Session-ийн тойм

2026-11-26-ны 00:58:40–01:58:40 (Asia/Ulaanbaatar) хооронд 60 минутын exploratory session хийж, 13 асуудлыг шалгаж баримтжуулав. Session-ийг Codex-ийн browser automation-аар local апп дээр гүйцэтгэсэн. Charter-ийг эхлэхээс өмнө `47f6e24` commit-оор хадгалсан; session тайлангийн commit нь session дууссаны дараа хийгдсэн.

- UI болон өгөгдөл: `bugs/bug-01.md`–`bug-07.md`, `bug-10.md`–`bug-12.md`
- API болон validation: `bugs/bug-08.md`, `bug-09.md`, `bug-13.md`
- `curl -i` нотолгоонууд: `evidence/`

## Гол дүгнэлт

Supermodel аялал хамгийн олон хэрэглэгчийн урсгалын асуудлыг илрүүлсэн: тоолуур, оны формат, хайлт, `/old` холбоос, устгах товчны өнгө, давхардсан ном. Couch Potato аяллаар хоосон болон дутуу талбар, whitespace-only оролт, жилийн хилээс давсан болон бүхэл бус утгууд баталгаажуулалтгүйг харуулав. Saboteur аяллаар malformed JSON-д 200 буцах, буруу жилийн өгөгдөл хадгалагдах, ижил ном давхардах, JSON `null` server-ийг унагахыг `curl -i`-ээр шалгав. Хамгийн үр дүнтэй нь шинэ өгөгдөл бүрийн дараа UI жагсаалт, `/api/books`, `/api/stats`-ийг зэрэгцүүлэн тулгасан явдал байв. Charter-ийн үндсэн чиглэлээс гадуур устгасны дараах буруу мессеж, урт гарчгийн layout overflow, HTML entity давхар escape болох асуудал илэрсэн. Энэ session-д concurrent request, keyboard-only accessibility болон өөр browser engine-үүдийн ялгааг шалгаагүй тул дараагийн charter эдгээр чиглэлд төвлөрч болно. Playwright тестээр жагсаалтын мөр ба stats тоог, оны формат, required-field validation, case-insensitive хайлт, duplicate prevention болон `/old` status-ийг автоматжуулж шалгаж болох байв. HTTP буруу payload болон `null`-ийн crash-ийг API түвшний автомат тест барина. Ногоон устгах товч, буруу toast болон хүснэгтийн overflow-г screenshot assertion-оор автоматжуулж болох ч хүний харааны шалгалт эдгээрийг хурдан танихад үр дүнтэй.
