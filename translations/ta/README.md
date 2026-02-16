# தொடக்கத்தக்கோர் AI முகவரிகள் - ஒரு படிப்பு

![தொடக்கத்தக்கோருக்கான உருவாக்கும் AI](../../translated_images/ta/repo-thumbnailv2.06f4a48036fde647.webp)

## AI முகவரிகள் உருவாக்க தொடங்குவதற்கு நீங்கள் அறிந்துகொள்ள வேண்டிய அனைத்தையும் படிக்கும் ஒரு பாடநெறி

[![GitHub உரிமம்](https://img.shields.io/github/license/microsoft/ai-agents-for-beginners.svg)](https://github.com/microsoft/ai-agents-for-beginners/blob/master/LICENSE?WT.mc_id=academic-105485-koreyst)
[![GitHub பங்களிப்பாளர்கள்](https://img.shields.io/github/contributors/microsoft/ai-agents-for-beginners.svg)](https://GitHub.com/microsoft/ai-agents-for-beginners/graphs/contributors/?WT.mc_id=academic-105485-koreyst)
[![GitHub பிரச்சனைகள்](https://img.shields.io/github/issues/microsoft/ai-agents-for-beginners.svg)](https://GitHub.com/microsoft/ai-agents-for-beginners/issues/?WT.mc_id=academic-105485-koreyst)
[![GitHub வழக்கான-கோரிக்கைகள்](https://img.shields.io/github/issues-pr/microsoft/ai-agents-for-beginners.svg)](https://GitHub.com/microsoft/ai-agents-for-beginners/pulls/?WT.mc_id=academic-105485-koreyst)
[![PRs வரவேற்கப்படுகிறது](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com?WT.mc_id=academic-105485-koreyst)

### 🌐 பல்மொழி ஆதரவு

#### GitHub Action மூலம் ஆதரிக்கப்படுகிறது (தானாகவும் எப்போதும் புதுப்பிக்கப்படುವುದು)

<!-- CO-OP TRANSLATOR LANGUAGES TABLE START -->
[அரபி](../ar/README.md) | [பெங்காலி](../bn/README.md) | [பல்கேரியன்](../bg/README.md) | [பர்மீஸ் (மியான்மர்)](../my/README.md) | [சீன (எளிமையான)](../zh-CN/README.md) | [சீன (பண்பாட்டுச் செம்மையான, ஹாங்காங்)](../zh-HK/README.md) | [சீன (பண்பாட்டுச் செம்மையான, மேகாஓ)](../zh-MO/README.md) | [சீன (பண்பாட்டுச் செம்மையான, தைவான்)](../zh-TW/README.md) | [குரோஷியன்](../hr/README.md) | [செக்](../cs/README.md) | [டானிஷ்](../da/README.md) | [டச்சு](../nl/README.md) | [எஸ்டோனியன்](../et/README.md) | [பின்னிஷ்](../fi/README.md) | [பிரஞ்சு](../fr/README.md) | [ஜெர்மன்](../de/README.md) | [கிரேக்கம்](../el/README.md) | [ஹீப்ரூ](../he/README.md) | [ஹிந்தி](../hi/README.md) | [ஹுங்கேரியன்](../hu/README.md) | [இந்தோனீசியன்](../id/README.md) | [இத்தாலியன்](../it/README.md) | [ஜப்பானீஸ்](../ja/README.md) | [கன்னடம்](../kn/README.md) | [கோரியன்](../ko/README.md) | [லிதுவேனியன்](../lt/README.md) | [மலாய்](../ms/README.md) | [மலையாளம்](../ml/README.md) | [மராத்தி](../mr/README.md) | [நெபாளி](../ne/README.md) | [நைஜீரிய பிஜின்](../pcm/README.md) | [நார்வேஜியன்](../no/README.md) | [பெர்ஷியன் (பார்சி)](../fa/README.md) | [போலிஷ்](../pl/README.md) | [போர்த்துகீசு (பிரேசில்)](../pt-BR/README.md) | [போர்த்துகீசு (போர்ச்சுகல்)](../pt-PT/README.md) | [பஞ்சாபி (குருமுகி)](../pa/README.md) | [ரோமானியன்](../ro/README.md) | [ரஷ்யன்](../ru/README.md) | [செர்பியன் (சிரிலிக்)](../sr/README.md) | [சிலோவாக்](../sk/README.md) | [ஸ்லோவேனியன்](../sl/README.md) | [ஸ்பானிஷ்](../es/README.md) | [ஸ்வாஹிலி](../sw/README.md) | [ஸ்வீடிஷ்](../sv/README.md) | [டகலாக் (பிலிபினோ)](../tl/README.md) | [தமிழ்](./README.md) | [தெலுங்கு](../te/README.md) | [தாய்](../th/README.md) | [துருக்கியன்](../tr/README.md) | [உக்ரைனியன்](../uk/README.md) | [உருது](../ur/README.md) | [வியேட்நாமீஸ்](../vi/README.md)

> **உள்ளூரில் கிளோன் செய்ய விரும்புகிறீர்களா?**
>
> இந்தக் கண்காப்பு 50+ மொழி மொழிபெயர்ப்புகளை உட்படுத்துகிறது, இது பதிவிறக்கக் காப்பை பெரிதும் அதிகரிக்கிறது. மொழிபெயர்ப்புகளின்றி கிளோன் செய்ய, ஸ்பார்ஸ் செக்க்அவுட்டை பயன்படுத்தவும்:
>
> **Bash / macOS / Linux:**
> ```bash
> git clone --filter=blob:none --sparse https://github.com/microsoft/ai-agents-for-beginners.git
> cd ai-agents-for-beginners
> git sparse-checkout set --no-cone '/*' '!translations' '!translated_images'
> ```
>
> **CMD (Windows):**
> ```cmd
> git clone --filter=blob:none --sparse https://github.com/microsoft/ai-agents-for-beginners.git
> cd ai-agents-for-beginners
> git sparse-checkout set --no-cone "/*" "!translations" "!translated_images"
> ```
>
> இது படிப்பை முடிக்க தேவையான அனைத்தையும் விரைவான பதிவிறக்கத்துடன் உங்களுக்கு தருகிறது.
<!-- CO-OP TRANSLATOR LANGUAGES TABLE END -->

**மேலும் மொழி மொழிபெயர்ப்புகளுக்கு ஆதரவளிக்க விரும்பினால், அவை இங்கே பட்டியலிடப்பட்டுள்ளன [இங்கே](https://github.com/Azure/co-op-translator/blob/main/getting_started/supported-languages.md)**

[![GitHub பார்வையாளர்](https://img.shields.io/github/watchers/microsoft/ai-agents-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/ai-agents-for-beginners/watchers/?WT.mc_id=academic-105485-koreyst)
[![GitHub கிளோன்ஸ்](https://img.shields.io/github/forks/microsoft/ai-agents-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/ai-agents-for-beginners/network/?WT.mc_id=academic-105485-koreyst)
[![GitHub நட்சத்திரங்கள்](https://img.shields.io/github/stars/microsoft/ai-agents-for-beginners.svg?style=social&label=Star)](https://GitHub.com/microsoft/ai-agents-for-beginners/stargazers/?WT.mc_id=academic-105485-koreyst)

[![Microsoft Foundry Discord](https://dcbadge.limes.pink/api/server/nTYy5BXMWG)](https://discord.gg/nTYy5BXMWG)


## 🌱 ஆரம்பிப்பது எப்படி

இந்தப் பாடநெறியில் AI முகவரிகளை உருவாக்குவதற்கான அடிப்படைகளை உள்ளடக்கிய பாடப்பாடங்கள் உள்ளன. ஒவ்வொரு பாடப்பாடமும் அதன் சொந்த தலைப்பை உள்ளடக்கியது, எனவே நீங்கள் விரும்பிய இடத்திலிருந்து தொடங்குங்கள்!

இந்தப் பாடநெறிக்கு பல்மொழி ஆதரவு உள்ளது. எங்களுடைய [கிடைக்கும் மொழிகள் இங்கே](../..) என செல்லவும்.

உங்கள் முதற்படி உருவாக்கம் உருவாக்கும் AI மாதிரிகளுடனானது என்றால், எங்கள் [தொடக்கத்தக்கோர் உருவாக்கும் AI](https://aka.ms/genai-beginners) பாடநெறியை பார்த்து செல்லவும், இதுவொன்று GenAI உடன் உருவாக்க 21 பாடங்களை உள்ளடக்கியது.

இந்தக் கோப்பிடையை [நட்சத்திரமிட (🌟)](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) மற்றும் [fork செய்ய](https://github.com/microsoft/ai-agents-for-beginners/fork) மறவாதீர்கள், அதன் மூலம் கோ드를 இயக்கலாம்.

### பிற கற்றுக்கொள்ளுநர்களை சந்திக்கவும், உங்கள் கேள்விகளுக்கு பதில்கள் பெறவும்

நீங்கள் அடிதடு அடைந்தால் அல்லது AI முகவரிகளை உருவாக்குவதற்கு ஏதேனும் கேள்விகள் இருந்தால், எங்கள் [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) இல் உள்ள விசேட Discord சேனலில் சேருங்கள்.

### என்ன தேவையாகும்

இந்தப் பாடநெறியில் உள்ள ஒவ்வொரு பாடப்பாடமும் குறியீடு உதாரணங்களை கொண்டுள்ளது, அவைகள் code_samples என்ற கோப்புறையில் கிடைக்கின்றன. உங்கள் சொந்த நகலை உருவாக்க நீங்கள் [இந்தக் கோப்பிடையை fork செய்யலாம்](https://github.com/microsoft/ai-agents-for-beginners/fork).

இந்த பயிற்சிகளிலுள்ள குறியீடு உதாரணங்கள், Azure AI Foundry மற்றும் GitHub மாதிரி பட்டியலைப் பயன்படுத்தி மொழி மாதிரிகளுடன் தொடர்பு கொள்ளுகின்றன:

- [GitHub மாதிரிகள்](https://aka.ms/ai-agents-beginners/github-models) - இலவசம் / வரையறுக்கப்பட்டவை
- [Azure AI Foundry](https://aka.ms/ai-agents-beginners/ai-foundry) - Azure கணக்கு தேவை

இந்தப் பாடநெறி மேலும் Microsoft-இனுடைய பின்வரும் AI முகவர் கட்டமைப்புகள் மற்றும் சேவைகளையும் பயன்படுத்துகின்றது:

- [Microsoft முகவர் கட்டமைப்பு (MAF) - புதியது!](https://aka.ms/ai-agents-beginners/agent-framewrok)
- [Azure AI முகவர் சேவை](https://aka.ms/ai-agents-beginners/ai-agent-service)
- [Semantic Kernel](https://aka.ms/ai-agents-beginners/semantic-kernel)
- [AutoGen](https://aka.ms/ai-agents/autogen)


இந்தக் கோடு இயக்குவதற்கான மேலதிக தகவலுக்கு, [Course Setup](./00-course-setup/README.md) பார்க்கவும்.

## 🙏 உதவ விரும்புகிறீர்களா?

உங்களிடம் பரிந்துரைகள் உள்ளதா அல்லது எழுத்துப்பிழைகள் அல்லது குறியீட்டு பிழைகள் கண்டுபிடிக்கப்பட்டுள்ளதா? [ஒரு பிரச்சனையை எழுதியிடவும்](https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst) அல்லது [ஒரு புல் கோரிக்கையை உருவாக்கவும்](https://github.com/microsoft/ai-agents-for-beginners/pulls?WT.mc_id=academic-105485-koreyst)



## 📂 ஒவ்வொரு பாடப்பாடமும் கொண்டிருப்பவை

- README-ல் உள்ள எழுத்துப்பாடமும் ஒரு குறுகிய வீடியோவும்
- Azure AI Foundry மற்றும் Github மாதிரிகளை (இலவசம்) ஆதரிக்கும் Python குறியீடு உதாரணங்கள்
- உங்கள் கற்றலை தொடர செல்லக்கூடிய கூடுதல் வளங்களுக்கான இணைப்புகள்


## 🗃️ பாடங்கள்

| **பாடம்**                                  | **உரை & குறியீடு**                                 | **வீடியோ**                                                 | **கூடுதல் கற்றல்**                                                                        |
|-------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| AI முகவரிகளுக்கும் முகவர் பயன்களுக்கும் அறிமுகம்   | [இணைப்பு](./01-intro-to-ai-agents/README.md)             | [வீடியோ](https://youtu.be/3zgm60bXmQk?si=z8QygFvYQv-9WtO1)   | [இணைப்பு](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| AI முகவர் கட்டமைப்புகளை ஆராய்வு                 | [இணைப்பு](./02-explore-agentic-frameworks/README.md)       | [வீடியோ](https://youtu.be/ODwF-EZo_O8?si=Vawth4hzVaHv-u0H)   | [இணைப்பு](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| AI முகவர் வடிவமைப்பு மாதிரிகள் புரிதல்             | [இணைப்பு](./03-agentic-design-patterns/README.md)          | [வீடியோ](https://youtu.be/m9lM8qqoOEA?si=BIzHwzstTPL8o9GF)   | [இணைப்பு](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| கருவி பயன்பாட்டுக் கட்டமைப்பு மாதிரி              | [இணைப்பு](./04-tool-use/README.md)                       | [வீடியோ](https://youtu.be/vieRiPRx-gI?si=2z6O2Xu2cu_Jz46N)   | [இணைப்பு](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| முகவர் RAG                                  | [இணைப்பு](./05-agentic-rag/README.md)                     | [வீடியோ](https://youtu.be/WcjAARvdL7I?si=gKPWsQpKiIlDH9A3)   | [இணைப்பு](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| நம்பகமான AI முகவரிகள் உருவாக்குதல்             | [இணைப்பு](./06-building-trustworthy-agents/README.md)       | [வீடியோ](https://youtu.be/iZKkMEGBCUQ?si=jZjpiMnGFOE9L8OK )  | [இணைப்பு](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| திட்டமிடல் கட்டமைப்பு மாதிரி                      | [இணைப்பு](./07-planning-design/README.md)                 | [வீடியோ](https://youtu.be/kPfJ2BrBCMY?si=6SC_iv_E5-mzucnC)   | [இணைப்பு](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| பல முகவர் கட்டமைப்பு மாதிரி                     | [இணைப்பு](./08-multi-agent/README.md)                   | [வீடியோ](https://youtu.be/V6HpE9hZEx0?si=rMgDhEu7wXo2uo6g)   | [இணைப்பு](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| மெட்டாகாக்னிஷன் வடிவமைப்பு வரைபடம்                 | [Link](./09-metacognition/README.md)               | [Video](https://youtu.be/His9R6gw6Ec?si=8gck6vvdSNCt6OcF)  | [Link](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| உற்பத்தியில் AI முகவர்கள்                      | [Link](./10-ai-agents-production/README.md)        | [Video](https://youtu.be/l4TP6IyJxmQ?si=31dnhexRo6yLRJDl)  | [Link](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| முகவரிக்கை நியமங்களைப் பயன்படுத்து (MCP, A2A மற்றும் NLWeb) | [Link](./11-agentic-protocols/README.md)           | [Video](https://youtu.be/X-Dh9R3Opn8)                                 | [Link](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| AI முகவர்களுக்கு சூழல் பொறியியல்            | [Link](./12-context-engineering/README.md)         | [Video](https://youtu.be/F5zqRV7gEag)                                 | [Link](https://aka.ms/ai-agents-beginners/collection?WT.mc_id=academic-105485-koreyst) |
| முகவரிக்கை நினைவகத்தை நிர்வகித்தல்                      | [Link](./13-agent-memory/README.md)     |      [Video](https://youtu.be/QrYbHesIxpw?si=vZkVwKrQ4ieCcIPx)                                                      |                                                                                        |
| Microsoft முகவர் கட்டமைப்பை ஆராய்தல்                         | [Link](./14-microsoft-agent-framework/README.md)                            |                                                            |                                                                                        |
| கணினி பயன்பாட்டு முகவர்களை உருவாக்குதல் (CUA)           | விரைவில் வருகிறது                            |                                                            |                                                                                        |
| பரவலான முகவர்களை இயக்குதல்                    | விரைவில் வருகிறது                            |                                                            |                                                                                        |
| உள்ளூர் AI முகவர்களை உருவாக்குதல்                     | விரைவில் வருகிறது                               |                                                            |                                                                                        |
| AI முகவர்களை பாதுகாப்பாற்றுதல்                           | விரைவில் வருகிறது                               |                                                            |                                                                                        |

## 🎒 பிற படிப்புகள்

எங்கள் குழு பிற படிப்புகளை தயாரிக்கிறது! பாருங்கள்:

<!-- CO-OP TRANSLATOR OTHER COURSES START -->
### LangChain
[![LangChain4j for Beginners](https://img.shields.io/badge/LangChain4j%20for%20Beginners-22C55E?style=for-the-badge&&labelColor=E5E7EB&color=0553D6)](https://aka.ms/langchain4j-for-beginners)
[![LangChain.js for Beginners](https://img.shields.io/badge/LangChain.js%20for%20Beginners-22C55E?style=for-the-badge&labelColor=E5E7EB&color=0553D6)](https://aka.ms/langchainjs-for-beginners?WT.mc_id=m365-94501-dwahlin)
[![LangChain for Beginners](https://img.shields.io/badge/LangChain%20for%20Beginners-22C55E?style=for-the-badge&labelColor=E5E7EB&color=0553D6)](https://github.com/microsoft/langchain-for-beginners?WT.mc_id=m365-94501-dwahlin)
---

### Azure / Edge / MCP / முகவர்கள்
[![AZD for Beginners](https://img.shields.io/badge/AZD%20for%20Beginners-0078D4?style=for-the-badge&labelColor=E5E7EB&color=0078D4)](https://github.com/microsoft/AZD-for-beginners?WT.mc_id=academic-105485-koreyst)
[![Edge AI for Beginners](https://img.shields.io/badge/Edge%20AI%20for%20Beginners-00B8E4?style=for-the-badge&labelColor=E5E7EB&color=00B8E4)](https://github.com/microsoft/edgeai-for-beginners?WT.mc_id=academic-105485-koreyst)
[![MCP for Beginners](https://img.shields.io/badge/MCP%20for%20Beginners-009688?style=for-the-badge&labelColor=E5E7EB&color=009688)](https://github.com/microsoft/mcp-for-beginners?WT.mc_id=academic-105485-koreyst)
[![AI Agents for Beginners](https://img.shields.io/badge/AI%20Agents%20for%20Beginners-00C49A?style=for-the-badge&labelColor=E5E7EB&color=00C49A)](https://github.com/microsoft/ai-agents-for-beginners?WT.mc_id=academic-105485-koreyst)

---
 
### உருவாக்கும் AI தொடர்
[![Generative AI for Beginners](https://img.shields.io/badge/Generative%20AI%20for%20Beginners-8B5CF6?style=for-the-badge&labelColor=E5E7EB&color=8B5CF6)](https://github.com/microsoft/generative-ai-for-beginners?WT.mc_id=academic-105485-koreyst)
[![Generative AI (.NET)](https://img.shields.io/badge/Generative%20AI%20(.NET)-9333EA?style=for-the-badge&labelColor=E5E7EB&color=9333EA)](https://github.com/microsoft/Generative-AI-for-beginners-dotnet?WT.mc_id=academic-105485-koreyst)
[![Generative AI (Java)](https://img.shields.io/badge/Generative%20AI%20(Java)-C084FC?style=for-the-badge&labelColor=E5E7EB&color=C084FC)](https://github.com/microsoft/generative-ai-for-beginners-java?WT.mc_id=academic-105485-koreyst)
[![Generative AI (JavaScript)](https://img.shields.io/badge/Generative%20AI%20(JavaScript)-E879F9?style=for-the-badge&labelColor=E5E7EB&color=E879F9)](https://github.com/microsoft/generative-ai-with-javascript?WT.mc_id=academic-105485-koreyst)

---
 
### கோர் கற்றல்
[![ML for Beginners](https://img.shields.io/badge/ML%20for%20Beginners-22C55E?style=for-the-badge&labelColor=E5E7EB&color=22C55E)](https://aka.ms/ml-beginners?WT.mc_id=academic-105485-koreyst)
[![Data Science for Beginners](https://img.shields.io/badge/Data%20Science%20for%20Beginners-84CC16?style=for-the-badge&labelColor=E5E7EB&color=84CC16)](https://aka.ms/datascience-beginners?WT.mc_id=academic-105485-koreyst)
[![AI for Beginners](https://img.shields.io/badge/AI%20for%20Beginners-A3E635?style=for-the-badge&labelColor=E5E7EB&color=A3E635)](https://aka.ms/ai-beginners?WT.mc_id=academic-105485-koreyst)
[![Cybersecurity for Beginners](https://img.shields.io/badge/Cybersecurity%20for%20Beginners-F97316?style=for-the-badge&labelColor=E5E7EB&color=F97316)](https://github.com/microsoft/Security-101?WT.mc_id=academic-96948-sayoung)
[![Web Dev for Beginners](https://img.shields.io/badge/Web%20Dev%20for%20Beginners-EC4899?style=for-the-badge&labelColor=E5E7EB&color=EC4899)](https://aka.ms/webdev-beginners?WT.mc_id=academic-105485-koreyst)
[![IoT for Beginners](https://img.shields.io/badge/IoT%20for%20Beginners-14B8A6?style=for-the-badge&labelColor=E5E7EB&color=14B8A6)](https://aka.ms/iot-beginners?WT.mc_id=academic-105485-koreyst)
[![XR Development for Beginners](https://img.shields.io/badge/XR%20Development%20for%20Beginners-38BDF8?style=for-the-badge&labelColor=E5E7EB&color=38BDF8)](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)

---
 
### கோபைலட் தொடர்
[![Copilot for AI Paired Programming](https://img.shields.io/badge/Copilot%20for%20AI%20Paired%20Programming-FACC15?style=for-the-badge&labelColor=E5E7EB&color=FACC15)](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
[![Copilot for C#/.NET](https://img.shields.io/badge/Copilot%20for%20C%23/.NET-FBBF24?style=for-the-badge&labelColor=E5E7EB&color=FBBF24)](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
[![Copilot Adventure](https://img.shields.io/badge/Copilot%20Adventure-FDE68A?style=for-the-badge&labelColor=E5E7EB&color=FDE68A)](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)
<!-- CO-OP TRANSLATOR OTHER COURSES END -->

## 🌟 சமூக நன்றிகள்

Agentic RAG-ஐ காட்டும் முக்கிய குறியீட்டு எடுத்துக்காட்டுகளை வழங்கிய [Shivam Goyal](https://www.linkedin.com/in/shivam2003/) அவர்களுக்கு நன்றி.

## பங்களித்தல்

இந்த திட்டம் பங்களிப்புகளையும் பரிந்துரைகளையும் வரவேற்கிறது. பெரும்பாலான பங்களிப்புகளுக்கு, நீங்கள் பங்களிப்பை பயன்படுத்த அதிகாரம் உண்டு மற்றும் உண்மையில் வழங்குவதாக ஒரு பங்களிப்பாளர் உரிமம் ஒப்பந்தம் (CLA) உடன்பட வேண்டும். விவரங்களுக்கு, <https://cla.opensource.microsoft.com> ஐ பார்வையிடவும்.

நீங்கள் ஒரு புல் வேண்டுகோளை சமர்ப்பிக்கும் போது, CLA போட் தானாகவே நீங்கள் CLA வழங்க வேண்டுமா என்பதை தீர்மானித்து, PR-யைக் (உதா: நிலை சரிபார்ப்பு, கருத்து) சிறப்பிக்கிறது. போட்டினால் வழங்கிய வழிமுறைகளை பின்பற்றுங்கள். அனைத்து கிடப்புகளிலும் ஒருமுறை மட்டுமே இதைப்ப Doing 해야합니다.

இந்தத் திட்டம் [Microsoft திறந்த மூலக் குறியீட்டுத் தொழிலாளர்கள் நெறிமுறையை](https://opensource.microsoft.com/codeofconduct/) கடைபிடிக்கிறது.
கூடுதல் தகவலுக்கு [நெறிமுறை அடிக்கடி கேள்விகள்](https://opensource.microsoft.com/codeofconduct/faq/) ஐ பார்த்து,
அல்லது [opencode@microsoft.com](mailto:opencode@microsoft.com) என்ற முகவரிக்கு எந்தவொரு கேள்விகளும் அல்லது கருத்துகளும் தொடர்பு கொள்ளலாம்.

## வரையறைகள்

இந்தத் திட்டத்தில் திட்டங்கள், பொருட்கள் அல்லது சேவைகளுக்கான வரையறைகள் அல்லது லோகோக்கள் இருக்கலாம். Microsoft வரையறைகள் அல்லது லோகோக்களை பயன்படுத்த அதிகாரம் பெறுவது [Microsoft வரையறைகள் & பிராண்ட் வழிகாட்டுதல்களை](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general) கடைப்பிடிக்க வேண்டும்.
இந்த திட்டத்தை மாற்றிய பதிப்புகளில் Microsoft வரையறைகள் அல்லது லோகோக்களை பயன்படுத்துவது குழப்பத்தை ஏற்படுத்தக்கூடாது அல்லது Microsoft ஆதரவாக கருதப்படக் கூடாது.
மூன்றாம் தரப்பாருடைய வரையறைகள் அல்லது லோகோக்களை பயன்படுத்துவது அந்த மூன்றாம் தரப்பாருடைய கொள்கைகளுக்குள் இருக்கும்.

## உதவி பெறுதல்

உங்களுக்கு பிரச்சினை ஏற்பட்டால் அல்லது AI செயலிகள் உருவாக்குவதில் எந்தவொரு கேள்விகளும் இருந்தால், சேரவும்:

[![Microsoft Foundry Discord](https://dcbadge.limes.pink/api/server/nTYy5BXMWG)](https://discord.gg/nTYy5BXMWG)

உங்களுக்கு தயாரிப்பு கருத்துகள் அல்லது பிழைகள் இருந்தால், பராமரிக்கவும்:

[![Microsoft Foundry Developer Forum](https://img.shields.io/badge/GitHub-Microsoft_Foundry_Developer_Forum-blue?style=for-the-badge&logo=github&color=000000&logoColor=fff)](https://aka.ms/foundry/forum)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**பிரதிபாதிப்பு**:  
இந்த ஆவணம் AI மொழிபெயர்ப்பு சேவை [Co-op Translator](https://github.com/Azure/co-op-translator) மூலம் மொழிபெயர்க்கப்பட்டுள்ளது. நாங்கள் துல்லியத்தை உறுதிப்படுத்த முயற்சித்தாலும், தானியங்கி மொழிபெயர்ப்புகளில் பிழைகள் அல்லது தவறுகள் இருக்க வாய்ப்பு உண்டு என்பதை தயவுசெய்து கவனத்தில் கொள்ளவும். முதன்மை ஆவணம் அதன் சொந்த மொழியில் இருப்பது அதிகாரபூர்வமான மூலமாகக் கருதப்பட வேண்டும். முக்கிய தகவல்களுக்கு, தொழில்முறை மனித மொழிபெயர்ப்பை பயன்படுத்த பரிந்துரை செய்யப்படுகிறது. இந்த மொழிபெயர்ப்பைப் பயன்படுதுவதால் ஏற்படும் தவறானப் புரிதல்கள் அல்லது பொருள் பிழைகளுக்கு நாங்கள் பொறுப்பில் இல்லை.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->