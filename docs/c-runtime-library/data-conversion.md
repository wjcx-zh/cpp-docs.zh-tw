---
title: "資料轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.conversions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "轉換資料"
  - "資料轉換常式 [C++]"
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 資料轉換
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些常式將資料轉換至另一個表單。  通常這些常式比您撰寫的轉換還快。  `to` 前置詞開頭的每個常式會實作為函式和當做巨集。  如需選擇實作的詳細資訊，請參閱 [選取函式和巨集之間](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) 。  
  
### 資料轉換常式  
  
|常式|使用|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|尋找整數絕對值|[\<caps:sentence id\="tgt11" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將字串轉換至`float`|[\<caps:sentence id\="tgt13" sentenceid\="363f8f2cb09f8ca850491a65df66522e" class\="tgtSentence"\>System::Convert::ToDouble\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[atoi、\_atoi\_l、\_wtoi、\_wtoi\_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|將字串轉換至`int`|[System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)， [System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)|  
|[\_atoi64、\_atoi64\_l、\_wtoi64、\_wtoi64\_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|將字串轉換至`__int64`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)， [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)|  
|[atol、\_atol\_l、\_wtol、\_wtol\_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|將字串轉換至`long`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)， [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)|  
|[\_ecvt](../c-runtime-library/reference/ecvt.md), [\_ecvt\_s](../c-runtime-library/reference/ecvt-s.md)|將 `double` 轉換為指定長度的字串|[\<caps:sentence id\="tgt22" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_fcvt](../c-runtime-library/reference/fcvt.md), [\_fcvt\_s](../c-runtime-library/reference/fcvt-s.md)|將 `double` 轉換成以特定小數點後的數量。|[\<caps:sentence id\="tgt25" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_gcvt](../c-runtime-library/reference/gcvt.md), [\_gcvt\_s](../c-runtime-library/reference/gcvt-s.md)|將 `double` 數字轉換成字串；將字串儲存於緩衝區|[\<caps:sentence id\="tgt28" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md), [\_itoa\_s、\_i64toa\_s、\_ui64toa\_s、\_itow\_s、\_i64tow\_s、\_ui64tow\_s](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|將`int` 或 `__int64`轉換成字串。|[\<caps:sentence id\="tgt31" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[labs](../misc/labs-llabs.md)|尋找長整數\(`long`integer\)的絕對值|[\<caps:sentence id\="tgt34" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[\_ltoa、\_ltow](../c-runtime-library/reference/ltoa-ltow.md), [\_ltoa\_s、\_ltow\_s](../c-runtime-library/reference/ltoa-s-ltow-s.md)|將`long`轉換成字串|[\<caps:sentence id\="tgt37" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_mbbtombc、\_mbbtombc\_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|將 1 位元多位元組字元轉換為對應的 2 位元多位元組字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbcjistojms、\_mbcjistojms\_l、\_mbcjmstojis、\_mbcjmstojis\_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|將日本業界標準 \(JIS\) 的字元轉換至 Microsoft 日文 \(JMS\) 字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbcjistojms、\_mbcjistojms\_l、\_mbcjmstojis、\_mbcjmstojis\_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|將 JMS 字元轉換為 JIS 字元。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbctohira、\_mbctohira\_l、\_mbctokata、\_mbctokata\_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|轉換多位元組字元為 1 位元組平假名程式碼|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbctohira、\_mbctohira\_l、\_mbctokata、\_mbctokata\_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|轉換多位元組字元為 1 位元組片假名程式碼|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbctombb、\_mbctombb\_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|將 2 位元多位元組字元轉換為對應的 1 位元多位元組字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[mbstowcs、\_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs\_s、\_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|轉換多位元組字元序列至對應的寬字元序列|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[mbtowc、\_mbtowc\_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|轉換多位元組字元至對應的寬字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[strtod、\_strtod\_l、wcstod、\_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|將字串轉換至`double`|[\<caps:sentence id\="tgt72" sentenceid\="363f8f2cb09f8ca850491a65df66522e" class\="tgtSentence"\>System::Convert::ToDouble\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[strtol、wcstol、\_strtol\_l、\_wcstol\_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|將字串轉換長整數\(`long` integer\)|[\<caps:sentence id\="tgt74" sentenceid\="e227c715eb07e76d963577b7a799c2bb" class\="tgtSentence"\>System::Convert::ToInt32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)|  
|[strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|將字串轉換成`unsigned long` integer|[\<caps:sentence id\="tgt76" sentenceid\="121858e0b5a36f51abe1c266ab6fba6a" class\="tgtSentence"\>System::Convert::ToUInt32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)|  
|[strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|將字串轉換成以地區特定資訊設定的自動分頁表單|[\<caps:sentence id\="tgt78" sentenceid\="f57d3343223d1337ec503c6d3e02bac0" class\="tgtSentence"\>System::IFormattable::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.iformattable.tostring.aspx)|  
|[toascii \_\_toascii](../c-runtime-library/reference/toascii-toascii.md)|將字元轉換成 ASCII 程式碼||  
|[tolower、\_tolower、towlower、\_tolower\_l、\_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|測試字元，若目前為大寫則轉換為小寫|[\<caps:sentence id\="tgt82" sentenceid\="531bb90548dfdc9e9adea31b19ef1cc1" class\="tgtSentence"\>System::Char::ToLower\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.tolower.aspx)|  
|[tolower、\_tolower、towlower、\_tolower\_l、\_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|將字元無條件地轉換為小寫|[\<caps:sentence id\="tgt84" sentenceid\="067c0d5e10b0facda111402483f5cd3a" class\="tgtSentence"\>System::String::ToLower\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|  
|[toupper、\_toupper、towupper、\_toupper\_l、\_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|測試字元，若目前為小寫則轉換為大寫|[\<caps:sentence id\="tgt87" sentenceid\="fb184167443ee6ce1ae71a9ab9b01edb" class\="tgtSentence"\>System::Char::ToUpper\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.toupper.aspx)|  
|[toupper、\_toupper、towupper、\_toupper\_l、\_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|將字元無條件地轉換為大寫|[\<caps:sentence id\="tgt89" sentenceid\="86a1b4a5abf74ef908414687bc4c78df" class\="tgtSentence"\>System::String::ToUpper\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)|  
|[\_ultoa、\_ultow](../c-runtime-library/reference/ultoa-ultow.md), [\_ultoa\_s、\_ultow\_s](../c-runtime-library/reference/ultoa-s-ultow-s.md)|將 `unsigned` `long`轉換至字串|[\<caps:sentence id\="tgt92" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[wcstombs、\_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|轉換寬字元序列至對應的多位元組字元序列|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[wctomb、\_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb\_s、\_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|轉換寬字元至對應的多位元組字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|轉換寬字元字串為 `double`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)， [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)， [System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)， [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[atoi、\_atoi\_l、\_wtoi、\_wtoi\_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|轉換寬字元字串為 `int`|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_atoi64、\_atoi64\_l、\_wtoi64、\_wtoi64\_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|轉換寬字元字串為 `__int64`|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[atol、\_atol\_l、\_wtol、\_wtol\_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|轉換寬字元字串為 `long`|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)