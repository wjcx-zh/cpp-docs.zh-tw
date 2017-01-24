---
title: "多位元組字元序列的解譯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.character.multibyte"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "MBCS [C++], 地區設定字碼頁"
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多位元組字元序列的解譯
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大部分 Microsoft 執行階段程式庫中的多位元組字元常式辨識與多位元組字碼頁相關聯的多位元組字元序列。  輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  
  
### 與地區設定相關的多位元組常式  
  
|常式|用法|  
|--------|--------|  
|[\_mbclen、mblen、\_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|驗證並傳回以多位元表示的位元組數目|  
|[strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|對於多位元組字元字串:驗證字串中的每個字元;傳回字串的長度。  對於寬字串:傳回字串的長度。|  
|[mbstowcs、\_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs\_s、\_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|轉換多位元組字元序列至對應的寬字元序列|  
|[mbtowc、\_mbtowc\_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|轉換多位元組字元至對應的寬字元|  
|[wcstombs、\_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|轉換寬字元序列至對應的多位元組字元序列|  
|[wctomb、\_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb\_s、\_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|轉換寬字元至對應的多位元組字元|  
  
## 請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)