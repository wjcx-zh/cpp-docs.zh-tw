---
title: "字元分類 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types.character"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字元分類常式"
  - "字元, 測試"
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 字元分類
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些常式中測試每一個符合條件指定的單一位元組字元、字元或多位元組字元。\(根據定義，0 到 127 的 ASCII 字元集是所有多位元組字元集的子集。  例如，日文片假名包括 ASCII 以及非 ASCII 字元\)。  
  
 測試條件會受到地區設定的 `LC_CTYPE` 類別設定影響。如需詳細資訊，請參閱 [設定區域設定](../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  
  
 通常這些常式執行會比您可以撰寫趨勢的測試快速。  例如，下列程式碼來執行慢至呼叫 `isalpha(c)`:  
  
```  
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))  
    return TRUE;  
```  
  
### 字元分類常式  
  
|常式|字元測試條件|.NET Framework 對等用法|  
|--------|------------|-------------------------|  
|[isalnum、iswalnum、\_isalnum\_l、\_iswalnum\_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|英數字元。|[System::Char::IsLetterOrDigit](https://msdn.microsoft.com/en-us/library/system.char.isletterordigit.aspx)|  
|[\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|英數字元。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[isalpha、iswalpha、\_isalpha\_l、\_iswalpha\_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md), [\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|字母順序|[\<caps:sentence id\="tgt20" sentenceid\="7985fd1b5b2aeb907c06a172679a27b2" class\="tgtSentence"\>System::Char::IsLetter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)|  
|[isascii \_\_isascii、 iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|[\<caps:sentence id\="tgt22" sentenceid\="7985fd1b5b2aeb907c06a172679a27b2" class\="tgtSentence"\>System::Char::IsLetter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)|  
|[isblank、iswblank、\_isblank\_l、\_iswblank\_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)， [\_ismbcsblank， \_ismbcsblank\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白 \(空格或水平索引標籤\)|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[iscntrl、iswcntrl、\_iscntrl\_l、\_iswcntrl\_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|控制項|[\<caps:sentence id\="tgt29" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[iscsym、 iscsymf、 \_\_iscsym、 \_\_iswcsym、 \_\_iscsymf、 \_\_iswcsymf、 \_iscsym\_l、 \_iswcsym\_l、 \_iscsymf\_l、 \_iswcsymf\_l](../c-runtime-library/reference/iscsym-functions.md)|字母、底線或數字。|[\<caps:sentence id\="tgt31" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[iscsym、 iscsymf、 \_\_iscsym、 \_\_iswcsym、 \_\_iscsymf、 \_\_iswcsymf、 \_iscsym\_l、 \_iswcsym\_l、 \_iscsymf\_l、 \_iswcsymf\_l](../c-runtime-library/reference/iscsym-functions.md)|字母或底線|[\<caps:sentence id\="tgt33" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[isdigit、iswdigit、\_isdigit\_l、\_iswdigit\_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|十進位數字|[\<caps:sentence id\="tgt36" sentenceid\="20b77d76c6cf167a186925e085420e65" class\="tgtSentence"\>System::Char::IsDigit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)|  
|[isgraph、iswgraph、\_isgraph\_l、\_iswgraph\_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md), [\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可列印空白之外|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[islower、iswlower、\_islower\_l、\_iswlower\_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [\_ismbclower、\_ismbclower\_l、\_ismbcupper、\_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小寫|[\<caps:sentence id\="tgt44" sentenceid\="5e79724bd080c040f5d77abaa610244d" class\="tgtSentence"\>System::Char::IsLower\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.islower.aspx)|  
|[\_ismbchira、\_ismbchira\_l、\_ismbckata、\_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|平假名|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbchira、\_ismbchira\_l、\_ismbckata、\_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|片假名|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbclegal、\_ismbclegal\_l、\_ismbcsymbol、\_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|合法多位元組字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbcl0、\_ismbcl0\_l、\_ismbcl1、\_ismbcl1\_l、\_ismbcl2、\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本層級 0 多位元組字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbcl0、\_ismbcl0\_l、\_ismbcl1、\_ismbcl1\_l、\_ismbcl2、\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本層級 1 多位元組字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbcl0、\_ismbcl0\_l、\_ismbcl1、\_ismbcl1\_l、\_ismbcl2、\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本層級 2 多位元組字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbclegal、\_ismbclegal\_l、\_ismbcsymbol、\_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|非英數多位元組字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[isprint、iswprint、\_isprint\_l、\_iswprint\_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md), [\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可列印的|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ispunct、iswpunct、\_ispunct\_l、\_iswpunct\_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|標點符號|[\<caps:sentence id\="tgt80" sentenceid\="d38bbde5482b110a63876458567db603" class\="tgtSentence"\>System::Char::IsPunctuation\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)|  
|[isspace、iswspace、\_isspace\_l、\_iswspace\_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白字元|[\<caps:sentence id\="tgt83" sentenceid\="acbb8b5269b25caa0be79d70895dc079" class\="tgtSentence"\>System::Char::IsWhiteSpace\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)|  
|[Isupper, swupper](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)， [\_ismbclower、\_ismbclower\_l、\_ismbcupper、\_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大寫|[\<caps:sentence id\="tgt86" sentenceid\="7f17c3dfa91d5cdf120546eae2131f1f" class\="tgtSentence"\>System::Char::IsUpper\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isupper.aspx)|  
|[\_isctype、iswctype、\_isctype\_l、\_iswctype\_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|`desc` 引數指定的屬性。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[isxdigit、iswxdigit、\_isxdigit\_l、\_iswxdigit\_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|十六進位數字|[\<caps:sentence id\="tgt92" sentenceid\="ce7b0e5c510cf706d10a80a8594068ce" class\="tgtSentence"\>System::Char::IsNumber\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isnumber.aspx)|  
|[\_mbclen、mblen、\_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|傳回有效多位元組字元的長度：結果取決於 `LC_CTYPE` 目前地區設定分類設定|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)