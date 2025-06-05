[ข้ามไปที่เนื้อหาหลัก](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [Deutsch](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/grounding?lang=python&hl=ko)

[ลงชื่อเข้าใช้](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Fgrounding%3Fhl%3Dth%26lang%3Dpython&prompt=select_account)

- ในหน้านี้
- [กำหนดค่าการกําหนดค่าการค้นหา](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#configure-search)
- [การแนะนำของ Google Search](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#search-suggestions)
- [การดึงข้อมูลของ Google Search](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#google-search-retrieval)
  - [เริ่มต้นใช้งาน](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#getting-started)
  - [เกณฑ์แบบไดนามิก](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#dynamic-threshold)
  - [การดึงข้อมูลแบบไดนามิก](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#dynamic-retrieval)
- [การตอบกลับที่อิงตามข้อมูล](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#grounded-response)


ขอแนะนำ Gemini 2.5 Flash, Veo 2 และการอัปเดต Live API [ดูข้อมูลเพิ่มเติม](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

![](https://ai.google.dev/_static/images/translated.svg?hl=th)

หน้านี้ได้รับการแปลโดย [Cloud Translation API](https://cloud.google.com/translate/?hl=th)

- [หน้าแรก](https://ai.google.dev/?hl=th)
- [Gemini API](https://ai.google.dev/gemini-api?hl=th)
- [โมเดล](https://ai.google.dev/gemini-api/docs?hl=th)

ข้อมูลนี้มีประโยชน์ไหม



 ส่งความคิดเห็น



# พื้นฐานด้วย Google Search

- ในหน้านี้
- [กำหนดค่าการกําหนดค่าการค้นหา](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#configure-search)
- [การแนะนำของ Google Search](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#search-suggestions)
- [การดึงข้อมูลของ Google Search](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#google-search-retrieval)
  - [เริ่มต้นใช้งาน](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#getting-started)
  - [เกณฑ์แบบไดนามิก](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#dynamic-threshold)
  - [การดึงข้อมูลแบบไดนามิก](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#dynamic-retrieval)
- [การตอบกลับที่อิงตามข้อมูล](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#grounded-response)

PythonJavaScriptREST

คุณสามารถใช้ฟีเจอร์การหาข้อมูลพื้นฐานด้วย Google Search ใน Gemini API และ AI Studio เพื่อปรับปรุงความแม่นยำและความใหม่ของคำตอบจากโมเดล นอกเหนือจากคำตอบที่เป็นข้อเท็จจริงมากขึ้นแล้ว เมื่อเปิดใช้การอ้างอิงกับ Google Search แล้ว Gemini API จะแสดงแหล่งที่มาของการอ้างอิง (ลิงก์สนับสนุนในบทสนทนา) และ [คำแนะนำของ Google Search](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#search-suggestions) พร้อมกับเนื้อหาคำตอบ คำแนะนำการค้นหาจะนําผู้ใช้ไปยังผลการค้นหาที่เกี่ยวข้องกับคําตอบที่อิงตามข้อมูล

คู่มือนี้จะช่วยคุณเริ่มต้นใช้งาน Grounding ด้วย Google Search

### ก่อนเริ่มต้น

ก่อนเรียกใช้ Gemini API โปรดตรวจสอบว่าคุณได้ติดตั้ง [SDK ที่ต้องการ](https://ai.google.dev/gemini-api/docs/downloads?hl=th) รวมถึงกําหนดค่า [คีย์ API ของ Gemini](https://ai.google.dev/gemini-api/docs/api-key?hl=th) ให้พร้อมใช้งานแล้ว

## กำหนดค่าการกําหนดค่าการค้นหา

ตั้งแต่ Gemini 2.0 เป็นต้นไป Google Search จะพร้อมใช้งานเป็นเครื่องมือ ซึ่งหมายความว่ารูปแบบจะตัดสินใจได้ว่าจะเลือกใช้ Google Search เมื่อใด ตัวอย่างต่อไปนี้แสดงวิธีกำหนดค่า Search เป็นเครื่องมือ

```
from google import genai
from google.genai.types import Tool, GenerateContentConfig, GoogleSearch

client = genai.Client()
model_id = "gemini-2.0-flash"

google_search_tool = Tool(
    google_search = GoogleSearch()
)

response = client.models.generate_content(
    model=model_id,
    contents="When is the next total solar eclipse in the United States?",
    config=GenerateContentConfig(
        tools=[google_search_tool],
        response_modalities=["TEXT"],
    )
)

for each in response.candidates[0].content.parts:
    print(each.text)
# Example response:
# The next total solar eclipse visible in the contiguous United States will be on ...

# To get grounding metadata as web content.
print(response.candidates[0].grounding_metadata.search_entry_point.rendered_content)

```

ฟังก์ชันการค้นหาเป็นเครื่องมือยังเปิดใช้การค้นหาแบบหลายรอบด้วย ระบบยังไม่รองรับการรวมการค้นหากับการเรียกใช้ฟังก์ชัน

เครื่องมือค้นหาช่วยให้ใช้พรอมต์และเวิร์กโฟลว์ที่ซับซ้อนซึ่งต้องมีการวางแผน เหตุผล และการคิดได้

- การอ้างอิงเพื่อเพิ่มความเป็นข้อเท็จจริงและความใหม่และให้คำตอบที่แม่นยำยิ่งขึ้น
- ดึงข้อมูลรายการต่างๆ จากเว็บเพื่อวิเคราะห์เพิ่มเติม
- ค้นหารูปภาพ วิดีโอ หรือสื่ออื่นๆ ที่เกี่ยวข้องเพื่อช่วยในการอนุมานหรือสร้างงานแบบมัลติโมเดล
- การเขียนโค้ด การแก้ปัญหาทางเทคนิค และงานอื่นๆ ที่มีความเชี่ยวชาญ
- การค้นหาข้อมูลเฉพาะภูมิภาคหรือช่วยแปลเนื้อหาให้ถูกต้อง
- การค้นหาเว็บไซต์ที่เกี่ยวข้องเพื่อเรียกดูเพิ่มเติม

การยึดเหนี่ยวกับ Google Search ใช้ได้กับ [ภาษาทั้งหมดที่พร้อมใช้งาน](https://ai.google.dev/gemini-api/docs/models/gemini?hl=th#available-languages) เมื่อใช้พรอมต์ข้อความ ในแพ็กเกจแบบชำระเงินของ Gemini Developer API คุณจะได้รับการค้นหาเพื่อหาข้อมูลพื้นฐานจาก Google Search ได้ 1,500 รายการต่อวันโดยไม่มีค่าใช้จ่าย โดยจะมีการเรียกเก็บเงินสำหรับการค้นหาเพิ่มเติมในราคามาตรฐาน $35 ต่อ 1,000 รายการ

ดูข้อมูลเพิ่มเติมได้โดย [ลองใช้โน้ตบุ๊กเครื่องมือค้นหา](https://colab.research.google.com/github/google-gemini/cookbook/blob/main/quickstarts/Search_Grounding.ipynb?hl=th)

## การแนะนำของ Google Search

หากต้องการใช้การอ้างอิงกับ Google Search คุณต้องแสดงคำแนะนำของ Google Search ซึ่งเป็นคำค้นหาที่แนะนำซึ่งรวมอยู่ในข้อมูลเมตาของคำตอบที่มีการอ้างอิง ดูข้อมูลเพิ่มเติมเกี่ยวกับข้อกำหนดในการแสดงได้ที่หัวข้อ [ใช้การแนะนำของ Google Search](https://ai.google.dev/gemini-api/docs/grounding/search-suggestions?hl=th)

## การดึงข้อมูลของ Google Search

หากต้องการกําหนดค่าโมเดลให้ใช้การดึงข้อมูลของ Google Search ให้ส่งเครื่องมือที่เหมาะสม

โปรดทราบว่าการดึงข้อมูล Google Search ใช้ได้กับรุ่น 1.5 เท่านั้น รุ่นที่ใหม่กว่าต้องใช้ [Search Grounding](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#grounding) หากคุณพยายามใช้ SDK จะแปลงโค้ดของคุณให้ใช้การกําหนดค่าพื้นฐานของ Search แทน และจะละเว้นการตั้งค่าเกณฑ์แบบไดนามิก

### เริ่มต้นใช้งาน

```
from google import genai
from google.genai import types

client = genai.Client(api_key="GEMINI_API_KEY")

response = client.models.generate_content(
    model='gemini-1.5-flash',
    contents="Who won the US open this year?",
    config=types.GenerateContentConfig(
        tools=[types.Tool(\
            google_search_retrieval=types.GoogleSearchRetrieval()\
        )]
    )
)
print(response)

```

### เกณฑ์แบบไดนามิก

การตั้งค่า `dynamic_threshold` ช่วยให้คุณควบคุม [ลักษณะการดึงข้อมูล](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#dynamic-retrieval) ได้ ซึ่งจะช่วยให้คุณควบคุมเพิ่มเติมได้ว่าจะใช้การเชื่อมโยงกับ Google Search เมื่อใด

```
from google import genai
from google.genai import types

client = genai.Client(api_key="GEMINI_API_KEY")

response = client.models.generate_content(
    model='gemini-1.5-flash',
    contents="Who won Roland Garros this year?",
    config=types.GenerateContentConfig(
        tools=[types.Tool(\
            google_search_retrieval=types.GoogleSearchRetrieval(\
                dynamic_retrieval_config=types.DynamicRetrievalConfig(\
                    mode=types.DynamicRetrievalConfigMode.MODE_DYNAMIC,\
                    dynamic_threshold=0.6))\
        )]
    )
)
print(response)

```

### การดึงข้อมูลแบบไดนามิก

คำค้นหาบางรายการมีแนวโน้มที่จะได้ประโยชน์จาก "พื้นฐานจาก Google Search" มากกว่าคำค้นหาอื่นๆ ฟีเจอร์ _การดึงข้อมูลแบบไดนามิก_ ช่วยให้คุณควบคุมเพิ่มเติมได้ว่าจะใช้การอ้างอิงกับ Google Search เมื่อใด

หากไม่ได้ระบุโหมดการดึงข้อมูลแบบไดนามิก ระบบจะเรียกใช้การกําหนดค่าพื้นฐานด้วย Google Search เสมอ หากตั้งค่าโหมดเป็นแบบไดนามิก โมเดลจะตัดสินใจว่าควรใช้การต่อกราวด์เมื่อใดโดยอิงตามเกณฑ์ที่คุณกำหนดค่าได้ ซึ่งจะเป็นค่าทศนิยมในช่วง \[0,1\] และค่าเริ่มต้นคือ 0.3 หากค่าเกณฑ์เป็น 0 คําตอบจะอิงตาม Google Search เสมอ หากเป็น 1 คําตอบจะไม่อิงตาม Google Search เลย

#### วิธีการทํางานของการดึงข้อมูลแบบไดนามิก

คุณสามารถใช้การดึงข้อมูลแบบไดนามิกในคำขอเพื่อเลือกเวลาเปิดใช้การค้นหาด้วย Google ซึ่งจะมีประโยชน์เมื่อพรอมต์ไม่กำหนดให้คำตอบต้องอิงตาม Google Search และโมเดลสามารถให้คำตอบตามความรู้ของตนเองได้โดยไม่ต้องอิงตามข้อมูล ซึ่งจะช่วยให้คุณจัดการเวลาในการตอบสนอง คุณภาพ และต้นทุนได้อย่างมีประสิทธิภาพมากขึ้น

ก่อนเรียกใช้การกําหนดค่าการดึงข้อมูลแบบไดนามิกในคําขอ โปรดทําความเข้าใจคําศัพท์ต่อไปนี้

- **คะแนนการคาดการณ์**: เมื่อคุณขอคำตอบที่อิงตามข้อมูลจริง Gemini จะกำหนด _คะแนนการคาดการณ์_ ให้กับพรอมต์ คะแนนการคาดการณ์คือค่าทศนิยมในช่วง \[0,1\] มูลค่าของเมตริกนี้ขึ้นอยู่กับว่าพรอมต์จะได้รับประโยชน์จากการอิงคำตอบตามข้อมูลล่าสุดจาก Google Search หรือไม่ ดังนั้น หากพรอมต์ต้องการคำตอบที่อิงตามข้อเท็จจริงล่าสุดบนเว็บ พรอมต์นั้นจะมีคะแนนการคาดคะเนสูงกว่า พรอมต์ที่มีคำตอบที่โมเดลสร้างขึ้นเพียงพอจะมีคะแนนการคาดการณ์ต่ำ

ตัวอย่างพรอมต์และคะแนนการคาดการณ์บางส่วนมีดังนี้




| พรอมต์ | คะแนนการคาดการณ์ | ความคิดเห็น |
| --- | --- | --- |
| "เขียนบทกวีเกี่ยวกับดอกโบตั๋น" | 0.13 | โมเดลใช้ความรู้ของตัวเองได้และคำตอบไม่จำเป็นต้องมีพื้นฐาน |
| "แนะนำของเล่นสำหรับเด็กอายุ 2 ขวบ" | 0.36 | โมเดลใช้ความรู้ของตัวเองได้และคำตอบไม่จำเป็นต้องมีพื้นฐาน |
| "ขอสูตรกัวคาโมเลที่ได้รับแรงบันดาลใจจากเอเชียได้ไหม" | 0.55 | Google Search สามารถให้คำตอบที่อิงตามแหล่งข้อมูล แต่การอ้างอิงแหล่งข้อมูลนั้นไม่จำเป็นอย่างเคร่งครัด ความรู้ของโมเดลก็อาจเพียงพอแล้ว |
| "Agent Builder คืออะไร "การเรียกเก็บเงินสำหรับการอ้างอิงข้อมูลใน Agent Builder เป็นอย่างไร" | 0.72 | กำหนดให้ Google Search สร้างคำตอบที่มีข้อมูลอ้างอิง |
| "ใครชนะการแข่งขัน F1 Grand Prix ครั้งล่าสุด" | 0.97 | กำหนดให้ Google Search สร้างคำตอบที่มีข้อมูลอ้างอิง |

- **เกณฑ์**: ในคําขอ API คุณสามารถระบุการกําหนดค่าการดึงข้อมูลแบบไดนามิกที่มีเกณฑ์ได้ ซึ่งเกณฑ์คือค่าตัวเลขทศนิยมในช่วง \[0,1\] และค่าเริ่มต้นคือ 0.3 หากค่าเกณฑ์เป็น 0 การตอบกลับจะอิงตาม Google Search เสมอ สำหรับค่าอื่นๆ ทั้งหมดของเกณฑ์ จะใช้ค่าต่อไปนี้

  - หากคะแนนการคาดการณ์มากกว่าหรือเท่ากับเกณฑ์ คำตอบจะอิงตาม Google Search
    เกณฑ์ที่ต่ำลงหมายความว่าพรอมต์จำนวนมากขึ้นมีคำตอบที่สร้างขึ้นโดยใช้การอ้างอิงกับ Google Search
  - หากคะแนนการคาดการณ์น้อยกว่าเกณฑ์ โมเดลอาจยังคงสร้างคำตอบ แต่คำตอบนั้นจะไม่อิงตาม Google Search

หากต้องการดูวิธีตั้งค่าเกณฑ์การดึงข้อมูลแบบไดนามิกโดยใช้ SDK หรือ REST API โปรดดู [ตัวอย่างโค้ด](https://ai.google.dev/gemini-api/docs/grounding?hl=th&lang=python#configure-grounding) ที่เหมาะสม

หากต้องการค้นหาเกณฑ์ที่เหมาะสมกับความต้องการทางธุรกิจ คุณสามารถสร้างชุดข้อความค้นหาที่แสดงถึงสิ่งที่คาดว่าจะพบ จากนั้นคุณสามารถจัดเรียงการค้นหาตามคะแนนการคาดการณ์ในการตอบกลับและเลือกเกณฑ์ที่เหมาะสมสําหรับกรณีการใช้งานของคุณ

## การตอบกลับที่อิงตามข้อมูล

หากพรอมต์ของคุณเชื่อมโยงกับ Google Search สำเร็จ คำตอบจะมี `groundingMetadata` คำตอบที่อิงตามหลักฐานอาจมีลักษณะดังนี้ (ตัดการตอบบางส่วนออกเพื่อความกระชับ)

```
{
  "candidates": [\
    {\
      "content": {\
        "parts": [\
          {\
            "text": "Carlos Alcaraz won the Gentlemen's Singles title at the 2024 Wimbledon Championships. He defeated Novak Djokovic in the final, winning his second consecutive Wimbledon title and fourth Grand Slam title overall. \n"\
          }\
        ],\
        "role": "model"\
      },\
      ...\
      "groundingMetadata": {\
        "searchEntryPoint": {\
          "renderedContent": "\u003cstyle\u003e\n.container {\n  align-items: center;\n  border-radius: 8px;\n  display: flex;\n  font-family: Google Sans, Roboto, sans-serif;\n  font-size: 14px;\n  line-height: 20px;\n  padding: 8px 12px;\n}\n.chip {\n  display: inline-block;\n  border: solid 1px;\n  border-radius: 16px;\n  min-width: 14px;\n  padding: 5px 16px;\n  text-align: center;\n  user-select: none;\n  margin: 0 8px;\n  -webkit-tap-highlight-color: transparent;\n}\n.carousel {\n  overflow: auto;\n  scrollbar-width: none;\n  white-space: nowrap;\n  margin-right: -12px;\n}\n.headline {\n  display: flex;\n  margin-right: 4px;\n}\n.gradient-container {\n  position: relative;\n}\n.gradient {\n  position: absolute;\n  transform: translate(3px, -9px);\n  height: 36px;\n  width: 9px;\n}\n@media (prefers-color-scheme: light) {\n  .container {\n    background-color: #fafafa;\n    box-shadow: 0 0 0 1px #0000000f;\n  }\n  .headline-label {\n    color: #1f1f1f;\n  }\n  .chip {\n    background-color: #ffffff;\n    border-color: #d2d2d2;\n    color: #5e5e5e;\n    text-decoration: none;\n  }\n  .chip:hover {\n    background-color: #f2f2f2;\n  }\n  .chip:focus {\n    background-color: #f2f2f2;\n  }\n  .chip:active {\n    background-color: #d8d8d8;\n    border-color: #b6b6b6;\n  }\n  .logo-dark {\n    display: none;\n  }\n  .gradient {\n    background: linear-gradient(90deg, #fafafa 15%, #fafafa00 100%);\n  }\n}\n@media (prefers-color-scheme: dark) {\n  .container {\n    background-color: #1f1f1f;\n    box-shadow: 0 0 0 1px #ffffff26;\n  }\n  .headline-label {\n    color: #fff;\n  }\n  .chip {\n    background-color: #2c2c2c;\n    border-color: #3c4043;\n    color: #fff;\n    text-decoration: none;\n  }\n  .chip:hover {\n    background-color: #353536;\n  }\n  .chip:focus {\n    background-color: #353536;\n  }\n  .chip:active {\n    background-color: #464849;\n    border-color: #53575b;\n  }\n  .logo-light {\n    display: none;\n  }\n  .gradient {\n    background: linear-gradient(90deg, #1f1f1f 15%, #1f1f1f00 100%);\n  }\n}\n\u003c/style\u003e\n\u003cdiv class=\"container\"\u003e\n  \u003cdiv class=\"headline\"\u003e\n    \u003csvg class=\"logo-light\" width=\"18\" height=\"18\" viewBox=\"9 9 35 35\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\"\u003e\n      \u003cpath fill-rule=\"evenodd\" clip-rule=\"evenodd\" d=\"M42.8622 27.0064C42.8622 25.7839 42.7525 24.6084 42.5487 23.4799H26.3109V30.1568H35.5897C35.1821 32.3041 33.9596 34.1222 32.1258 35.3448V39.6864H37.7213C40.9814 36.677 42.8622 32.2571 42.8622 27.0064V27.0064Z\" fill=\"#4285F4\"/\u003e\n      \u003cpath fill-rule=\"evenodd\" clip-rule=\"evenodd\" d=\"M26.3109 43.8555C30.9659 43.8555 34.8687 42.3195 37.7213 39.6863L32.1258 35.3447C30.5898 36.3792 28.6306 37.0061 26.3109 37.0061C21.8282 37.0061 18.0195 33.9811 16.6559 29.906H10.9194V34.3573C13.7563 39.9841 19.5712 43.8555 26.3109 43.8555V43.8555Z\" fill=\"#34A853\"/\u003e\n      \u003cpath fill-rule=\"evenodd\" clip-rule=\"evenodd\" d=\"M16.6559 29.8904C16.3111 28.8559 16.1074 27.7588 16.1074 26.6146C16.1074 25.4704 16.3111 24.3733 16.6559 23.3388V18.8875H10.9194C9.74388 21.2072 9.06992 23.8247 9.06992 26.6146C9.06992 29.4045 9.74388 32.022 10.9194 34.3417L15.3864 30.8621L16.6559 29.8904V29.8904Z\" fill=\"#FBBC05\"/\u003e\n      \u003cpath fill-rule=\"evenodd\" clip-rule=\"evenodd\" d=\"M26.3109 16.2386C28.85 16.2386 31.107 17.1164 32.9095 18.8091L37.8466 13.8719C34.853 11.082 30.9659 9.3736 26.3109 9.3736C19.5712 9.3736 13.7563 13.245 10.9194 18.8875L16.6559 23.3388C18.0195 19.2636 21.8282 16.2386 26.3109 16.2386V16.2386Z\" fill=\"#EA4335\"/\u003e\n    \u003c/svg\u003e\n    \u003csvg class=\"logo-dark\" width=\"18\" height=\"18\" viewBox=\"0 0 48 48\" xmlns=\"http://www.w3.org/2000/svg\"\u003e\n      \u003ccircle cx=\"24\" cy=\"23\" fill=\"#FFF\" r=\"22\"/\u003e\n      \u003cpath d=\"M33.76 34.26c2.75-2.56 4.49-6.37 4.49-11.26 0-.89-.08-1.84-.29-3H24.01v5.99h8.03c-.4 2.02-1.5 3.56-3.07 4.56v.75l3.91 2.97h.88z\" fill=\"#4285F4\"/\u003e\n      \u003cpath d=\"M15.58 25.77A8.845 8.845 0 0 0 24 31.86c1.92 0 3.62-.46 4.97-1.31l4.79 3.71C31.14 36.7 27.65 38 24 38c-5.93 0-11.01-3.4-13.45-8.36l.17-1.01 4.06-2.85h.8z\" fill=\"#34A853\"/\u003e\n      \u003cpath d=\"M15.59 20.21a8.864 8.864 0 0 0 0 5.58l-5.03 3.86c-.98-2-1.53-4.25-1.53-6.64 0-2.39.55-4.64 1.53-6.64l1-.22 3.81 2.98.22 1.08z\" fill=\"#FBBC05\"/\u003e\n      \u003cpath d=\"M24 14.14c2.11 0 4.02.75 5.52 1.98l4.36-4.36C31.22 9.43 27.81 8 24 8c-5.93 0-11.01 3.4-13.45 8.36l5.03 3.85A8.86 8.86 0 0 1 24 14.14z\" fill=\"#EA4335\"/\u003e\n    \u003c/svg\u003e\n    \u003cdiv class=\"gradient-container\"\u003e\u003cdiv class=\"gradient\"\u003e\u003c/div\u003e\u003c/div\u003e\n  \u003c/div\u003e\n  \u003cdiv class=\"carousel\"\u003e\n    \u003ca class=\"chip\" href=\"https://vertexaisearch.cloud.google.com/grounding-api-redirect/AWhgh4x8Epe-gzpwRBvp7o3RZh2m1ygq1EHktn0OWCtvTXjad4bb1zSuqfJd6OEuZZ9_SXZ_P2SvCpJM7NaFfQfiZs6064MeqXego0vSbV9LlAZoxTdbxWK1hFeqTG6kA13YJf7Fbu1SqBYM0cFM4zo0G_sD9NKYWcOCQMvDLDEJFhjrC9DM_QobBIAMq-gWN95G5tvt6_z6EuPN8QY=\"\u003ewho won wimbledon 2024\u003c/a\u003e\n  \u003c/div\u003e\n\u003c/div\u003e\n"\
        },\
        "groundingChunks": [\
          {\
            "web": {\
              "uri": "https://vertexaisearch.cloud.google.com/grounding-api-redirect/AWhgh4whET1ta3sDETZvcicd8FeNe4z0VuduVsxrT677KQRp2rYghXI0VpfYbIMVI3THcTuMwggRCbFXS_wVvW0UmGzMe9h2fyrkvsnQPJyikJasNIbjJLPX0StM4Bd694-ZVle56MmRA4YiUvwSqad1w6O2opmWnw==",\
              "title": "wikipedia.org"\
            }\
          },\
          {\
            "web": {\
              "uri": "https://vertexaisearch.cloud.google.com/grounding-api-redirect/AWhgh4wR1M-9-yMPUr_KdHlnoAmQ8ZX90DtQ_vDYTjtP2oR5RH4tRP04uqKPLmesvo64BBkPeYLC2EpVDxv9ngO3S1fs2xh-e78fY4m0GAtgNlahUkm_tBm_sih5kFPc7ill9u2uwesNGUkwrQlmP2mfWNU5lMMr23HGktr6t0sV0QYlzQq7odVoBxYWlQ_sqWFH",\
              "title": "wikipedia.org"\
            }\
          },\
          {\
            "web": {\
              "uri": "https://vertexaisearch.cloud.google.com/grounding-api-redirect/AWhgh4wsDmROzbP-tmt8GdwCW_pqISTZ4IRbBuoaMyaHfcQg8WW-yKRQQvMDTPAuLxJh-8_U8_iw_6JKFbQ8M9oVYtaFdWFK4gOtL4RrC9Jyqc5BNpuxp6uLEKgL5-9TggtNvO97PyCfziDFXPsxylwI1HcfQdrz3Jy7ZdOL4XM-S5rC0lF2S3VWW0IEAEtS7WX861meBYVjIuuF_mIr3spYPqWLhbAY2Spj-4_ba8DjRvmevIFUhRuESTKvBfmpxNSM",\
              "title": "cbssports.com"\
            }\
          },\
          {\
            "web": {\
              "uri": "https://vertexaisearch.cloud.google.com/grounding-api-redirect/AWhgh4yzjLkorHiUKjhOPkWaZ9b4cO-cLG-02vlEl6xTBjMUjyhK04qSIclAa7heR41JQ6AAVXmNdS3WDrLOV4Wli-iezyzW8QPQ4vgnmO_egdsuxhcGk3-Fp8-yfqNLvgXFwY5mPo6QRhvplOFv0_x9mAcka18QuAXtj0SPvJfZhUEgYLCtCrucDS5XFc5HmRBcG1tqFdKSE1ihnp8KLdaWMhrUQI21hHS9",\
              "title": "jagranjosh.com"\
            }\
          },\
          {\
            "web": {\
              "uri": "https://vertexaisearch.cloud.google.com/grounding-api-redirect/AWhgh4y9L4oeNGWCatFz63b9PpP3ys-Wi_zwnkUT5ji9lY7gPUJQcsmmE87q88GSdZqzcx5nZG9usot5FYk2yK-FAGvCRE6JsUQJB_W11_kJU2HVV1BTPiZ4SAgm8XDFIxpCZXnXmEx5HUfRqQm_zav7CvS2qjA2x3__qLME6Jy7R5oza1C5_aqjQu422le9CaigThS5bvJoMo-ZGcXdBUCj2CqoXNVjMA==",\
              "title": "apnews.com"\
            }\
          }\
        ],\
        "groundingSupports": [\
          {\
            "segment": {\
              "endIndex": 85,\
              "text": "Carlos Alcaraz won the Gentlemen's Singles title at the 2024 Wimbledon Championships."\
            },\
            "groundingChunkIndices": [\
              0,\
              1,\
              2,\
              3\
            ],\
            "confidenceScores": [\
              0.97380733,\
              0.97380733,\
              0.97380733,\
              0.97380733\
            ]\
          },\
          {\
            "segment": {\
              "startIndex": 86,\
              "endIndex": 210,\
              "text": "He defeated Novak Djokovic in the final, winning his second consecutive Wimbledon title and fourth Grand Slam title overall."\
            },\
            "groundingChunkIndices": [\
              1,\
              0,\
              4\
            ],\
            "confidenceScores": [\
              0.96145374,\
              0.96145374,\
              0.96145374\
            ]\
          }\
        ],\
        "webSearchQueries": [\
          "who won wimbledon 2024"\
        ]\
      }\
    }\
  ],
  ...
}

```

หากการตอบกลับไม่มี `groundingMetadata` แสดงว่าระบบไม่สามารถกําหนดแหล่งที่มาของการตอบกลับได้สําเร็จ ปัญหานี้อาจเกิดขึ้นได้จากหลายสาเหตุ เช่น ความเกี่ยวข้องของแหล่งที่มาต่ำหรือข้อมูลไม่สมบูรณ์ภายในคําตอบของโมเดล

เมื่อสร้างผลการค้นหาที่อิงตามสถานที่แล้ว ข้อมูลเมตาจะมี URI ที่เปลี่ยนเส้นทางไปยังผู้เผยแพร่เนื้อหาที่ใช้ในการสร้างผลการค้นหาที่อิงตามสถานที่
URI เหล่านี้มีโดเมนย่อย `vertexaisearch` ดังตัวอย่างที่ตัดให้สั้นลงนี้
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/...` ข้อมูลเมตายังมีโดเมนของผู้เผยแพร่โฆษณาด้วย URI ที่ระบุจะเข้าถึงได้เป็นเวลา 30 วันหลังจากสร้างผลการค้นหาที่อิงตามสถานที่

ช่อง `renderedContent` ภายใน `searchEntryPoint` คือรหัสที่ระบุไว้สําหรับการใช้การแนะนําการค้นหาของ Google ดูข้อมูลเพิ่มเติมที่หัวข้อ [ใช้การแนะนำของ Google Search](https://ai.google.dev/gemini-api/docs/grounding/search-suggestions?hl=th)

ข้อมูลนี้มีประโยชน์ไหม



 ส่งความคิดเห็น



เนื้อหาของหน้าเว็บนี้ได้รับอนุญาตภายใต้ [ใบอนุญาตที่ต้องระบุที่มาของครีเอทีฟคอมมอนส์ 4.0](https://creativecommons.org/licenses/by/4.0/) และตัวอย่างโค้ดได้รับอนุญาตภายใต้ [ใบอนุญาต Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) เว้นแต่จะระบุไว้เป็นอย่างอื่น โปรดดูรายละเอียดที่ [นโยบายเว็บไซต์ Google Developers](https://developers.google.com/site-policies?hl=th) Java เป็นเครื่องหมายการค้าจดทะเบียนของ Oracle และ/หรือบริษัทในเครือ

อัปเดตล่าสุด 2025-04-28 UTC

โหลดหน้าเว็บใหม่แล้ว