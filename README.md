# Анализ IDE и ИИ-помощников для командной разработки

## Цель документа

Целью данного анализа является определение оптимальных IDE и методов интеграции ИИ-помощников (таких как GitHub Copilot, JetBrains AI Assistant, локальные LLM-агенты) в командную разработку с использованием стеков: C++, C#, TypeScript, Python, Kotlin Multiplatform, с ориентацией на работу в Linux.

## Основные платформы и IDE

Современные платформы для разработки можно условно разделить на три категории:

1. **JetBrains IDE** (CLion, PyCharm, IntelliJ IDEA, Rider, WebStorm, Android Studio)
   - Кроссплатформенные (Linux поддерживается полностью).
   - Платные (есть бесплатные community-версии).
   - Хорошо интегрируются с GitHub Copilot и JetBrains AI Assistant.
   - Интеграция собственных ИИ сложнее (из-за закрытой экосистемы), требуется написание собственных плагинов.

2. **Visual Studio**
   - Основной выбор для C# и .NET.
   - Linux не поддерживается (только Windows).
   - GitHub Copilot интегрирован официально.
   - Интеграция своих агентов практически невозможна.

3. **VSCode**
   - Лёгкая, расширяемая IDE.
   - Полностью бесплатная и кроссплатформенная.
   - Поддержка GitHub Copilot, Amazon CodeWhisperer и любых сторонних ИИ-плагинов.
   - Лучшая среда для подключения собственных локальных LLM (Continue.dev, Tabby, CodeGPT, LocalPilot).
   - Большое коммьюнити и маркетплейс плагинов.

---

## Обзор ИИ-помощников

1. **GitHub Copilot / Copilot Chat**  
   - Официальный продукт для автодополнения и генерации кода.
   - Поддерживается в VSCode, Visual Studio, JetBrains IDE.

2. **JetBrains AI Assistant**  
   - Инструмент для IntelliJ, PyCharm, CLion и других IDE JetBrains.
   - Платный сервис, работает через облачные модели OpenAI, Gemini и др.

3. **Amazon CodeWhisperer**  
   - Аналог Copilot от AWS.
   - Интеграция в VSCode и JetBrains IDE.

4. **Локальные ИИ-агенты / свои LLM**  
   Поддержка в основном через плагины в VSCode:
   - **Continue.dev** — open-source агент.
   - **TabbyML** — локальный аналог Copilot.
   - **CodeGPT** — плагин для подключения своего API (OpenAI, LLaMA, локальные модели).
   - **LocalPilot** — вариант локального Copilot.

JetBrains IDE и Visual Studio в этом плане более закрыты и заточены под коммерческие решения.

---

## Сравнительная таблица IDE

