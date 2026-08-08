# AI Engineering — Azərbaycan dilində qeydlər

Bu fayl AI/LLM Engineering kursunda keçilən mövzuların Azərbaycan dilində izahlı qeydləridir. Məqsəd terminləri sadəcə sadalamaq yox, onların məntiqini başa düşməkdir.

## LLM və model anlayışları

LLM — Large Language Model, yəni böyük dil modelidir. Mətn qəbul edir və öyrəndiyi dil nümunələrinə əsasən cavab yaradır. LLM-lər sual-cavab, kodlaşdırma, xülasə, tutor və kommersiya AI tətbiqlərində istifadə edilə bilər.

Cloud LLM uzaqdakı serverdə işləyir. Local LLM isə lokal kompüterin CPU/GPU və RAM/VRAM resurslarından istifadə edə bilər.

Ollama model deyil. Lokal LLM-ləri yükləmək və işlətmək üçün istifadə olunan alətdir.

```bash
ollama run MODEL_NAME
```

`270M`, `3B`, `20B` kimi yazılışlar parametr sayını göstərir. Böyük model adətən daha çox resurs tələb edir, amma ən böyük model hər tapşırıq üçün avtomatik ən yaxşı seçim deyil.

Frontier model hazırkı AI imkanlarının ön sıralarında olan güclü modeldir. Open model-lər çox vaxt lokal və ya öz infrastrukturumuzda işlədilə bilər. Reasoning/Thinking modelləri çoxmərhələli problem, planlaşdırma, hesablama və texniki analiz kimi tapşırıqlara optimallaşdırıla bilər.

## Kursun 8 həftəlik istiqaməti

```text
Week 1  → Foundations
Week 2  → Frontier Models
Week 3  → Open Models
Week 4  → Model Selection
Week 5  → RAG
Week 6  → Frontier Model Fine-Tuning
Week 7  → Open Model Fine-Tuning
Week 8  → Agentic AI
```

RAG xarici məlumatı sorğu zamanı tapıb LLM-ə kontekst kimi verir. Fine-tuning isə modeli əlavə nümunələr üzərində yenidən təlim edərək uyğunlaşdırır. Bunlar eyni şey deyil.

Agentic sistem sadə `Sual → LLM → Cavab` axınından daha irəli gedərək plan qura, tool istifadə edə, nəticəni yoxlaya və növbəti addımı seçə bilər.

Kursda AI Builder, AI Coder, AI Leader, AI Engineer Core, AI Engineer Agentic və AI Engineer Production track-ləri təqdim edildi. Hugging Face, Gradio, LangChain, Weights & Biases və Modal kimi alətlərin də gələcəkdə istifadə ediləcəyi qeyd olunub, amma onları hələ dərindən keçməmişik.

# Development Environment

AI layihəsinin işləməsi üçün təkcə kod kifayət etmir. Layihə faylları, Git, IDE, Python environment, dependency-lər, API key-lər və environment variable-lar birlikdə düzgün qurulmalıdır.

## Git Clone və Project Root

`git clone` GitHub repository-sini faylları və Git metadata-sı ilə birlikdə lokal kompüterə gətirir.

Project root layihənin ən yuxarı əsas qovluğudur:

```text
llm_engineering/   ← project root
├── week1/
├── week2/
├── README.md
└── digər layihə faylları
```

Cursor-da məhz project root açılmalıdır.

## Cursor Explorer, Markdown və README

Cursor-un sol tərəfində repository faylları görünmürsə:

```text
View → Explorer
```

seçilir.

`README.md` Markdown formatında yazılmış fayldır. Markdown sadə mətnə başlıq, siyahı və kod bloku kimi formatlama imkanları verən sintaksisdir.

Cursor-da `.md` faylını adi açdıqda Markdown mənbəyini görürük. `Open Preview` etdikdə formatlanmış görünüşünü görürük.

Repository `git clone` edildiyi üçün README və guide-lar artıq lokal kompüterdə də mövcuddur.

## Cursor Terminal

Cursor-un öz daxilində terminal var. Kursda shortcut belə göstərildi:

```text
Ctrl + `
```

Buradakı işarə backtick-dir. Birdən çox terminal açmaq mümkündür. Beləliklə layihənin əmrlərini IDE daxilindən icra edə bilərik.

# Step 2 — `uv` və Python Environment

## Dependency nədir?

Dependency layihənin işləmək üçün ehtiyac duyduğu əlavə package/library-dir.

Məsələn:

```text
openai
pandas
transformers
gradio
```

Sadə məntiq:

```text
Proqram
  ↓
İşləmək üçün başqa package-ə ehtiyac duyur
  ↓
