---
title: "ios_base 類別 | Microsoft Docs"
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
  - "ios_base"
  - "std.ios_base"
  - "std::ios_base"
  - "xiosbase/std::ios_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ios_base 類別"
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ios_base 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此類別說明未依存於範本參數的輸入和輸出資料流通用的儲存體和成員函式。  \(範本類別 [basic\_ios](../standard-library/basic-ios-class.md) 描述何者常見且相依於範本參數。\)  
  
 Ios\_base 類別的物件會儲存格式設定資訊，包括：  
  
-   [fmtflags](../Topic/ios_base::fmtflags.md) 類型物件中的格式旗標。  
  
-   [iostate](../Topic/ios_base::iostate.md) 類型物件中的例外狀況遮罩。  
  
-   `int` 類型物件中的欄位寬度*。*  
  
-   `int` 類型物件中的顯示精確度。  
  
-   **locale** 類型物件中的地區設定物件。  
  
-   兩個可延伸的陣列，具有 **long** 類型和 `void` 指標的項目。  
  
 Ios\_base 類別的物件也會將資料流的狀態資訊儲存在 [iostate](../Topic/ios_base::iostate.md) 類型的物件，以及回呼堆疊中。  
  
### 建構函式  
  
|||  
|-|-|  
|[ios\_base](../Topic/ios_base::ios_base.md)|建構 `ios_base` 物件。|  
  
### Typedef  
  
|||  
|-|-|  
|[event\_callback](../Topic/ios_base::event_callback.md)|描述傳遞至 [register\_call](../Topic/ios_base::register_callback.md) 的函式。|  
|[fmtflags](../Topic/ios_base::fmtflags.md)|指定輸出外觀的常數。|  
|[iostate](../Topic/ios_base::iostate.md)|定義描述資料流狀態的常數。|  
|[openmode](../Topic/ios_base::openmode.md)|描述如何與資料流互動。|  
|[seekdir](../Topic/ios_base::seekdir.md)|指定位移作業的起點。|  
  
### 列舉  
  
|||  
|-|-|  
|[事件](../Topic/ios_base::event.md)|指定事件類型。|  
  
### 常數  
  
