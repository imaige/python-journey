# AI Engineering — Azərbaycan dilində qeydlər

Bu fayl AI/LLM Engineering kursunda keçilən mövzuların Azərbaycan dilində izahlı qeydləridir. Məqsəd terminləri sadəcə yadda saxlamaq yox, onların nə olduğunu, niyə istifadə edildiyini və sistemdə nəyə təsir etdiyini başa düşməkdir.

# LLM və əsas model anlayışları

## LLM nədir?

LLM — Large Language Model, yəni böyük dil modelidir. Mətn qəbul edir və öyrəndiyi dil nümunələrinə əsasən yeni mətn yaradır.

İstifadə sahələri:

- sual-cavab
- kodlaşdırma
- tutor sistemi
- mətn xülasəsi
- chatbot
- kommersiya AI tətbiqləri

## Cloud LLM və Local LLM

Cloud LLM uzaqdakı serverdə işləyir:

```text
Python
  ↓
Internet / API
  ↓
Cloud model
  ↓
Cavab
```

Local LLM isə bizim kompüterdə işləyir:

```text
Python
  ↓
localhost
  ↓
Local model
  ↓
Cavab
```

Local model CPU/GPU və RAM/VRAM resurslarını bizim kompüterdən istifadə edir.

## Ollama nədir?

Ollama model deyil. Lokal LLM-ləri yükləmək, işə salmaq və onlarla API vasitəsilə danışmaq üçün istifadə olunan alətdir.

```bash
ollama run MODEL_NAME
```

Məsələn kurs praktikası üçün lokal `gpt-oss` modeli işlədildi.

## Model ölçüsü və parameter sayı

`270M`, `3B`, `20B` kimi yazılışlar təxminən modelin parametr sayını bildirir.

```text
M → million
B → billion
```

Böyük model adətən daha çox resurs tələb edir, amma böyük model avtomatik olaraq hər tapşırıq üçün ən yaxşı model demək deyil.

## Frontier və Open model

Frontier model hazırkı AI imkanlarının ön sıralarında olan güclü modeldir.

Open model-lər isə çox vaxt yüklənib lokal və ya şəxsi infrastrukturda işlədilə bilər.

## Reasoning / Thinking model

Reasoning model birbaşa cavab vermək əvəzinə daha çox daxili hesablama və çoxmərhələli problem həlli üçün optimallaşdırıla bilər.

Məsələn:

- planlaşdırma
- texniki analiz
- riyazi problemlər
- çox addımlı qərarlar

# Kursun 8 həftəlik istiqaməti

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

## RAG və Fine-Tuning fərqi

RAG xarici məlumatı sorğu zamanı tapıb modelə əlavə context kimi verir.

Fine-tuning isə modelin özünü əlavə nümunələrlə yenidən öyrətməkdir.

```text
RAG
→ məlumatı modelə request zamanı gətirir

Fine-Tuning
→ modelin davranışını əlavə training ilə dəyişir
```

Bunlar eyni şey deyil.

## Agentic AI

Agentic sistem sadə:

```text
Sual → Model → Cavab
```

axınından daha irəli gedə bilər.

Agent:

- plan qura bilər
- tool istifadə edə bilər
- nəticəni yoxlaya bilər
- növbəti addımı seçə bilər

# Development Environment

AI layihəsinin işləməsi üçün təkcə Python kodu kifayət etmir.

```text
Project files
Git
IDE
Python
Dependencies
Virtual Environment
API keys
Environment Variables
Jupyter Kernel
```

hamısı birlikdə düzgün işləməlidir.

## Git Clone və Project Root

`git clone` GitHub repository-sini lokal kompüterə gətirir.

Project root isə layihənin əsas üst qovluğudur.

```text
llm_engineering/
├── week1/
├── week2/
├── README.md
└── digər fayllar
```

Cursor-da bütün layihə ilə işləmək üçün project root açılır.

