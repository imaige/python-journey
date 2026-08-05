# AI Engineering — Azərbaycan dilində qeydlər

Bu fayl AI/LLM Engineering kursunda keçilən mövzuların Azərbaycan dilində izahlı qeydləridir. Məqsəd terminləri sadəcə sadalamaq yox, onların məntiqini başa düşməkdir.

## LLM nədir?

LLM — Large Language Model, yəni böyük dil modelidir.

Sadə dillə desək, LLM böyük həcmdə mətn nümunələrindən dilin strukturlarını və əlaqələrini öyrənmiş modeldir. İstifadəçidən mətn qəbul edir və həmin kontekstə uyğun yeni mətn yaradır.

Məsələn:

```text
Sual → LLM → Cavab
```

LLM-lər aşağıdakı işlərdə istifadə oluna bilər:

- sual-cavab
- mətn yaratmaq
- kod yazmaq
- xülasə hazırlamaq
- müəllim/tutor kimi davranmaq
- kommersiya tətbiqlərinin arxasında AI funksionallığı vermək

## Cloud LLM və Local LLM fərqi

### Cloud LLM

ChatGPT kimi xidmətlərdə model adətən sənin kompüterində işləmir. Sən sorğunu internet vasitəsilə uzaqdakı serverə göndərirsən, model orada işləyir və cavab geri gəlir.

```text
Sənin kompüterin
    ↓
Internet / API
    ↓
Uzaqdakı server
    ↓
LLM
    ↓
Cavab
```

### Local LLM

Local LLM isə sənin öz kompüterində işləyən modeldir.

Model faylları lokalda olur və inference zamanı sənin CPU/GPU/RAM resurslarından istifadə edir.

```text
Sənin kompüterin
├── model faylları
├── RAM / VRAM
├── CPU / GPU
└── lokal inference
```

Local modelin üstünlükləri arasında öyrənmək, eksperiment aparmaq, müəyyən hallarda privacy və self-hosted işləmə imkanları var.

## Ollama nədir?

Ollama model deyil.

Ollama lokal LLM-ləri yükləmək, işə salmaq və onlarla işləmək üçün istifadə olunan alətdir.

```text
Gemma → model
Ollama → modeli lokal işlətməyə kömək edən proqram
```

Ümumi əmr məntiqi:

```bash
ollama run MODEL_NAME
```

Yəni Ollama model serving prosesini sadələşdirir.

## Parameter nədir?

Model ölçülərində belə yazılışlar görə bilərik:

```text
270M = 270 milyon parametr
3B   = 3 milyard parametr
20B  = 20 milyard parametr
```

Parameter modelin təlim zamanı öyrəndiyi daxili ədədi dəyərlərdir.

Ümumiyyətlə daha böyük model daha çox resurs tələb edə bilər:

- daha çox RAM/VRAM
- daha çox storage
- daha çox compute

Amma vacib prinsip budur:

```text
Ən böyük model = hər tapşırıq üçün ən yaxşı model deyil
```

AI Engineer tapşırığa uyğun model seçməlidir.

## LLM-ə rol vermək

LLM-ə sadəcə sual verməkdən əlavə, ona rol və məqsəd də təyin etmək olar.

Məsələn:

```text
Sən ispan dili müəllimisən.
Mən beginnerəm.
Mənimlə sadə dialoq apar.
```

Burada modeldən konkret davranış tələb olunur.

Bu bizi mühüm keçidə aparır:

```text
LLM istifadə etmək
      ↓
LLM üzərində tətbiq qurmaq
```

Kommersiya tətbiqində istifadəçi sadəcə UI görür, arxada isə LLM işləyə bilər.

## Reasoning / Thinking model nədir?

Bəzi modellər çoxmərhələli problemləri həll etmək üçün daha çox daxili hesablama aparmağa optimallaşdırılır.

Məsələn:

- plan qurmaq
- mürəkkəb hesablamalar
- texniki analiz
- qərarvermə
- addım-addım problem həlli

Sadə fakt sualı ilə mürəkkəb reasoning tapşırığı eyni səviyyədə hesablama tələb etmir.

## Frontier Model nədir?

Frontier model hazırkı dövrdə AI imkanlarının ön sıralarında olan ən güclü modellərə verilən addır.