Həmin package dependency-dir
```

## Virtual Environment nədir?

Fərqli Python layihələri fərqli package və package versiyaları tələb edə bilər. Bunların hamısını eyni ümumi Python mühitində saxlamaq konflikt yarada bilər.

Ona görə hər layihəyə ayrıca izolyasiya olunmuş Python mühiti yaradırıq:

```text
Project A → öz environment-i
Project B → öz environment-i
```

Buna virtual environment deyilir.

## `.venv` nədir?

Bu kursda virtual environment layihənin daxilində `.venv` qovluğunda yaradılır.

```text
llm_engineering/
├── week1/
├── week2/
├── README.md
└── .venv/    ← bu layihənin virtual environment-i
```

`.venv` bütün kompüter üçün ümumi mühit deyil. Konkret layihəyə aid izolyasiya olunmuş Python mühitidir.

## `uv` nədir?

`uv` Python environment və dependency-ləri idarə etmək üçün istifadə olunan alətdir. Kursun əvvəlki versiyasında Anaconda istifadə olunurdu, hazırkı versiyada isə `uv` seçilib.

Sadə analogiya:

```text
Layihə        = ev
Dependencies  = ev üçün lazım olan əşyalar
.venv         = həmin evin şəxsi anbarı
uv            = anbarı idarə edən şəxs
uv sync       = siyahıya bax və lazım olanları uyğunlaşdır
```

Texniki məntiq:

```text
Project requirements
        ↓
       uv
        ↓
Python environment + dependencies
```

## `uv --version`

```bash
uv --version
```

Bu əmr `uv`-nin quraşdırılıb-quraşdırılmadığını və terminal tərəfindən tanınıb-tanınmadığını yoxlayır.

Əgər `uv` yeni quraşdırılıb, amma terminal onu görmürsə, yeni terminal açmaq lazım ola bilər. Səbəb yeni terminalın PATH/environment dəyişikliklərini yenidən oxumasıdır. Lazım gəlsə sistem restart edilə bilər.

## `uv self update`

```bash
uv self update
```

Bu əmr `uv` alətinin özünü son versiyaya yeniləyir.

## `uv sync`

Əsas əmr:

```bash
uv sync
```

Sadə dillə:

> Layihənin hansı environment və dependency-lərə ehtiyacı olduğunu nəzərə al və həmin layihə üçün uyğun Python mühitini hazırla/sinxronlaşdır.

Proses:

```text
uv sync
   ↓
layihənin konfiqurasiyasını nəzərə alır
   ↓
lazım olan dependency-ləri uyğunlaşdırır
   ↓
virtual environment qurur
   ↓
.venv yaranır
   ↓
layihənin Python mühiti hazır olur
```

`sync` sözü synchronization, yəni uyğunlaşdırmaq/sinxronlaşdırmaq mənasındadır.

## Əsas fərqlər

```text
dependency
→ layihənin ehtiyac duyduğu əlavə package

virtual environment
→ layihə üçün ayrıca izolyasiya olunmuş Python mühiti

.venv
→ həmin virtual environment-in yerləşdiyi qovluq

uv
→ environment və dependency-ləri idarə edən alət

uv sync
→ layihənin environment-ini tələb olunan vəziyyətlə sinxronlaşdıran əmr
```

# API, API Key və `.env` — ilkin anlayışlar

API proqramların bir-biri ilə əlaqə qurmasına imkan verən interfeysdir. API key proqramın xarici xidmətə autentikasiya üçün istifadə etdiyi credential-dır və secret kimi qorunmalıdır.

`.env` secret və config dəyərlərini koddan ayrı saxlamaq üçün istifadə oluna bilər:

```env
OPENAI_API_KEY=your_key_here
```

Əsas prinsip:

```text
code != secret
```

Bu mövzular kursda növbəti setup addımlarında daha detallı keçiləcək.

# Troubleshooting yanaşması

```text
Problem
 ↓
README / rəsmi documentation
 ↓
Troubleshooting guide
 ↓
Error-u analiz et
 ↓
Lazım olsa LLM-dən kömək al
 ↓
LLM-in təklifini yoxla
 ↓
Sonra tətbiq et
```

LLM debugging üçün faydalıdır, amma verdiyi cavab avtomatik doğru qəbul edilməməlidir.

# Hazırkı kurs vəziyyəti

```text
STEP 1
Git + repository clone + Cursor + project root
                                    ✅

STEP 2
README/Markdown + Cursor terminal + uv + dependency
+ virtual environment + .venv + uv sync
                                    ✅

STEP 3
OpenAI API                         ⏭️

STEP 4
.env / environment variables      qarşıdadır

STEP 5
Final editor/Jupyter setup        qarşıdadır
```

Hazırda Setup Step 2-ni tamamlamışıq. Növbəti AI dərsində Step 3-dən davam edəcəyik.