## Cursor, Explorer və Markdown

Cursor kursda istifadə olunan IDE/editor-dur.

Repository faylları görünmürsə:

```text
View → Explorer
```

istifadə olunur.

`README.md` Markdown faylıdır. Onu source kimi və ya `Open Preview` ilə formatlanmış formada görmək olar.

## Cursor terminal

Cursor daxilində ayrıca terminal mövcuddur.

```text
Ctrl + `
```

ilə açıla bilər.

# `uv`, dependency və `.venv`

## Dependency nədir?

Dependency layihənin ehtiyac duyduğu xarici package/library-dir.

Məsələn:

```text
openai
pandas
transformers
gradio
```

## Virtual Environment nədir?

Hər layihənin öz Python və package mühitinin olması üçün ayrıca izolyasiya olunmuş environment yaradırıq.

```text
Project A → Environment A
Project B → Environment B
```

Bu kursda həmin environment:

```text
.venv/
```

qovluğunda saxlanılır.

## `uv` nə edir?

`uv` Python project, package və environment idarəetmə alətidir.

Əsas əmrlər:

```bash
uv --version
uv self update
uv sync
```

`uv sync` layihənin metadata/lock məlumatlarına uyğun olaraq `.venv` environment-ini hazırlayır və lazım olan dependency-ləri sinxronlaşdırır.

Sadə yadda saxlama:

```text
dependency → layihənin ehtiyac duyduğu package
virtual environment → layihəyə aid izolyasiya olunmuş Python mühiti
.venv → həmin mühitin qovluğu
uv → environment və dependency-ləri idarə edən alət
uv sync → mühiti layihənin tələbləri ilə uyğunlaşdırır
```

# OpenAI API və API Key

## ChatGPT və API eyni şey deyil

ChatGPT hazır istifadəçi məhsuludur.

OpenAI API isə bizim proqramımızın model ilə proqramatik danışması üçündür.

```text
Python proqramı
      ↓
OpenAI API
      ↓
Model
      ↓
Response
```

## API nədir?

API iki proqramın bir-biri ilə strukturlaşdırılmış şəkildə danışdığı interfeysdir.

## API Key nədir?

API key proqramın API xidmətinə özünü tanıtmaq üçün istifadə etdiyi gizli credential-dır.

Onu parol kimi qorumaq lazımdır.

API key:

- source code-a hard-code edilməməlidir
- GitHub-a commit edilməməlidir
- ictimai paylaşılmamalıdır

## ChatGPT billing və API billing ayrıdır

Vacib praktiki dərs:

```text
ChatGPT subscription ≠ OpenAI API credit
```

Yəni ChatGPT ödənişli işləyə bilər, amma API hesabında ayrıca credit olmaya bilər.

API request-in mərhələləri belə düşünülə bilər:

```text
DNS
 ↓
TCP connection
 ↓
TLS handshake
 ↓
HTTP request
 ↓
API key authentication
 ↓
quota / billing
 ↓
model execution
```

Buna görə məsələn TLS xətası çıxırsa problem billing mərhələsinə hələ çatmamış ola bilər.

Əksinə server `credit_balance_exhausted` kimi cavab verirsə request artıq serverə çatıb və billing mərhələsində dayanıb.

# `.env` və Secret Management

API key-i birbaşa kodda saxlamaq təhlükəlidir.

Buna görə `.env` istifadə edirik:

```env
OPENAI_API_KEY=your_secret_key
```

Burada:

```text
OPENAI_API_KEY → dəyişənin adı
your_secret_key → gizli dəyər
```

Əsas prinsip:

```text
code != secret
```

# Jupyter Notebook

## Notebook nədir?

Jupyter Notebook mətn, executable Python code və nəticəni bir sənəddə saxlaya bilən interaktiv mühitdir.

```text
Notebook
├── izah
├── code cell
├── output
├── izah
└── növbəti code cell
```

Notebook faylları `.ipynb` uzantılıdır.

## Cell nədir?

Notebook daxilindəki ayrı bloklara `cell` deyilir.

Code cell ayrıca işlədilə bilər.

```text
Shift + Enter
```

cari cell-i işə salır.

## Kernel nədir?

Kernel notebook-dakı Python kodunu arxa planda işlədən Python prosesidir.

```text
Jupyter Notebook
      ↓
