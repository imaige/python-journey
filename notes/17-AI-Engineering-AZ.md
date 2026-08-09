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

`README.md` Markdown formatında yazılmış fayldır. Cursor-da `.md` faylını adi açdıqda Markdown mənbəyini, `Open Preview` etdikdə isə formatlanmış görünüşünü görürük.

## Cursor Terminal

Cursor-un öz daxilində terminal var. Kursda shortcut belə göstərildi:

```text
Ctrl + `
```

Buradakı işarə backtick-dir. Birdən çox terminal açmaq mümkündür.

# Step 2 — `uv` və Python Environment

## Dependency nədir?

Dependency layihənin işləmək üçün ehtiyac duyduğu əlavə package/library-dir. Məsələn `openai`, `pandas`, `transformers` və `gradio`.

## Virtual Environment və `.venv`

Fərqli Python layihələri fərqli package versiyaları tələb edə bilər. Ona görə hər layihəyə ayrıca izolyasiya olunmuş Python mühiti yaradırıq. Buna virtual environment deyilir.

Bu kursda həmin environment `.venv` qovluğunda yerləşir.

```text
llm_engineering/
├── week1/
├── week2/
├── README.md
└── .venv/
```

## `uv`

`uv` Python environment və dependency-ləri idarə etmək üçün istifadə olunan alətdir.

```bash
uv --version
uv self update
uv sync
```

`uv sync` layihənin dependency-lərini və virtual environment-ini uyğunlaşdırır və `.venv` mühitini hazırlayır.

```text
dependency → layihənin ehtiyac duyduğu əlavə package
virtual environment → layihəyə aid izolyasiya olunmuş Python mühiti
.venv → həmin environment-in qovluğu
uv → environment və dependency-ləri idarə edən alət
uv sync → layihənin environment-ini hazırlayan/sinxronlaşdıran əmr
```

# Step 3 — OpenAI API və API Key

ChatGPT hazır istifadəçi məhsuludur. OpenAI API isə bizim yazdığımız proqramın OpenAI modelləri ilə proqram vasitəsilə əlaqə qurması üçündür.

```text
Python proqramı
      ↓
OpenAI API
      ↓
Model
      ↓
Cavab
```

API-ni iki proqramın bir-biri ilə danışdığı yol kimi düşünmək olar.

API key proqramın API xidmətinə qoşulmaq üçün istifadə etdiyi gizli açardır. Onu parol kimi qorumaq lazımdır və GitHub-a göndərmək olmaz.

# Step 4 — `.env` və Secret Management

API key-i birbaşa Python kodunda saxlamaq təhlükəlidir. Buna görə secret məlumatı koddan ayrı `.env` faylında saxlayırıq.

```env
OPENAI_API_KEY=your_secret_key
```

Burada `OPENAI_API_KEY` dəyişənin adı, sağ tərəfdəki hissə isə gizli dəyərdir.

Əsas prinsip:

```text
code != secret
```

# Step 5 — Cursor Extensions və Jupyter Setup

Bu, environment setup-ın son mərhələsidir. Məqsəd Cursor-u Python və Jupyter Notebook-larla işləməyə hazırlamaqdır.

## Python Extension

Cursor-a Python extension quraşdırılır. Bu əlavə Cursor-un Python kodunu daha yaxşı tanımasına, kodun rənglənməsinə və yoxlanmasına kömək edir.

Kursda Cursor/Anysphere və Microsoft tərəfindən təqdim edilən Python extension variantlarının hər ikisinin uyğun olduğu qeyd edilir.

## Jupyter Extension

Sonra Jupyter extension quraşdırılır. Bu extension Cursor daxilində `.ipynb` notebook-larını açmağa və işlətməyə imkan verir.

Extensions quraşdırıldıqdan sonra Explorer-ə qayıdıb ilk notebook açılır:

```text
week1/day1.ipynb
```

## Jupyter Notebook nədir?

Jupyter Notebook adi `.py` faylından fərqli olaraq mətn, kod və kodun nəticəsini eyni sənəddə saxlaya bilən interaktiv sənəddir.

```text
Jupyter Notebook
├── izah / mətn
├── Python kodu
├── nəticə
├── növbəti izah
└── növbəti kod
```

Notebook fayllarının uzantısı:

```text
.ipynb
```

Kursda bunlara həm notebook, həm də lab deyilə bilər.

## Cell nədir?

Notebook daxilindəki ayrı-ayrı hissələrə `cell` deyilir.

Məsələn bir code cell:

```python
x = 10
```

başqa code cell:

```python
print(x)
```

ola bilər. Hər code cell ayrıca işlədilə bilər. Buna görə bütün proqramı hər dəfə başdan sona işlətmək məcburiyyətində deyilik.

Bu yanaşma kodu hissə-hissə yoxlamaq və eksperiment aparmaq üçün çox rahatdır.

## Kernel nədir?

Notebook özü kodu işlətmir. Notebook-dakı Python kodunu arxa planda işlədən Python prosesinə `kernel` deyilir.

Sadə məntiq:

```text
Jupyter Notebook
      ↓
