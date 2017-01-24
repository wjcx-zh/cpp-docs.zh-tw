---
title: "fpos 類別 | Microsoft Docs"
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
  - "std.fpos"
  - "std::fpos"
  - "iosfwd/std::fpos"
  - "fpos"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fpos 類別"
  - "fpos 類別, 關於 fpos 類別"
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fpos 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此範本類別說明可儲存對任何資料流內的任意檔案位置指標進行還原之所有必要資訊的物件。  屬於類別 fpos\<**St**\> 的物件有效地儲存至少兩個成員物件：  
  
-   位元組位移，屬於類型 [streamoff](../Topic/streamoff.md)。  
  
-   轉換狀態 \(供屬於類別 basic\_filebuf 的物件使用\)，屬於類型 **St**，通常是 `mbstate_t`。  
  
 它也可以儲存屬於類型 `fpos_t` 的任意檔案位置，供屬於類別 [basic\_filebuf](../standard-library/basic-filebuf-class.md) 的物件使用。  但在大小受限的環境中，`streamoff` 與 `fpos_t` 有時候可以互換使用。  若環境中沒有任何資料流有依存於狀態的編碼，實際上可能不會用到 `mbstate_t`。  因此，儲存的成員物件數目可能會不同。  
  
## 語法  
  
```  
  
     template <class   
     Statetype  
     >  
class fpos  
```  
  
#### 參數  
 *Statetype*  
 狀態資訊。  
  
### 建構函式  
  
|||  
|-|-|  
|[fpos](../Topic/fpos::fpos.md)|建立一個物件，其中包含與資料流中的位置 \(位移\) 有關的資訊。|  
  
### 成員函式  
  
|||  
|-|-|  
|[seekpos](../Topic/fpos::seekpos.md)|僅限 Standard C\+\+ 程式庫內部使用。  請勿從您的程式碼呼叫此方法。|  
|[state](../Topic/fpos::state.md)|設定或傳回轉換狀態。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\!\=](../Topic/fpos::operator!=.md)|測試檔案位置指標是否不相等。|  
|[operator\+](../Topic/fpos::operator+.md)|遞增檔案位置指標|  
|[operator\+\=](../Topic/fpos::operator+=.md)|遞增檔案位置指標|  
|[operator\-](../Topic/fpos::operator-.md)|減少檔案位置指標。|  
|[operator\-\=](../Topic/fpos::operator-=.md)|減少檔案位置指標。|  
|[operator\=\=](../Topic/fpos::operator==.md)|測試檔案位置指標是否相等。|  
|[operator streamoff](../Topic/fpos::operator%20streamoff.md)|將類型 `fpos` 的物件轉換成類型 `streamoff` 的物件。|  
  
## 需求  
 **標頭：**\<ios\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)