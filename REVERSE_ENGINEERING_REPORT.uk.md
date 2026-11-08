# ЗВІТ З РЕВЕРСНОЇ ІНЖЕНЕРІЇ — HL7Norway/Medications

## Оригінальний репозиторій
- Назва: Medications
- URL: https://github.com/HL7Norway/Medications
- Тип: Implementation Guide FHIR R4 для профілів ліків (HL7 Норвегія / Helse Nord)
- Гілка: master
- База: f757b7c Merge pull request #21 from andrePancinha2/patch-2

## Дата аудиту
2026-11-07

## Використані інструменти
- Git v2.49.0
- PowerShell 5.1
- gh (GitHub CLI), автентифіковано як admeduardovieira
- Kilo Code (статичний аналіз файлів XML/JSON/markdown)

## Виявлена архітектура
FHIR R4 Implementation Guide для профілів ліків регіону VKP (Норвегія). Містить:
- `StructureDefinition/` — профілі FHIR (наприклад, sfm-Medication.StructureDefinition.xml)
- `CodeSystems/` — CodeSystems (наприклад, SFMAdmByCodeSystem.xml)
- `ValueSet/` — ValueSets
- `Examples/` — приклади ресурсів
- `ImplementationGuide/` — конфігурація IG
- `NamingSystem/` — визначення систем іменування
- `Script/` — допоміжні скрипти
- `Images/` — діаграми та знімки екрана

Виконавчий код відсутній; лише клінічні/FHIR визначення.

## Технології та залежності
- FHIR R4 (4.0.0)
- Жодних залежностей не оголошено в package.json (файл ігнорується в .gitignore)

## Стан обслуговування
- ~21 коміт
- 3 PR (усі злито; останній 2026-10-27)
- 1 Issue закрита (#3 "Update readme" — CLOSED)
- Немає автоматизованих тестів
- README відсутній (bul "readme" з 4 байтів до виправлення)

## Обмеження дослідження
- Не є проєктом виконавчого коду; немає середовища для валідації збирання FHIR
- SUSHI/releaselabel не поширюється (немає sushi-config.yaml)

---

## Виявлені проблеми (Medications)

| ID | Sev | Статус | Місцезнаходження | Проблема | Виправлення застосовано |
|---|---|---|---|---|---|
| REA-001 | P3 | ПІДТВЕРДжено | `readme` (4 байти) | Файл "readme" з лише словом "Test" — без корисної документації | Замінено на підходящий README.md (призначення, структура, версіонування, ліцензія) |
| REA-002 | P3 | ПІДТВЕРДжено | `.gitignore` | Мінімальний `.gitignore` (лише `fhirpkg.lock.json`, `StructureDefinition/package.json`, `package.json`); не ігнорує збирання/вивід/ОС | `.gitignore` розширено з fsh-generated/, output/, temp/, *.zip, *.log, .DS_Store, Thumbs.db |
| REA-003 | P3 | ГІПОТЕЗА | `sfm-Medication.StructureDefinition.xml:7` | Профіль з `<status value="draft" />` — без ознаки, чи готові до продакшну | Не виправлено (потребує клінічного перегляду домену) |
| REA-004 | P2 | ЙМОВІРНО | `sfm-Medication.StructureDefinition.xml:13` | `baseDefinition` вказує на `http://hl7.no/fhir/StructureDefinition/no-basis-Medication` — зовнішня залежність | Не виправлено (зовнішня залежність; вимагає підтвердження секретаря проєкту) |

## Повторювані проблеми
- PR #3 "Update readme" (CLOSED) — свідчить, що документація вже була предметом попередніх виправлень, але залишалася неадекватною (readme з 4 байтів).

## Нездокументовані помилки (нові з аудиту)
REA-001, REA-002, REA-003, REA-004 не мають публічного запису.

## Зміни, що було впроваджено (Фаза 2)
1. `readme` → `README.md`: замінити 4-байтовий файл ("Test") на належний README.md з призначенням, структурою, версіонуванням, ліцензією.
2. `.gitignore`: розширено з fsh-generated/, output/, temp/, *.zip, *.log, .DS_Store, Thumbs.db.

## Зміни, що НЕ було впроваджено (потребує рішення секретаря проєкту або клінічного перегляду)
- REA-003: перегляд статусу `draft` профілів FHIR (клінічний домен).
- REA-004: зовнішня залежність `no-basis-Medication` — вимагає підтвердження секретаря проєкту.

## Валідація, що проведено
- Статичний перегляд файлів XML/markdown.
- Не виконано: збирання FHIR/SUSHI (не застосовується).

## Залишаючіся ризики
- Зовнішні залежності (`hl7.no/fhir/...`) можуть бути недоступні.
- Профілі зі статусом `draft` можуть не бути готовими до продакшну.

## Рекомендації для майбутніх аудитів
- Вирішити Issues, пов'язані з документуванням та валідацією профілів.
- Додати базовий CI для валідації XML FHIR.