Kernel
      ↓
Python kodu
      ↓
Output
```

## Niyə `.venv` kernel seçirik?

Layihənin dependency-ləri `.venv` daxilindədir.

Ona görə notebook-un da həmin environment-in Python-u ilə işləməsi lazımdır.

```text
uv sync
   ↓
.venv
   ↓
project Python + packages
   ↓
Jupyter kernel
```

# Jupyter-də import edilmiş modul niyə köhnə qala bilər?

Jupyter kernel state saxlayır.

Məsələn:

```python
from scraper import fetch_website_contents
```

bir dəfə işlətdikdən sonra `scraper.py` faylını dəyişsək belə kernel köhnə import edilmiş versiyanı yaddaşda saxlaya bilər.

Bu halda:

```python
import importlib
import scraper

importlib.reload(scraper)
```

ilə modulu yenidən yükləmək olar.

Sadə məntiq:

```text
scraper.py dəyişdi
      ↓
Jupyter bunu avtomatik bilməyə bilər
      ↓
importlib.reload()
      ↓
yeni kod kernel-ə yüklənir
```

Bu, AI-dən çox Python/Jupyter debugging dərsidir, amma real layihədə çox vacibdir.

# İlk real LLM layihəsi — Web Page Summarizer

Layihənin məqsədi:

```text
URL götür
 ↓
Website məlumatını al
 ↓
Lazımsız hissələri təmizlə
 ↓
Mətni prompt-a əlavə et
 ↓
LLM-ə göndər
 ↓
Summary al
```

Tam pipeline:

```text
Website URL
    ↓
HTML əldə edilir
    ↓
BeautifulSoup
    ↓
Təmiz website text
    ↓
User Prompt
    ↓
System + User messages
    ↓
LLM
    ↓
Summary
```

Buradakı ən vacib dərs:

> LLM özü gedib website-i oxumadı.

Biz əvvəl website-dən məlumatı götürdük, sonra həmin mətni modelə verdik.

# Web Scraping AI deyil

Scraping hissəsinin işi yalnız məlumatı əldə etməkdir:

```text
Website
   ↓
Scraper
   ↓
Text
```

AI hissəsi bundan sonra başlayır:

```text
Text
 ↓
LLM
 ↓
Summary
```

Yəni:

```text
Scraper → məlumatı gətirir
LLM → məlumatı anlayır və nəticə yaradır
```

# BeautifulSoup nə edir?

Website-dən gələn HTML-in içində çoxlu lazımsız element olur.

Məsələn:

- script
- style
- image tag-ləri
- input elementləri
- navigation mətnləri

BeautifulSoup HTML-i parse edir və bizə lazım olan visible text-i çıxarmağa kömək edir.

# Restricted TLS mühitində öyrəndiyimiz ümumi troubleshooting dərsi

Bəzi şəbəkələrdə security proxy, TLS inspection və ya endpoint security layer HTTPS bağlantısına müdaxilə edə bilər.

Belə vəziyyətdə:

```text
Python application
      ↓
HTTP library
      ↓
TLS/OpenSSL
      ↓
Network security layer
      ↓
Website/API
```

zəncirinin hansı hissəsində xəta olduğunu ayırmaq lazımdır.

Əgər bir OS-native client işləyir, amma Python HTTPS client sertifikat xətası verir, bu iki client-in eyni TLS implementation istifadə etməməsi ilə bağlı ola bilər.

Vacib prinsip:

> İlk həll kimi `verify=False` edib certificate verification-u söndürmək düzgün yanaşma deyil.

Əvvəl root cause tapılmalıdır.

Kurs lab-ında public website HTML-i almaq üçün OS-native `curl.exe` çağırılıb, parsing isə Python-da saxlanılıb.

Helper:

```python
import subprocess