|||  
|-|-|  
|[adjustfield](../Topic/ios_base::fmtflags.md)|定義為 `internal` 的位元遮罩                      &#124; `left` &#124; `right`.|  
|[app](../Topic/ios_base::openmode.md)|指定在每次插入之前搜尋到資料流的結尾。|  
|[ate](../Topic/ios_base::openmode.md)|指定在第一次建立控制物件時搜尋到資料流的結尾。|  
|[badbit](../Topic/ios_base::iostate.md)|記錄資料流緩衝區的完整性遺失。|  
|[basefield](../Topic/ios_base::fmtflags.md)|定義為 `dec` 的位元遮罩                      &#124; `hex` &#124; `oct`.|  
|[beg](../Topic/ios_base::seekdir.md)|指定相對於序列開頭的搜尋。|  
|[二進位](../Topic/ios_base::openmode.md)|指定檔案應該以二進位資料流讀取，而不是文字資料流。|  
|[boolalpha](../Topic/ios_base::fmtflags.md)|指定以名稱形式插入或擷取 `bool` 類型的物件 \(例如 `true` 和 `false`\)，而不是以數值形式。|  
|[cur](../Topic/ios_base::seekdir.md)|指定相對於序列中目前位置的搜尋。|  
|[dec](../Topic/ios_base::fmtflags.md)|指定以十進位格式插入或擷取整數值。|  
|[end](../Topic/ios_base::seekdir.md)|指定相對於序列結尾的搜尋。|  
|[eofbit](../Topic/ios_base::iostate.md)|從資料流擷取時記錄檔案結尾。|  
|[failbit](../Topic/ios_base::iostate.md)|記錄從資料流擷取有效欄位失敗。|  
|[固定](../Topic/ios_base::fmtflags.md)|以固定點格式插入浮點數值 \(沒有指數欄位\)。|  
|[floatfield](../Topic/ios_base::fmtflags.md)|定義為 `fixed` 的位元遮罩                      &#124; `scientific`|  
|[goodbit](../Topic/ios_base::iostate.md)|清除所有狀態位元。|  
|[hex](../Topic/ios_base::fmtflags.md)|指定以十六進位格式插入或擷取整數值。|  
|[in](../Topic/ios_base::openmode.md)|指定從資料流擷取。|  
|[internal](../Topic/ios_base::fmtflags.md)|藉由在產生的數字欄位內部一點中插入填滿字元，來填補欄位寬度。|  
|[左](../Topic/ios_base::fmtflags.md)|指定左側對齊。|  
|[oct](../Topic/ios_base::fmtflags.md)|指定以八進位格式插入或擷取整數值。|  
|[out](../Topic/ios_base::openmode.md)|指定插入資料流。|  
|[右](../Topic/ios_base::fmtflags.md)|指定右側對齊。|  
|[科學](../Topic/ios_base::fmtflags.md)|指定以科學記號格式插入浮點數值 \(具有一個指數欄位\)。|  
|[showbase](../Topic/ios_base::fmtflags.md)|指定插入可顯示所產生整數欄位之基底的前置詞。|  
|[showpoint](../Topic/ios_base::fmtflags.md)|指定在產生的浮點欄位無條件插入小數點。|  
|[showpos](../Topic/ios_base::fmtflags.md)|指定在產生的非負數字欄位插入加號。|  
|[skipws](../Topic/ios_base::fmtflags.md)|指定在進行某些擷取前，略過前置空白字元。|  
|[trunc](../Topic/ios_base::openmode.md)|指定在控制物件建立時刪除現有檔案的內容。|  
|[unitbuf](../Topic/ios_base::fmtflags.md)|導致在每次插入之後清除輸出。|  
|[全部大寫](../Topic/ios_base::fmtflags.md)|指定在進行某些插入時，插入小寫字母的大寫對應。|  
  
### 成員函式  
  
|||  
|-|-|  
|[失敗](../Topic/ios_base::failure.md)|成員類別做為範本類別 [basic\_ios](../standard-library/basic-ios-class.md) 成員函式 [clear](../Topic/basic_ios::clear.md) 所擲回之所有例外狀況的基底類別。|  
|[旗標](../Topic/ios_base::flags.md)|設定或傳回目前的旗標設定。|  
|[getloc](../Topic/ios_base::getloc.md)|傳回儲存的地區設定物件。|  
|[imbue](../Topic/ios_base::imbue.md)|變更地區設定。|  
|[Init](../Topic/ios_base::Init.md)|建構時建立標準 iostream 物件。|  
|[iword](../Topic/ios_base::iword.md)|指派將值儲存為 `iword`。|  
|[精確度](../Topic/ios_base::precision.md)|指定要在浮點數顯示的數字位數。|  
|[pword](../Topic/ios_base::pword.md)|指派將值儲存為 `pword`。|  
|[register\_callback](../Topic/ios_base::register_callback.md)|指定回呼函式。|  
|[setf](../Topic/ios_base::setf.md)|設定指定的旗標。|  
|[sync\_with\_stdio](../Topic/ios_base::sync_with_stdio.md)|可確保 iostream 和 C 執行階段程式庫作業依照它們在原始程式碼中出現的順序發生。|  
|[unsetf](../Topic/ios_base::unsetf.md)|使指定的旗標為關閉。|  
|[寬度](../Topic/ios_base::width.md)|設定輸出資料流的長度。|  
|[xalloc](../Topic/ios_base::xalloc.md)|指定變數應該是資料流的一部分。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/ios_base::operator=.md)|`ios_base` 物件的指派運算子。|  
  
## 需求  
 **標頭：**\<ios\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)