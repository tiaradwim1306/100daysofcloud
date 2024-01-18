# Machine Learning : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### Amazon Rekognition
service yang digunakan untuk find objects, people, text, scenes in images and videos using ML. Bisa melakukan analysis dan pencarian wajah untuk melakukan verifikasi pengguna, dan menghitung seberapa banyak orang dalam sebuah gambar.

Use cases: Labeling, Content Moderation, Text Detection, Face Detection and Analysis (gender, age range, emotions…), Face Search and Verification, Celebrity Recognition, Pathing (ex: for sports game analysis)

Content Moderation
- Mendeteksi konten yang tidak pantas, tidak diinginkan, atau menyinggung (gambar dan video)
- Digunakan di media sosial, media penyiaran, periklanan, dan situasi e-commerce untuk menciptakan pengalaman pengguna yang lebih aman
- Tetapkan Batas Keyakinan Minimum untuk item yang akan ditandai
- Tandai konten sensitif untuk tinjauan manual di Amazon Augmented AI (A2I)
- Membantu mematuhi peraturan

### Amazon Transcribe
otomatis convert speech to text, use a deep learning process called automatic speech recognition (ASR) to convert speech to text quickly and accurately.
otomatis menghapus Personally Identifiable Information (PII) using Redaksi. Support dentifikasi Bahasa Otomatis untuk audio multibahasa. 

Use case : transcribe customer service calls, mengotomatiskan teks dan subtitle, generate metadata for media assets to create a fully searchable archive.

### Amazon Polly
convert text ke speech using deep learning, memungkinkan membuat aplikasi yang berbicara.
- Customize the pronunciation of words with Pronunciation lexicons, 
     - Stylized words: St3ph4ne => “Stephane”
     - Acronyms: AWS => “Amazon Web Services”
- Upload the lexicons and use them in the SynthesizeSpeech operation
- Generate speech from plain text or from documents, ditandai dengan Speech Synthesis Markup Language (SSML) – enables more customization
   - menekankan kata atau frasa tertentu
   - menggunakan pengucapan fonetik
   - termasuk suara nafas, berbisik
   - menggunakan gaya bicara Newscaster
 
### Amazon Translate
Natural and accurate language translation, Amazon Translate memungkinkan Anda melokalkan konten - seperti situs web dan aplikasi - untuk pengguna internasional, dan dengan mudah menerjemahkan teks dalam jumlah besar secara efisien

### Amazon Lex & Connect
<b>Amazon Lex</b> : Automatic Speech Recognition (ASR) to convert speech to text, Natural Language Understanding untuk mengenali maksud teks, penelepon. Membantu membangun chatbot (bot pusat panggilan), 

<b>Amazon Connect</b> : receive calls, create contact flow, cloud-based virtual contact center. can integrate with other CRM (Customer Relationship Management) system or AWS. no upfront payment and 80% cheaper than traditional contact center solutions

### Amazon Comprehend 
For Natural Language Processing (NLP), Fully managed and serverless service, use machine learning to find insight and relationship text : 
- Language of the text
- Extracts key phrases, places, people, brands, or events
- Understands how positive or negative the text is
- Analyzes text using tokenization and parts of speech
- Automatically organizes a collection of text files by topic

Sample use cases : 
- menganalisis interaksi pelanggan (email) untuk menemukan apa yang mengarah pada pengalaman positif atau negatif
- Membuat dan mengelompokkan artikel berdasarkan topik yang akan diungkap oleh Pemahaman

### Amazon Comprehend Medical 
detects and returns useful information in unstructured clinical text : Physician’s notes, Discharge summaries, Test result, Case notes.
Menggunakan NLP untuk mendeteksi semua Protected Health Information (PHI). 
> Simpan dokumen Anda di Amazon S3, analisis data real-time dengan Kinesis Data Firehose, atau gunakan Amazon Transcribe untuk menyalin narasi pasien ke dalam teks yang dapat dianalisis oleh Amazon Comprehend Medical.

### Amazon SageMaker
Fully managed service for developers / data scientists to build ML models, Biasanya untuk membuat ML kita sulit melakukan semua proses di satu tempat + penyediaan server. Untuk itu kita bisa menggunakan sagemaker.

### Amazon Forecast
Fully managed service yang menggunakan ML untuk memberikan perkiraan yang sangat akurat, example: predict the future sales of a raincoat. 50% lebih akurat dibandingkan melihat datanya sendiri. Mengurangi waktu perkiraan dari bulan menjadi jam.
> Use cases: Product Demand Planning, Financial Planning, Resource Planning, …

### Amazon Kendra
document search service powered by Machine Learning, Extract answers from within a document (text, pdf, HTML, PowerPoint, MS Word, FAQs...).
Natural language search capabilities, Belajar dari interaksi/umpan balik pengguna untuk mendorong hasil yang diinginkan (Pembelajaran Tambahan).
Kemampuan untuk menyempurnakan hasil pencarian secara manual (pentingnya data, kesegaran, kustom, ...)

### Amazon Personalize
Fully managed ML-service to build apps with real-time personalized recommendations, example : 
- Rekomendasi/pemeringkatan ulang produk yang dipersonalisasi, pemasaran langsung yang disesuaikan 
- Pengguna membeli peralatan berkebun, memberikan rekomendasi pembelian berikutnya
Integrates into existing websites, applications, SMS, email marketing systems, etc. Implement in days, not months (you don’t need to build, train, and deploy ML solutions)
> Use cases: retail stores, media and entertainment...

### Amazon Textract
Automatically extracts text, handwriting, and data from any scanned documents using AI and ML.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/44513a7f-daa2-4562-a59d-1345016584c1)

extract data from forms and tables, read and process any type of document (PDFs, images, etc). Use cases :
- Financial Services (e.g., invoices, financial reports)
- Healthcare (e.g., medical records, insurance claims)
- Public Sector (e.g., tax forms, ID documents, passports)


## Summary
- Rekognition: face detection, labeling, celebrity recognition
- Transcribe: audio to text (ex: subtitles)
- Polly: text to audio
- Translate: translations
- Lex: build conversational bots - chatbots
- Connect: cloud contact center
- Comprehend: natural language processing
- SageMaker: machine learning for every developer

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1747980599556817093)