def fetch_html(url):
    result = subprocess.run(
        ["curl.exe", "-L", "-sS", url],
        capture_output=True,
        check=True,
    )
    return result.stdout
```

Sonra:

```python
html = fetch_html(url)
soup = BeautifulSoup(html, "html.parser")
```

Beləliklə architecture dəyişmir:

```text
Website
 ↓
HTML retrieval
 ↓
BeautifulSoup
 ↓
Text
```

sadəcə transport hissəsi lokal mühitə uyğunlaşdırılır.

# OpenAI message strukturu

Modelə chat formatında mesajları list daxilində dictionary-lər kimi göndəririk.

```python
messages = [
    {
        "role": "system",
        "content": system_prompt
    },
    {
        "role": "user",
        "content": user_prompt
    }
]
```

Burada Python fundamentals real AI kodunda işləyir:

```text
messages → list

hər mesaj → dict

role / content → key

system_prompt / user_prompt → value
```

# System Prompt və User Prompt

## System Prompt

System prompt modelə ümumi davranış verir.

```text
Sən kimsən?
Ümumi tapşırığın nədir?
Nəyə fokuslanmalısan?
Cavab hansı formada olmalıdır?
```

Məsələn:

```text
Website məzmununu analiz et.
Qısa summary hazırla.
Lazımsız navigation hissələrini nəzərə alma.
```

## User Prompt

User prompt həmin anda görülməli konkret işi bildirir.

```text
Bu website-i xülasə et.
```

Sadə yadda saxlama:

```text
SYSTEM PROMPT
→ necə davran

USER PROMPT
→ indi nə et
```

Eyni user prompt saxlanılıb system prompt dəyişdirilsə, modelin tonu və davranışı dəyişə bilər.

# f-string ilə website məlumatını prompt-a salmaq

Python f-string dəyişənin dəyərini string-in içinə yerləşdirməyə imkan verir.

Sadə nümunə:

```python
name = "Movsum"
text = f"Hello {name}"
```

Nəticə:

```text
Hello Movsum
```

Web Summarizer-də:

```python
user_prompt = f"""
Please summarize this website:

{ed}
"""
```

buradakı `{ed}` yerinə `ed` dəyişənində saxlanmış website text yerləşir.

Yəni modelə əslində belə məlumat gedir:

```text
Please summarize this website:

[website-dən çıxardığımız real mətn]
```

# Cloud client və Local client

Normal OpenAI cloud client belə yaradıla bilər:

```python
from openai import OpenAI

openai = OpenAI()
```

Bu halda client OpenAI cloud endpoint-ə getməyə çalışır.

Lokal Ollama ilə isə:

```python
local_ai = OpenAI(
    base_url="http://localhost:11434/v1/",
    api_key="ollama"
)
```

Burada ən vacib hissə:

```python
base_url="http://localhost:11434/v1/"
```

Bu client-ə deyir:

> OpenAI cloud serverinə yox, mənim kompüterimdə işləyən Ollama serverinə get.

Axın:

```text
Cloud:
Python
 ↓
api.openai.com
 ↓
Cloud model

Local:
Python
 ↓
localhost:11434
 ↓
Ollama
 ↓