Sadə dillə:

```text
frontier model = ən qabaqcıl capability səviyyəsində olan model
```

Bu anlayış sonradan open model-lərlə müqayisədə vacib olacaq.

## Open Model nədir?

Open model-lər çox vaxt lokal və ya öz infrastrukturu üzərində işlədilə bilən model ailələridir.

Məsələn kursda Gemma kimi lokal işlədilə bilən modellər göstərildi.

## 8 həftəlik AI Engineering roadmap

Kursun ümumi istiqaməti belədir:

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

Bu ardıcıllıq bünövrədən başlayıb production-a yaxın AI sistem düşüncəsinə aparır.

## RAG nədir?

RAG — Retrieval-Augmented Generation deməkdir.

Əsas məntiq:

```text
İstifadəçi sual verir
      ↓
Uyğun xarici məlumat tapılır
      ↓
Həmin məlumat LLM-ə kontekst kimi verilir
      ↓
LLM cavab yaradır
```

Məsələn şirkətin daxili sənədləri, incident report-ları və prosedurları varsa, LLM bunları avtomatik bilməyə bilər.

RAG sistemi lazım olan məlumatı tapıb modelə verə bilər.

Bu enterprise AI üçün çox vacibdir.

## RAG və Fine-Tuning fərqi

Bu iki anlayışı qarışdırmamaq lazımdır.

### RAG

Lazım olan məlumat sorğu zamanı tapılır və modelə kontekst kimi verilir.

### Fine-Tuning

Model əlavə nümunələrlə yenidən təlim edilərək davranışı və ya qabiliyyəti uyğunlaşdırılır.

```text
RAG != Fine-Tuning
```

## Agentic AI nədir?

Sadə LLM tətbiqi belə ola bilər:

```text
Sual → LLM → Cavab
```

Agentic sistem isə daha çox addım ata bilər:

```text
Məqsəd
 ↓
Plan
 ↓
Tool istifadə et
 ↓
Nəticəyə bax
 ↓
Növbəti addımı seç
 ↓
Final nəticə
```

Məsələn gələcək SOC agenti belə işləyə bilər:

```text
Alert
 ↓
IOC-ları yoxla
 ↓
Logları analiz et
 ↓
Threat intelligence yoxla
 ↓
Risk qiymətləndir
 ↓
Report hazırla
```

## AI Engineering track-ləri

Kurs müəllimi 6 kursdan ibarət curriculum təqdim etdi.

### AI Builder

No-code/low-code yanaşması ilə agent və voice agent qurmaq.

### AI Coder

Coding agent-lərdən istifadə edərək software development sürətini artırmaq.

### AI Leader

AI layihələrinin biznesdə tətbiqi və commercial impact.

### AI Engineer Core Track

Əsas texniki xətt:

- LLM
- API
- open models
- RAG
- fine-tuning
- model selection
- optimization

### AI Engineer Agentic Track

- agent loops
- agent SDK-lar
- MCP
- autonomous workflows

### AI Engineer Production Track

LLM və agent sistemlərini AWS, GCP və Azure kimi cloud platformalarda scale etmək.

Burada artıq aşağıdakılar önə çıxır:

- resiliency
- observability
- security
- production deployment

## Hugging Face, Gradio, LangChain və digər alətlər

Kursda gələcək üçün bu alətlərin adları çəkildi:

- Hugging Face
- Gradio
- LangChain
- Weights & Biases
- Modal

Hələ bu mərhələdə bunları dərindən keçməmişik. Sadəcə AI Engineering ekosistemində qarşılaşacağımız alətlər kimi qeyd olunub.

## Development Environment nədir?

AI layihəsinin işləməsi üçün təkcə `.py` faylı kifayət etmir.

Tipik development environment belə komponentlərdən ibarət ola bilər:

```text
Python version
+
Python packages
+
project files
+
IDE
+
API keys
+
environment variables
```

Bunlardan biri səhv qurularsa layihə işləməyə bilər.

## Git Clone nə edir?

`git clone` GitHub-dakı repository-ni lokal kompüterə gətirir.

```bash
git clone REPOSITORY_URL
```

