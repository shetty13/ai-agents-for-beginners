# AI Ajanları için Bellek
[![Agent Memory](../../../translated_images/tr/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

AI Ajanları oluşturmanın benzersiz faydalarından bahsedilirken iki şey genellikle tartışılır: görevleri tamamlamak için araçları çağırabilme yeteneği ve zaman içinde gelişme yeteneği. Bellek, kullanıcılarımıza daha iyi deneyimler yaratabilen, kendini geliştiren ajanlar oluşturmanın temelidir.

Bu derste, AI Ajanları için belleğin ne olduğunu, nasıl yönetileceğini ve uygulamalarımızın yararına nasıl kullanılacağını inceleyeceğiz.

## Giriş

Bu ders şunları kapsayacak:

• **AI Ajan Belleğini Anlama**: Belleğin ne olduğu ve ajanlar için neden önemli olduğu.

• **Belleği Uygulama ve Depolama**: AI ajanlarınıza bellek yetenekleri eklemek için pratik yöntemler, kısa süreli ve uzun süreli belleğe odaklanarak.

• **AI Ajanlarını Kendini Geliştiren Hale Getirme**: Belleğin ajanların geçmiş etkileşimlerden öğrenmesini ve zamanla gelişmesini nasıl sağladığı.

## Mevcut Uygulamalar

Bu derste iki kapsamlı not defteri öğreticisi bulunmaktadır:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Mem0 ve Azure AI Search kullanarak Semantic Kernel çerçevesi ile bellek uygulaması

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Gömülü destekli bilgi grafiği otomatik olarak oluşturan, grafiği görselleştiren ve akıllı arama yapabilen Cognee kullanarak yapılandırılmış bellek uygulaması

## Öğrenme Hedefleri

Bu dersi tamamladıktan sonra şunları bileceksiniz:

• **Çalışma, kısa süreli ve uzun süreli bellek gibi AI ajan belleğinin farklı türleri arasında ayrım yapabilmek** ve ayrıca persona ve epizodik bellek gibi özel türleri de tanımak.

• **Semantic Kernel çerçevesi kullanarak kısa süreli ve uzun süreli belleği AI ajanları için uygulamak ve yönetmek**, Mem0, Cognee, Whiteboard memory gibi araçlardan yararlanmak ve Azure AI Search ile entegrasyon yapmak.

• **Kendini geliştiren AI ajanların arkasındaki prensipleri anlamak** ve sağlam bellek yönetim sistemlerinin sürekli öğrenme ve uyum sağlamaya nasıl katkıda bulunduğunu kavramak.

## AI Ajan Belleğini Anlamak

Temelde, **AI ajanları için bellek, onların bilgiyi tutmasını ve hatırlamasını sağlayan mekanizmalardır**. Bu bilgi, bir konuşmaya ait belirli detaylar, kullanıcı tercihleri, geçmiş eylemler veya öğrenilmiş desenler olabilir.

Bellek olmadan, AI uygulamaları genellikle durumsuzdur; yani her etkileşim sıfırdan başlar. Bu, ajanların önceki bağlamı veya tercihleri "unutması" nedeniyle tekrar eden ve sinir bozucu bir kullanıcı deneyimine yol açar.

### Neden Bellek Önemlidir?

Bir ajanın zekası, geçmiş bilgiyi hatırlama ve kullanma yeteneğiyle derinden bağlıdır. Bellek ajanların:

• **Yansıtıcı** olmasını sağlar: Geçmiş eylemlerden ve sonuçlardan öğrenmek.

• **Etkileşimli** olmasını sağlar: Süregelen bir konuşma boyunca bağlamı korumak.

• **Proaktif ve Tepkisel** olmasını sağlar: Historik verilere dayanarak ihtiyaçları ön görmek veya uygun şekilde yanıt vermek.

• **Otonom** olmasını sağlar: Depolanan bilgileri kullanarak daha bağımsız çalışmak.

Belleği uygulamanın amacı, ajanları daha **güvenilir ve yetkin** hale getirmektir.

### Bellek Türleri

#### Çalışma Belleği

Bunu, bir ajanın tek bir devam eden görev veya düşünce sürecinde kullandığı bir karalama kağıdı olarak düşünebilirsiniz. Bir sonraki adımı hesaplamak için gereken anlık bilgileri tutar.

AI ajanları için çalışma belleği, genellikle bir konuşmadan en alakalı bilgileri yakalar; sohbet geçmişi uzun veya kesilmiş olsa bile. Gereksinimler, öneriler, kararlar ve eylemler gibi önemli unsurları çıkarmaya odaklanır.

**Çalışma Belleği Örneği**

Bir seyahat rezervasyon ajanında, çalışma belleği kullanıcının şu anki isteğini yakalayabilir; örneğin "Paris'e bir seyahat rezervasyonu yapmak istiyorum". Bu özel gereksinim, mevcut etkileşimi yönlendirmek için ajanın anlık bağlamında tutulur.

#### Kısa Süreli Bellek

Bu bellek türü, bir konuşma veya oturum boyunca bilgiyi tutar. Bu, mevcut sohbetin bağlamıdır ve ajanın önceki diyalog adımlarına geri başvurmasını sağlar.

**Kısa Süreli Bellek Örneği**

Bir kullanıcı "Paris'e bir uçak bileti ne kadar tutar?" diye sorar ve ardından "Peki ya oradaki konaklama?" diye devam ederse, kısa süreli bellek ajanın "orası"nın aynı konuşmada "Paris"e referans verdiğini anlamasını sağlar.

#### Uzun Süreli Bellek

Bu bilgi, birden fazla konuşma veya oturum boyunca kalıcıdır. Ajanların kullanıcı tercihlerine, geçmiş etkileşimlere veya genel bilgiye uzun süreli erişimini sağlar. Bu, kişiselleştirme için önemlidir.

**Uzun Süreli Bellek Örneği**

Uzun süreli bellek, "Ben kayak ve açık hava aktivitelerini seviyor, dağ manzaralı kahve tercih ediyor ve geçmişte yaşadığı bir sakatlanma nedeniyle zor kayak pistlerinden kaçınmak istiyor" bilgisini saklayabilir. Önceki etkileşimlerden öğrenilen bu bilgi, gelecekteki seyahat planlama oturumlarında önerileri son derece kişiselleştirir.

#### Persona Belleği

Bu özel bellek türü, bir ajanın tutarlı bir "kişilik" veya "kimlik" geliştirmesine yardımcı olur. Ajanın kendisi veya amaçlanan rolü hakkında detayları hatırlamasını sağlayarak etkileşimleri daha akıcı ve odaklı hale getirir.

**Persona Belleği Örneği**

Eğer seyahat ajanı "uzman kayak planlayıcısı" olarak tasarlanmışsa, persona belleği bu rolü pekiştirir ve yanıtların uzman bir ton ve bilgiyle uyumlu olmasını sağlar.

#### İş Akışı/Epizodik Bellek

Bu bellek, bir ajanın karmaşık bir görev sırasında yaptığı adım dizisini, başarıları ve başarısızlıkları ile birlikte saklar. Belli "epizodları" ya da geçmiş deneyimleri hatırlayarak onlardan öğrenmek gibidir.

**Epizodik Bellek Örneği**

Eğer ajan belirli bir uçuşu rezerve etmeyi denedi ama mevcudiyetsizlik nedeniyle başarısız olduysa, epizodik bellek bu hatayı kaydedebilir. Böylece ajan sonraki denemede alternatif uçuşları deneyebilir veya kullanıcıyı daha bilgili biçimde bilgilendirebilir.

#### Varlık Belleği

Bu, kişiler, yerler veya nesneler gibi belirli varlıkların ve olayların konuşmalardan çıkarılması ve hatırlanmasını içerir. Ajanın tartışılan ana unsurlar hakkında yapılandırılmış bir anlayış oluşturmasını sağlar.

**Varlık Belleği Örneği**

Geçmiş bir seyahatle ilgili konuşmadan ajan "Paris", "Eyfel Kulesi" ve "Le Chat Noir restoranında akşam yemeği" gibi varlıkları çıkarabilir. Gelecekteki bir etkileşimde, "Le Chat Noir"u hatırlayarak orada yeni bir rezervasyon yapmayı teklif edebilir.

#### Yapılandırılmış RAG (Retrieval Augmented Generation)

RAG daha geniş bir tekniktir, ancak "Yapılandırılmış RAG" güçlü bir bellek teknolojisi olarak vurgulanır. Konuşmalar, e-postalar ve görüntüler gibi çeşitli kaynaklardan yoğun, yapılandırılmış bilgiyi çıkarır ve yanıtların doğruluğunu, geri çağırma ve hızını artırmak için kullanır. Klasik RAG gibi yalnızca anlamsal benzerliğe dayanmak yerine, Yapılandırılmış RAG bilgi yapısının doğasıyla çalışır.

**Yapılandırılmış RAG Örneği**

Anahtar kelimeleri eşleştirmek yerine, Yapılandırılmış RAG bir e-postadan uçuş detayları (varış yeri, tarih, saat, havayolu) çıkarıp bunları yapılandırılmış biçimde depolayabilir. Bu sayede "Salı günü Paris'e hangi uçuşu rezerve ettim?" gibi kesin sorgular yapılabilir.

## Belleği Uygulama ve Depolama

AI ajanları için bellek uygulamak, bilgi oluşturma, depolama, geri çağırma, entegre etme, güncelleme ve hatta "unutma" (silme) süreçlerini içeren sistematik bir **bellek yönetimi** sürecidir. Geri çağırma özellikle kritik bir konudur.

### Özel Bellek Araçları

#### Mem0

Ajans belleğini saklamak ve yönetmek için özel araçlardan biri Mem0'dır. Mem0, ajanın alakalı etkileşimleri hatırlamasını, kullanıcı tercihleri ve gerçek içerikli bağlamı depolamasını ve zaman içinde başarılar ile başarısızlıklardan öğrenmesini sağlayan kalıcı bir bellek katmanı olarak çalışır. Buradaki fikir, durumsuz ajanların durumsallara dönüşmesidir.

İki aşamalı bir bellek hattı çalışması vardır: çıkarım ve güncelleme. Önce, ajanın ileti dizisine eklenen mesajlar Mem0 servisine gönderilir; burada Büyük Dil Modeli (LLM) kullanılarak konuşma geçmişi özetlenir ve yeni anılar çıkarılır. Sonrasında, LLM destekli bir güncelleme aşaması, bu anıların eklenip eklenmemesi, değiştirilmesi veya silinmesine karar verir ve bunları vektör, grafik ve anahtar-değer veritabanlarını içerebilen karma bir veri deposunda saklar. Bu sistem ayrıca çeşitli bellek türlerini destekler ve varlıklar arasındaki ilişkileri yönetmek için grafik belleğini de içerebilir.

#### Cognee

Bir diğer güçlü yaklaşım ise, yapısal ve yapılandırılmamış verileri sorgulanabilir gömülü destekli bilgi grafiklerine dönüştüren açık kaynak semantic bellek olan **Cognee** kullanımıdır. Cognee, vektör benzerlik araması ile grafik ilişkilerini birleştiren **çift-katmanlı mimari** sağlar; bu sayede ajanlar sadece hangi bilginin benzer olduğunu değil, kavramların birbirleriyle nasıl ilişkili olduğunu da anlayabilir.

Cognee, ham küme aramadan grafik farkındalıklı soru-cevaplamaya kadar vektör benzerliği, grafik yapısı ve LLM muhakemesini harmanlayan **hibrit geri çağırmayı** mükemmel yapar. Sistem, kısa süreli oturum bağlamı ve uzun süreli kalıcı belleği destekleyerek, sorgulanabilir tek bağlantılı bir grafik olarak evrilen **canlı belleği** korur.

Cognee not defteri öğreticisi ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) bu birleşik bellek katmanının inşasını; çeşitli veri kaynaklarının alınması, bilgi grafiğinin görselleştirilmesi ve farklı arama stratejileriyle sorgulama örnekleriyle pratik olarak gösterir.

### Belleği RAG ile Depolama

Mem0 gibi özel bellek araçlarının ötesinde, **Azure AI Search gibi sağlam arama servislerini belleklerin saklanması ve geri çağrılması için altyapı olarak kullanabilirsiniz**, özellikle yapılandırılmış RAG için.

Bu, ajanınızın yanıtlarını kendi verilerinizle temel almasını sağlar ve daha alakalı, doğru cevaplar verir. Azure AI Search, kullanıcıya özgü seyahat anılarını, ürün kataloglarını veya başka herhangi bir alan bilgilerini depolamak için kullanılabilir.

Azure AI Search, büyük veri kümelerinden (konuşma geçmişleri, e-postalar veya hatta görüntüler) yoğun, yapılandırılmış bilgiyi çıkarmada ve geri çağırmada üstün olan **Yapılandırılmış RAG** özelliklerini destekler. Bu, geleneksel metin parçalaması ve gömme yöntemlerine kıyasla "insanüstü hassasiyet ve geri çağırma" sağlar.

## AI Ajanlarını Kendini Geliştiren Hale Getirmek

Kendini geliştiren ajanlar için yaygın bir model, bir **"bilgi ajanı"** tanımlamaktır. Bu ayrı ajan, kullanıcı ile ana ajan arasındaki ana konuşmayı gözlemler. Rolü:

1. **Değerli bilgiyi belirlemek**: Konuşmanın herhangi bir kısmının genel bilgi veya özel kullanıcı tercihi olarak saklanmaya değer olup olmadığını belirlemek.

2. **Çıkarmak ve özetlemek**: Konuşmadan önemli öğrenmeyi veya tercihi özümsemek.

3. **Bilgi tabanına kaydetmek**: Bu çıkarılan bilgiyi genellikle vektör veritabanında tutmak, böylece sonra geri çağrılabilir hale getirmek.

4. **Gelecek sorguları desteklemek**: Kullanıcı yeni bir sorgu başlattığında, bilgi ajanı ilgili saklanan bilgiyi geri çağırarak kullanıcının uyarısına ekler ve ana ajan için kritik bağlam sağlar (RAG benzeri).

### Bellek için Optimizasyonlar

• **Gecikme Yönetimi**: Kullanıcı etkileşimlerini yavaşlatmamak için, önce bilgi depolamaya ya da çağırmaya değip değmeyeceğini hızlıca kontrol eden daha ucuz ve hızlı bir model kullanılır; sadece gerekli olduğunda daha karmaşık çıkarım/geri çağırma süreci başlatılır.

• **Bilgi Tabanı Bakımı**: Büyüyen bir bilgi tabanı için daha az kullanılan bilgiler "soğuk depolamaya" taşınarak maliyetler yönetilir.

## Ajan Belleği Hakkında Daha Fazla Sorunuz Mu Var?

Diğer öğrenenlerle tanışmak, çalışma saatlerine katılmak ve AI Ajanları ile ilgili sorularınıza yanıt almak için [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord)’a katılın.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Feragatname**:  
Bu belge, AI çeviri servisi [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba gösterilse de, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayın. Orijinal belge, kendi dilindeki kaynak olarak esas alınmalıdır. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımı sonucu ortaya çıkabilecek herhangi bir yanlış anlama veya yanlış yorumdan sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->