Local model
```

`api_key="ollama"` real OpenAI secret deyil. OpenAI-compatible client interface-in gözlədiyi sahəni doldurmaq üçün placeholder kimi istifadə olunur.

# OpenAI-compatible API nə deməkdir?

Burada vacib AI Engineering anlayışı öyrəndik.

Ollama başqa sistemdir, amma OpenAI-yə bənzər API interface təqdim edə bilər.

Buna görə eyni Python client və oxşar kod strukturu istifadə oluna bilir:

```python
response = local_ai.chat.completions.create(
    model="gpt-oss:latest",
    messages=messages
)
```

Bu bizə göstərir ki, application logic ilə konkret model/provider bir-birindən müəyyən qədər ayrıdır.

```text
Application logic
      ↓
Model interface
      ↓
Cloud model VƏ YA local model
```

# Response necə alınır?

Modelin yaratdığı real mətn:

```python
response.choices[0].message.content
```

ilə götürülür.

Mental model:

```text
response
   ↓
choices
   ↓
[0]
   ↓
message
   ↓
content
```

`content` bizim oxumaq istədiyimiz model cavabıdır.

# İlk uğurlu Local LLM call

Notebook-dan lokal model uğurla çağırıldı.

Məntiq:

```text
messages
   ↓
OpenAI-compatible Python client
   ↓
localhost:11434
   ↓
Ollama
   ↓
gpt-oss
   ↓
response
```

Bu praktika ilə aşağıdakılar real olaraq işlədi:

- Python-dan LLM çağırmaq
- `messages` strukturu
- system prompt
- user prompt
- local model inference
- response oxumaq

# Web Page Summarizer — yekun işləyən sistem

Son nəticədə layihə tam işlək vəziyyətə gəldi:

```text
edwarddonner.com
      ↓
HTML retrieval
      ↓
BeautifulSoup
      ↓
Təmiz website text
      ↓
f-string user prompt
      ↓
system + user messages
      ↓
local_ai
      ↓
Ollama
      ↓
gpt-oss
      ↓
Website Summary
```

Bu, ilk real kiçik AI application-dır.

Əsas formula:

```text
Data acquisition
      +
Prompt construction
      +
LLM inference
      =
AI Application
```

# Ən vacib memarlıq dərsi

Bu layihədə hissələr bir-birindən ayrıdır:

```text
Data Source
   ↓
Data Retrieval
   ↓
Data Preparation
   ↓
Prompt
   ↓
Model Interface
   ↓
Model
   ↓
Output Handling
```

Məsələn cloud model yerinə local model keçirdik, amma:

- `messages`
- system prompt
- user prompt
- website text
- response processing

kimi application məntiqinin çox hissəsi dəyişmədi.

Bu gələcək AI Engineering mövzularında çox vacib olacaq.

# Day 1 Exercise — Öz business task-ımızı sıfırdan qurmaq

Day 1-in son praktik tapşırığında məqsəd hazır Web Page Summarizer kodunu sadəcə təkrarlamaq yox, eyni LLM məntiqini başqa biznes probleminə tətbiq etmək idi.

Biz **email subject generator** qurduq.

Məqsəd:

```text
Email mətni
   ↓
LLM
   ↓
Qısa və peşəkar Subject
```

İstifadə olunan kod:

```python
from openai import OpenAI

local_ai = OpenAI(
    base_url="http://localhost:11434/v1/",
    api_key="ollama"
)

system_prompt = """
E-poçtun Subject hissəsini göndərilən mətnin məzmununa uyğun olaraq avtomatik yarat.
Subject qısa, aydın və peşəkar olmalı, e-poçtun əsas mövzusunu dəqiq ifadə etməlidir.
E-poçtun əsas mətnini dəyişdirmə, qısaltma və ya ona əlavə məlumat daxil etmə.
"""

email = """
Hi team,
The project meeting has been moved from Monday to Wednesday at 3 PM.
Please update your calendars.
Thanks.
"""

user_prompt = f"""
Mətn:
{email}
Bu məzmuna uyğun qısa və peşəkar Subject yarat.
"""

messages = [
    {"role": "system", "content": system_prompt},
    {"role": "user", "content": user_prompt}
]

response = local_ai.chat.completions.create(
    model="gpt-oss:latest",
    messages=messages
)