| IDE                  | Языки        | Преимущества          | Наличие Copilot | Наличие JetBrains AI | Существующие ИИ агенты | Можно добавить своих агентов? | Стоимость           | Поддержка Linux | Поддержка Windows |
|----------------------|---------------------------|-------------------------------|--------------------|------------------------|------------------------|-------------------------------|----------------------|-----------------|--------------------|
| VSCode               | Все (особенно TypeScript, Python) | Лёгкая, быстрая, максимально расширяемая | Да | Нет | Copilot, CodeWhisperer, Continue.dev, Tabby, CodeGPT | Да, очень легко (через плагины и API) | Бесплатно | Да | Да |
| Visual Studio        | C#, C++, .NET             | Глубокая интеграция с Microsoft экосистемой | Да (Copilot Chat встроен) | Нет | Copilot | Нет (закрытая архитектура) | Платно (около $45/мес для Pro, $250/год для Community бесплатно) — [цены](https://visualstudio.microsoft.com/vs/pricing/) | Нет | Да |
| Rider (JetBrains)    | C#, .NET, TypeScript      | Кроссплатформенность, глубоко интегрированная поддержка C# | Да (через плагин Copilot) | Да | Copilot, JetBrains AI Assistant | Нет (закрытая архитектура, возможно только через плагины) | Платно (~$149/год) — [цены](https://www.jetbrains.com/store/) | Да | Да |
| IntelliJ IDEA        | Java, Kotlin, KMP, TypeScript | Стандарт для JVM и мультиплатформенной разработки | Да (через плагин Copilot) | Да | Copilot, JetBrains AI Assistant | Нет (только через разработку плагинов) | Платно (~$149/год) — [цены](https://www.jetbrains.com/store/) | Да | Да |
| PyCharm              | Python                    | Оптимально для профессиональной Python-разработки | Да (через плагин Copilot) | Да | Copilot, JetBrains AI Assistant | Нет | Платно (~$99/год) — [цены](https://www.jetbrains.com/store/) | Да | Да |
| CLion                | C++, C, Rust              | Инструменты анализа кода C++, хорошая работа с CMake, поддержка Docker | Да (через плагин Copilot) | Да | Copilot, JetBrains AI Assistant | Нет | Платно (~$99/год) — [цены](https://www.jetbrains.com/store/) | Да | Да |
| WebStorm             | TypeScript, JavaScript    | Профессиональная поддержка фронтенд-стека | Да (через плагин Copilot) | Да | Copilot, JetBrains AI Assistant | Нет | Платно (~$99/год) — [цены](https://www.jetbrains.com/store/) | Да | Да |
| Android Studio       | Kotlin, Java (Android)    | Разработка под Android, нативная поддержка Kotlin Multiplatform | Да (через плагин Copilot) | Да (через JetBrains AI Assistant) | Copilot, JetBrains AI Assistant | Нет | Бесплатно | Да | Да |


## Пояснения

- **Copilot доступен**  
  Почти везде, включая VSCode, Visual Studio, JetBrains IDE (IntelliJ, PyCharm, CLion, Rider, WebStorm, Android Studio). В JetBrains IDE подключается через официальный плагин GitHub Copilot.

- **JetBrains AI Assistant**  
  Доступен только в IDE компании JetBrains (IntelliJ IDEA, PyCharm, Rider, CLion, WebStorm, Android Studio). Платный сервис, использующий внешние модели (OpenAI, Gemini и др.).

- **Существующие ИИ агенты**  
  Перечислены текущие доступные решения, такие как GitHub Copilot, Amazon CodeWhisperer, JetBrains AI Assistant, а также open-source агенты (Tabby, Continue.dev, CodeGPT) для VSCode.

- **Возможность добавить своих агентов**  
  - **VSCode** — лидер в этой категории. Открытая архитектура, огромное количество open-source плагинов, возможность подключения любых LLM через API (CodeGPT, Continue.dev, Tabby, LocalPilot и другие).
  - **JetBrains IDE** (CLion, PyCharm, IntelliJ, WebStorm, Rider) — закрытая архитектура, свои агенты можно добавить только через написание собственного плагина на Kotlin/Java.
  - **Visual Studio** — крайне ограниченные возможности. Собственные агенты подключить практически невозможно без модификации самой IDE.

- **Платность**  
  - JetBrains IDE — коммерческие продукты. Есть **All Products Pack** для доступа ко всем IDE. Стоимость от $149 в год за одну IDE.  
    [Цены JetBrains](https://www.jetbrains.com/store/).  
  - Visual Studio — платно для версий Professional и Enterprise. Бесплатна только Community-версия (ограничена по лицензированию).  
    [Цены Visual Studio](https://visualstudio.microsoft.com/vs/pricing/).  
  - **VSCode** и **Android Studio** — полностью бесплатные.

- **Поддержка ОС**  
  - Все JetBrains IDE, VSCode и Android Studio работают в Linux, Windows и macOS.  
  - Visual Studio работает только в Windows.


## Рекомендации по каждому языку

### C++
- Основная IDE: CLion (для крупных проектов и работы с CMake).
- Вспомогательная IDE: VSCode (лёгкая работа с файлами, эксперименты).
- ИИ-помощники: Copilot (плагин в CLion), JetBrains AI Assistant, локальные агенты в VSCode.
- Интеграция своих агентов: использовать VSCode.

### C#
- Основная IDE: Rider (Linux), Visual Studio (Windows).
- Вспомогательная IDE: VSCode для мелких задач.
- ИИ-помощники: Copilot (везде), JetBrains AI Assistant (в Rider).
- Интеграция своих агентов: практически невозможно в Rider и Visual Studio — использовать VSCode.

### TypeScript / JavaScript
- Основная IDE: VSCode (де-факто стандарт).
- Альтернативно: WebStorm (JetBrains) для глубоких проектов.
- ИИ-помощники: Copilot, CodeWhisperer, локальные агенты (Continue.dev, Tabby).
- Рекомендуется использовать VSCode для локальных LLM и агентов.

### Python
- Основная IDE: PyCharm.
- Вспомогательная IDE: VSCode.
- ИИ-помощники: Copilot, JetBrains AI Assistant.
- Для экспериментов с локальными моделями: использовать VSCode.

### Kotlin Multiplatform
- Основная IDE: IntelliJ IDEA или Android Studio.
- ИИ-помощники: Copilot, JetBrains AI Assistant.
- Интеграция локальных агентов: ограничена, использовать VSCode для экспериментов.

---

## Интеграция ИИ и локальных LLM

### Где лучше использовать ИИ-помощников:
- **JetBrains IDE**: Copilot (плагин), JetBrains AI Assistant.
- **VSCode**: максимальная свобода. Можно подключить:
  - GitHub Copilot.
  - Amazon CodeWhisperer.
  - Продвинутые open-source решения (Continue.dev, TabbyML, CodeGPT, LocalPilot).

### Какие LLM лучше использовать для кода:
| Модель            | Почему использовать                          | Лицензия         |
|-------------------|----------------------------------------------|-------------------|
| Code LLaMA        | Специализирована для кода, хорошее качество   | Open-source (Meta)|
| StarCoder 2       | Обучена на больших кодовых датасетах, infill  | Open-source       |
| DeepSeek-Coder    | Эффективна для TypeScript, Python             | Open-source       |
| WizardCoder       | Хороша для автодополнения                     | Open-source       |
| Phi-3             | Лёгкая, подходит для локального запуска       | Open-source (Microsoft)|
| GPT-4 (Turbo)     | Высшее качество, но закрытая                  | Закрытая (OpenAI) |
| Claude 3          | Хорошо пишет код, но закрытая                 | Закрытая (Anthropic) |
| Amazon CodeWhisperer | Прямой аналог Copilot от AWS               | Закрытая (AWS)         |


### Где запускать локальные агенты:
- Использовать **VSCode** с плагинами:
  - [Continue.dev](https://continue.dev)
  - [TabbyML](https://tabbyml.github.io) *
  - [CodeGPT](https://marketplace.visualstudio.com/items?itemName=DanielSanMedium.dscodegpt)
  - [LocalPilot](https://github.com/danielgross/localpilot)

---

## Итоговые рекомендации

1. **Стандартизировать JetBrains IDE** как основную рабочую среду (CLion, Rider, IntelliJ, PyCharm).
2. Использовать **VSCode** как обязательную вспомогательную IDE:
   - Для экспериментов с локальными LLM.
   - Для написания кастомных агентов.
   - Для работы с open-source экосистемой.
3. Для ИИ-помощников:
   - Использовать **GitHub Copilot** (везде).
   - Использовать **JetBrains AI Assistant** (в JetBrains IDE).
   - Развивать эксперименты с локальными агентами на базе **Code LLaMA, StarCoder 2, DeepSeek-Coder**.
4. развёртывание локальных LLM и собственных агентов:
   - Требований к приватности кода (работа в закрытых или защищённых контурах).
   - Потребности в кастомизации и интеграции ИИ в специфичные процессы.
   - Сокращения затрат на облачные подписки Copilot, CodeWhisperer и аналогичные сервисы.
  Рекомендуется использовать:
     - **TabbyML** — open-source аналог Copilot, позволяющий подключать свои модели.
     - **Continue.dev** — агент для VSCode, поддерживающий локальные и удалённые LLM.
     - **CodeGPT** — плагин для VSCode, подключающий любое API.
     - **Code LLaMA**, **StarCoder 2**, **DeepSeek-Coder**, **WizardCoder**, **Phi-3** — в качестве языковых моделей.
5. Использование локальных решений:
     - Контроль над ИИ-инфраструктурой.
     - Отсутствие утечки исходного кода во внешние облачные сервисы.
     - Возможность адаптации ИИ под специфику проекта (через дообучение или кастомные промпты).
   
---

## Обеспечение единого стиля кода в команде

В условиях многоплатформенной и многопрофильной разработки важно унифицировать стиль кода между различными языками и IDE. Несогласованный стиль приводит к ухудшению читаемости, росту количества merge-конфликтов и снижению качества проекта.

### Рекомендуемый подход:

### 1️⃣ Внедрение `.editorconfig`

Файл `.editorconfig` является стандартом, поддерживаемым большинством современных IDE (VSCode, JetBrains IDE, Visual Studio, Android Studio). Этот файл определяет базовые параметры форматирования:

### Для каждого языка проекта необходимо внедрить стандартные инструменты:

| Язык        | Рекомендуемые инструменты                 |
|-------------|-------------------------------------------|
| **Python**  | Black, Flake8, isort                      |
| **TypeScript / JavaScript** | ESLint, Prettier          |
| **C++**     | clang-format                              |
| **C#**      | dotnet-format, StyleCop                   |
| **Kotlin**  | ktlint                                    |


---

## Источники

- [GitHub Copilot](https://github.com/features/copilot)
- [JetBrains AI Assistant](https://www.jetbrains.com/ai/)
- [Amazon CodeWhisperer](https://aws.amazon.com/codewhisperer/)
- [TabbyML (open-source Copilot)](https://tabbyml.github.io) *
- [Continue.dev (open-source агент для VSCode)](https://continue.dev)
- [VSCode Marketplace](https://marketplace.visualstudio.com/)
- [Meta Code LLaMA](https://ai.meta.com/research/publications/code-llama/) *
- [StarCoder 2](https://huggingface.co/bigcode/starcoder2) *
- [DeepSeek-Coder](https://huggingface.co/DeepSeek-AI) 
- [WizardCoder](https://huggingface.co/WizardLM/WizardCoder) *
- [Microsoft Phi-3](https://huggingface.co/microsoft/phi-3-mini)
- [LocalPilot](https://github.com/danielgross/localpilot)
- [OpenAI API](https://platform.openai.com/)
- [Anthropic Claude](https://www.anthropic.com/claude)
