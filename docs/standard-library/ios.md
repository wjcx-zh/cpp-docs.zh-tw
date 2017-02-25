---
title: "&lt;ios&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<ios>"
  - "std::<ios>"
  - "<ios>"
  - "ios/std::<ios>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ios 標頭"
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;ios&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義 iostreams 作業的數個基本類型和函式。  此標頭通常會由其他 iostream 標頭為您納入；您很少會直接將其納入。  
  
## 語法  
  
```  
  
#include <ios>  
  
```  
  
## 備註  
 操作工具由一個大型函式群組所組成。  宣告於 \<ios\> 中的操作工具，會改變其儲存在 [ios\_base](../standard-library/ios-base-class.md) 之引數物件中的值。  其他操作工具會對由此類別衍生之類型的物件所控制的資料流執行動作，例如其中一個範本類別 [basic\_istream](../standard-library/basic-istream-class.md) 或 [basic\_ostream](../standard-library/basic-ostream-class.md) 的特製化。  例如，[noskipws](../Topic/noskipws.md)\(**str**\) 會清除物件 **str** 中的格式旗標 `ios_base::skipws`，它可能是其中一個類型。  
  
 基於針對衍生自 `ios_base` 的類別提供的特殊插入和擷取作業，您也可以將操作工具插入輸出資料流中，或從輸入資料流中加以擷取，以呼叫操作工具。  例如:  
  
```  
istr >> noskipws;  
```  
  
 呼叫 [noskipws](../Topic/noskipws.md)\(**istr**\)。  
  
### Typedefs  
  
|||  
|-|-|  
|[ios](../Topic/ios.md)|支援來自舊 iostream 程式庫的 ios 類別。|  
|[streamoff](../Topic/streamoff.md)|支援內部作業。|  
|[streampos](../Topic/streampos.md)|保留緩衝區指標或檔案指標的目前位置。|  
|[streamsize](../Topic/streamsize.md)|指定資料流的大小。|  
|[wios](../Topic/wios.md)|支援來自舊 iostream 程式庫的 wios 類別。|  
|[wstreampos](../Topic/wstreampos.md)|保留緩衝區指標或檔案指標的目前位置。|  
  
### 操作工具  
  
|||  
|-|-|  
|[boolalpha](../Topic/boolalpha.md)|指定類型 [bool](../cpp/bool-cpp.md) 的變數在資料流中會顯示為 **true** 或 **false**。|  
|[dec](../Topic/dec.md)|指定整數變數會以基底 10 標記法顯示。|  
|[defaultfloat](../Topic/%3Cios%3E%20defaultfloat.md)|設定 `ios_base` 物件的旗標會使用浮點值的預設顯示格式。|  
|[固定](../Topic/fixed.md)|指定浮點數會以固定十進位標記法顯示。|  
|[hex](../Topic/hex.md)|指定以基底 16 標記法顯示整數變數。|  
|[internal](../Topic/internal%20\(Standard%20C++%20Library\).md)|使數字的正負號靠左對齊，數字靠右對齊。|  
|[左](../Topic/left.md)|使與輸出寬度不同寬的文字出現在具有左邊界的資料流排清中。|  
|[noboolalpha](../Topic/noboolalpha.md)|指定類型 [bool](../cpp/bool-cpp.md) 的變數在資料流中會顯示為 0 或 1。|  
|[noshowbase](../Topic/noshowbase.md)|關閉指出據以顯示數字之標記基底的功能。|  
|[noshowpoint](../Topic/noshowpoint.md)|顯示小數部分為零之浮點數的整數部分。|  
|[noshowpos](../Topic/noshowpos.md)|使正數不明確標示正負號。|  
|[noskipws](../Topic/noskipws.md)|使輸入資料流讀取空格。|  
|[nounitbuf](../Topic/nounitbuf.md)|使輸出在緩衝區已滿時進行緩衝處理和處理。|  
|[nouppercase](../Topic/nouppercase.md)|指定以小寫顯示十六進位數字和科學標記法中的指數。|  
|[oct](../Topic/oct%20\(%3Cios%3E\).md)|指定以基底 8 標記法顯示整數變數。|  
|[右](../Topic/right.md)|使與輸出寬度不同寬的文字出現在具有右邊界的資料流排清中。|  
|[科學](../Topic/scientific.md)|使浮點數使用科學標記法顯示。|  
|[showbase](../Topic/showbase.md)|指出據以顯示數字的標記基底。|  
|[showpoint](../Topic/showpoint.md)|顯示浮點數的整數部分和小數點右側的數字，即使小數部分為零亦然。|  
|[showpos](../Topic/showpos.md)|使正數明確標示正負號。|  
|[skipws](../Topic/skipws.md)|使輸入資料流不讀取空格。|  
|[unitbuf](../Topic/unitbuf.md)|使輸出在緩衝區不為空時進行處理。|  
|[全部大寫](../Topic/uppercase.md)|指定以大寫顯示十六進位數字和科學標記法中的指數。|  
  
### 類別  
  
|||  
|-|-|  
|[basic\_ios](../standard-library/basic-ios-class.md)|此範本類別說明依存於範本參數的輸入資料流 \(屬於範本類別 [basic\_istream](../standard-library/basic-istream-class.md)\) 和輸出資料流 \(屬於範本類別 [basic\_ostream](../standard-library/basic-ostream-class.md)\) 通用的儲存體和成員函式。|  
|[fpos](../standard-library/fpos-class.md)|此範本類別說明可儲存對任何資料流內的任意檔案位置指標進行還原之所有必要資訊的物件。|  
|[ios\_base](../standard-library/ios-base-class.md)|此類別說明未依存於範本參數的輸入和輸出資料流通用的儲存體和成員函式。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)