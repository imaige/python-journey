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

Cursor-un sol tərəfində repository faylları görünmürsə `View → Explorer` seçilir.

`README.md` Markdown formatında yazılmış fayldır. Markdown sadə mətnə başlıq, siyahı və kod bloku kimi formatlama imkanları verən sintaksisdir. Cursor-da `.md` faylını adi açdıqda Markdown mənbəyini, `Open Preview` etdikdə isə formatlanmış görünüşünü görürük.

Repository `git clone` edildiyi üçün README və guide-lar artıq lokal kompüterdə də mövcuddur.

## Cursor Terminal

Cursor-un öz daxilində terminal var. Kursda shortcut belə göstərildi:

```text
Ctrl + `
```

Buradakı işarə backtick-dir. Birdən çox terminal açmaq mümkündür.

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

## Virtual Environment nədir?

Fərqli Python layihələri fərqli package və package versiyaları tələb edə bilər. Bunların hamısını eyni ümumi Python mühitində saxlamaq konflikt yarada bilər. Ona görə hər layihəyə ayrıca izolyasiya olunmuş Python mühiti yaradırıq. Buna virtual environment deyilir.

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

## Əsas `uv` əmrləri

```bash
uv --version
```

`uv`-nin quraşdırılıb və terminal tərəfindən tanınıb-tanınmadığını yoxlayır.

```bash
uv self update
```

`uv` alətinin özünü yeniləyir.

```bash
uv sync
```

Layihənin dependency-lərini və virtual environment-ini tələb olunan vəziyyətlə uyğunlaşdırır. Nəticədə `.venv` yaradılır və layihənin Python mühiti hazır olur.

Əgər `uv` yeni quraşdırılıb, amma terminal onu görmürsə, yeni terminal açmaq lazım ola bilər. Lazım gəlsə sistem restart edilə bilər.

# Step 3 — OpenAI API və API Key

## ChatGPT və OpenAI API eyni şey deyil

ChatGPT istifadəçinin hazır məhsul kimi istifadə etdiyi xidmətdir. OpenAI API isə bizim yazdığımız proqramın OpenAI modelləri ilə birbaşa əlaqə qurması üçündür.

Sadə axın:

```text
Python proqramı
      ↓
OpenAI API
      ↓
Model
      ↓
Cavab
```

Yəni proqram daxilindən modelə sorğu göndərmək üçün API istifadə olunur.

## API nədir?

API-ni sadə şəkildə iki proqramın bir-biri ilə danışdığı yol kimi düşünmək olar.

Bizim nümunədə:

```text
Python proqramı → OpenAI API → OpenAI modeli
```

## API Key nədir?

API key proqramın OpenAI xidmətinə hansı hesab vasitəsilə qoşulduğunu tanıtmaq üçün istifadə olunan gizli açardır.

Onu parol kimi düşünmək olar:

```text
Python proqramı
      ↓
API key
      ↓
OpenAI proqramı tanıyır
      ↓
API-dən istifadə edilir
```

API key secret-dir. Onu paylaşmaq və açıq GitHub repository-sinə göndərmək olmaz.

# Step 4 — `.env` və Secret Management

## `.env` nədir?

API key-i birbaşa Python kodunun daxilində saxlamaq təhlükəlidir. Kod GitHub-a göndərildikdə secret də təsadüfən yayıla bilər.

Buna görə secret məlumatı koddan ayrı `.env` faylında saxlayırıq.

```text
Python kodu → proqramın kodu
.env        → secret/config məlumatları
```

`.env` faylı project root-da yerləşməlidir:

```text
llm_engineering/
├── week1/
├── week2/
├── README.md
└── .env       ← düzgün yer
```

Faylın adı dəqiq `.env` olmalıdır.

## `OPENAI_API_KEY`

`.env` daxilində OpenAI API key belə saxlanılır:

```env
OPENAI_API_KEY=your_secret_key
```

Burada:

```text
OPENAI_API_KEY = dəyişənin adı
your_secret_key = onun gizli dəyəri
```

Adın dəqiq yazılması vacibdir, çünki proqram sonradan məhz `OPENAI_API_KEY` adlı məlumatı axtaracaq.

## Niyə API key kodun içində saxlanmır?

Pis yanaşma:

```python
api_key = "real-secret-key"
```

Belə kod GitHub-a push edilərsə key də yayıla bilər.

Düzgün məntiq:

```text
.env
 │
 └── OPENAI_API_KEY=secret
          ↓
     Python proqramı
          ↓
       OpenAI API
          ↓
          Model
```

Əsas prinsip:

```text
code != secret
```

`.env` faylı yaradıldıqdan və key əlavə edildikdən sonra faylın save edilməsi də vacibdir.

## Sadə yadda saxlama modeli

```text
API
→ Python ilə OpenAI arasında əlaqə yolu

API Key
→ OpenAI qarşısında proqramın gizli açarı

.env
→ həmin gizli məlumatı koddan ayrı saxladığımız fayl

OPENAI_API_KEY
→ .env daxilində API key-in saxlandığı dəyişənin adı
```

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
OpenAI API + API key
                                    ✅

STEP 4
.env + OPENAI_API_KEY + secret management
                                    ✅

STEP 5
Final editor/Jupyter setup        ⏭️
```

Hazırda Setup Step 4-ü tamamlamışıq. Növbəti AI dərsində Step 5-dən davam edəcəyik.