Bu sadəcə faylları download etmir. Eyni zamanda Git metadata və repository əlaqəsini də gətirir.

## `projects` qovluğu

Development layihələrini ayrıca qovluqda saxlamaq səliqəli yanaşmadır.

Windows nümunəsi:

```powershell
mkdir projects
cd projects
```

Burada:

```text
mkdir → yeni qovluq yarat
cd    → qovluğa keç
ls    → qovluğun içini göstər
```

## Project Root nədir?

Project root layihənin ən yuxarı səviyyəli əsas qovluğudur.

Məsələn:

```text
llm-engineering/   ← project root
├── week1/
├── week2/
├── README.md
└── config faylları
```

IDE-də düzgün project root açmaq vacibdir, çünki Git, yollar, config və environment faylları bu strukturdan asılı ola bilər.

## Cursor nədir?

Cursor AI-assisted code editor-dur və VS Code ekosisteminə yaxındır.

Kursda Cursor tövsiyə olunur, amma məcburi deyil. VS Code, PyCharm və digər IDE-lər də istifadə oluna bilər.

Əsas məqsəd doğru layihə qovluğunu düzgün IDE-də açmaqdır.

## Python Environment nədir?

Fərqli layihələrin fərqli package və Python versiyalarına ehtiyacı ola bilər.

Ona görə hər layihə üçün ayrıca environment yaratmaq faydalıdır.

```text
Project A
└── öz environment-i

Project B
└── öz environment-i
```

Bu isolation verir və package konfliktlərinin qarşısını alır.

## Dependency nədir?

Dependency layihənin işləmək üçün asılı olduğu xarici package-dir.

Məsələn:

```text
openai
pandas
transformers
gradio
```

Kursda Python environment və dependency management üçün `uv` aləti təqdim edildi.

## API və API Key

API proqramların bir-biri ilə əlaqə qurması üçün interfeysdir.

LLM tətbiqində belə axın ola bilər:

```text
Python app
   ↓
API
   ↓
LLM provider
   ↓
Cavab
```

API key isə proqramın xidmətə autentikasiya üçün istifadə etdiyi credential-dır.

API key password kimi qorunmalıdır.

## `.env` faylı nədir?

Secret və config dəyərləri koddan ayrı saxlamaq üçün `.env` faylı istifadə oluna bilər.

Məsələn:

```env
OPENAI_API_KEY=your_key_here
```

Pis yanaşma:

```python
api_key = "secret-key"
```

çünki kod GitHub-a push olunanda key sızıntısı yarana bilər.

Əsas prinsip:

```text
code != secret
```

## Environment Variable nədir?

Environment variable proqramın xaricində saxlanan config dəyəridir.

Məsələn:

```text
OPENAI_API_KEY
DATABASE_URL
AWS_REGION
```

Kod runtime zamanı bu dəyərləri oxuya bilər.

Dəyişənin adı dəqiq olmalıdır. Məsələn `OPENAI_API_KEY` ilə `OPEN_AI_API_KEY` proqram üçün fərqli adlardır.

## Documentation-first troubleshooting

Kursda mühüm engineering vərdişi vurğulandı:

```text
Problem
 ↓
README / official documentation
 ↓
Troubleshooting guide
 ↓
Error message analysis
 ↓
LLM-dən kömək
 ↓
Təklifi yoxla
 ↓
Sonra tətbiq et
```

LLM debugging üçün faydalıdır, amma onun dediyini kor-koranə icra etmək düzgün deyil.

## Windows setup-da qeyd olunan nüanslar

PC environment setup hissəsində aşağıdakılar qeyd olundu:

- PowerShell
- Git-in quraşdırıldığını yoxlamaq
- lazım olsa Run as Administrator
- VPN problemləri
- Windows 260-character path limiti
- düzgün project root açmaq

Bu problemlər real olaraq qarşımıza çıxsa, ayrıca debug ediləcək.

## Hazırkı vəziyyət

AI Engineering mövzusu ilkin foundations və PC environment setup mərhələsindən sonra müvəqqəti dayandırılıb.

Python öyrənmə prosesi əvvəlki qaydada davam edir.

AI kursuna qayıdanda bu fayl keçilən yeni mövzularla paralel şəkildə Azərbaycan dilində yenilənəcək.