print(response.choices[0].message.content)
```

## Bu exercise-də nəyi sübut etdik?

Əvvəl qurduğumuz sistem belə idi:

```text
Website
  ↓
Instruction
  ↓
LLM
  ↓
Summary
```

İndi eyni architecture-ni belə dəyişdik:

```text
Email
  ↓
Instruction
  ↓
LLM
  ↓
Subject
```

Yəni əsas skill konkret `summarizer` yazmaq deyil. Əsas skill eyni LLM application pattern-i başqa problemə tətbiq edə bilməkdir.

## System Prompt burada nə edir?

System prompt modelə daimi qaydaları verir:

```text
Subject yarat
↓
qısa olsun
↓
aydın olsun
↓
peşəkar olsun
↓
email-in əsas mövzusuna sadiq qalsın
```

Bu qaydalar `output constraints` kimi düşünülə bilər. Yəni modelə sadəcə nə etməli olduğunu yox, nəticənin necə olmalı olduğunu da deyirik.

## User Prompt burada nə edir?

User prompt konkret email-i və həmin email üçün görülməli işi verir:

```text
Bu email budur
↓
Buna uyğun Subject yarat
```

`f-string` içindəki `{email}` dəyişənin real məzmununu user prompt-a daxil edir.

## `messages` niyə yenə eyni qaldı?

Çünki business task dəyişsə də modelə mesaj göndərmə interface-i dəyişmədi:

```python
messages = [
    {"role": "system", "content": system_prompt},
    {"role": "user", "content": user_prompt}
]
```

Bu çox vacib memarlıq dərsidir:

```text
Application logic dəyişə bilər
amma
Model interface çox vaxt eyni qala bilər
```

## Ümumi GenAI formulu

Bu exercise-dən sonra daha ümumi formula belədir:

```text
DATA
  +
INSTRUCTION
  +
LLM
  =
AI APPLICATION
```

Məsələn eyni pattern ilə:

```text
Email + instruction → Subject
Email + instruction → Summary
Məqalə + instruction → Translation
Review + instruction → Sentiment
Document + instruction → Key Points
```

kimi fərqli tətbiqlər qurmaq olar.

# Troubleshooting-dən öyrəndiyimiz qaydalar

1. Xətanın adını və traceback-i tam oxu.
2. Problemin hansı layer-də olduğunu ayır.
3. Connection error ilə billing error-u qarışdırma.
4. TLS xətasında certificate verification-u dərhal söndürmə.
5. Bir client işləyib digəri işləmirsə onların fərqli transport/TLS stack istifadə edə biləcəyini nəzərə al.
6. Jupyter kernel-in state saxladığını unutma.
7. `.py` faylı dəyişəndən sonra lazım gələrsə modulu reload et.
8. Bir anda çox dəyişiklik etmə, hər fix-i ayrıca test et.
9. Root cause tapmadan nəticə elan etmə.

# Hazırkı kurs vəziyyəti

```text
Environment setup                                  ✅
uv + .venv                                         ✅
Jupyter Notebook + Kernel                          ✅
.env və API key anlayışı                           ✅
ChatGPT vs API fərqi                               ✅
API billing vs ChatGPT billing                     ✅
OpenAI message structure                           ✅
System Prompt və User Prompt                       ✅
f-string prompt construction                       ✅
Web scraping                                       ✅
BeautifulSoup                                      ✅
Local LLM with Ollama                              ✅
OpenAI-compatible local client                     ✅
Response handling                                  ✅
Jupyter module reload anlayışı                     ✅
Web Page Summarizer                                ✅
Email Subject Generator                            ✅
Day 1 custom business LLM exercise                 ✅
```

Artıq Day 1-in həm ilk real LLM application hissəsi, həm də həmin architecture-ni başqa business task-a uyğunlaşdırmaq exercise-i tamamlanıb.