Kernel
      ↓
Python kodunu işləyir
      ↓
Nəticə
```

Yəni notebook sənəddir, kernel isə həmin sənəddəki kodu həqiqətən işlədən mühərrikdir.

## Niyə `.venv` Kernel seçirik?

Əvvəl `uv sync` vasitəsilə layihəmiz üçün `.venv` yaratmışdıq. Həmin environment-də layihənin Python-u və lazım olan dependency-lər var.

Jupyter Notebook açıldıqda hansı Python environment-in istifadə ediləcəyini seçməliyik:

```text
Select Kernel
      ↓
Python Environments
      ↓
.venv / recommended Python
```

Beləliklə əvvəlki mövzu ilə Step 5 birləşir:

```text
uv sync
   ↓
.venv yaranır
   ↓
Python + dependency-lər hazır olur
   ↓
Jupyter Notebook açılır
   ↓
.venv kernel seçilir
   ↓
Notebook həmin layihə mühitində işləyir
```

Əgər `.venv` kernel siyahısında görünməzsə, kursdakı `setup` qovluğunda olan troubleshooting notebook-dan istifadə etmək lazımdır.

# Notebook-larla necə işləyəcəyik?

Müəllimin yanaşması kodu sadəcə ekrandan kopyalamaq deyil. Məqsəd kodun necə və niyə işlədiyini başa düşməkdir.

Tövsiyə olunan proses:

```text
İzahı oxu
 ↓
Kodu başa düş
 ↓
Cell-i işə sal
 ↓
Nəticəyə bax
 ↓
print əlavə et
 ↓
Kodu dəyiş
 ↓
Eksperiment apar
```

Notebook-lar kurs boyunca yenilənə bilən canlı sənədlərdir. Buna görə videodakı məzmunla repository-dəki notebook arasında kiçik fərqlər ola bilər.

# İlk real LLM layihəsi — Web Page Summarizer

Environment setup bitdikdən sonra ilk LLM layihəsinə başlayırıq.

Layihənin məqsədi istifadəçidən web səhifənin URL-ni götürmək, həmin səhifənin məlumatını əldə etmək, GPT modelinə göndərmək və səhifənin xülasəsini yaratmaqdır.

Sadə proses:

```text
URL
 ↓
Web səhifə əldə/scrape edilir
 ↓
Lazım olan məzmun çıxarılır
 ↓
Python proqramı
 ↓
OpenAI API
 ↓
GPT modeli
 ↓
Xülasə yaradılır
 ↓
Formatlanmış nəticə göstərilir
```

Bu layihə əvvəl öyrəndiyimiz anlayışların bir yerdə işləməyə başladığı ilk praktik nümunədir:

```text
GitHub repository
       ↓
Cursor
       ↓
uv
       ↓
.venv
       ↓
Jupyter Notebook
       ↓
Kernel (.venv)
       ↓
Python kodu
       ↓
OPENAI_API_KEY (.env)
       ↓
OpenAI API
       ↓
GPT
       ↓
Web səhifənin xülasəsi
```

# Troubleshooting yanaşması

Problem olduqda əvvəl README/rəsmi documentation və kursun troubleshooting notebook-u yoxlanılır. LLM-dən kömək almaq olar, amma verdiyi təkliflər yoxlanmadan tətbiq edilməməlidir.

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
Python/Jupyter extensions + Notebook + Kernel
                                    ✅
```

Environment setup tam başa çatıb. Növbəti mərhələ ilk praktik LLM lab-ı — Web Page Summarizer layihəsidir.
