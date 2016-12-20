---
title: "ctype 類別 | Microsoft Docs"
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
  - "ctype"
  - "std::ctype"
  - "std.ctype"
  - "CType"
  - "xlocale/std::ctype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype 類別"
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
caps.latest.revision: 19
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctype 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別，提供用於字元分類、大小寫轉換，以及原生字元集和地區設定所用字元集之間轉換的 facet。  
  
## 語法  
  
```  
template <class CharType>  
   class ctype : public ctype_base;  
```  
  
#### 參數  
 `CharType`  
 用於程式內部字元編碼的類型。  
  
## 備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。  第一次嘗試存取它的儲存值時，會在 **id** 中儲存唯一的正值。基底類別 ctype\_base 中為分類準則提供巢狀位元遮罩類型。  
  
 Standard C\+\+ 程式庫定義這個樣板類別的兩個明確特製化：  
  
-   [ctype](#vclrf_locale_ctype_class)\<`char`\>，分別描述差異的明確特製化。  
  
-   **ctype**\<`wchar_t`\>，會將項目當做寬字元。  
  
 樣板類別 **ctype**\<**CharType**\> 的其他特製化：  
  
-   使用運算式 \(`char`\)**ch**，將 **CharType** 類型的值 ***ch*** 轉換為類型 `char` 的值。  
  
-   使用運算式 **CharType** \(**byte**\)，將 `char` 類型的值 ***byte*** 轉換為類型 **CharType** 的值。  
  
 以明確特製化 **ctype**\<`char`\> 相同的方式，對 `char` 值執行所有其他作業。  
  
### 建構函式  
  
|||  
|-|-|  
|[ctype](../Topic/ctype::ctype.md)|`ctype` 類別物件的建構函式，這些物件做為字元的地區設定 facet。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/ctype::char_type.md)|類型，描述由地區設定使用的字元。|  
  
### 成員函式  
  
|||  
|-|-|  
|[do\_is](../Topic/ctype::do_is.md)|虛擬函式，呼叫以測試單一字元是否有特定屬性，或分類範圍中每個字元的屬性並將其儲存在陣列中。|  
|[do\_narrow](../Topic/ctype::do_narrow.md)|虛擬函式，呼叫以將地區設定使用的 `CharType` 類型字元轉換為原生字元集中 `char` 類型的對應字元。|  
|[do\_scan\_is](../Topic/ctype::do_scan_is.md)|虛擬函式，呼叫以尋找範圍中符合指定之遮罩的第一個字元。|  
|[do\_scan\_not](../Topic/ctype::do_scan_not.md)|虛擬函式，呼叫以尋找範圍中不符合指定之遮罩的第一個字元。|  
|[do\_tolower](../Topic/ctype::do_tolower.md)|虛擬函式，呼叫以將字元或字元範圍轉換為小寫。|  
|[do\_toupper](../Topic/ctype::do_toupper.md)|虛擬函式，呼叫以將字元或字元範圍轉換為大寫。|  
|[do\_widen](../Topic/ctype::do_widen.md)|虛擬函式，呼叫以將原生字元集中 `CharType` 類型的字元轉換為地區設定使用的 `char` 類型的對應字元。|  
|[is](../Topic/ctype::is.md)|測試單一字元是否有特定屬性，或分類範圍中每個字元的屬性並將其儲存在陣列中。|  
|[narrow](../Topic/ctype::narrow.md)|將地區設定使用的 `CharType` 類型的字元轉換為原生字元集中 char 類型的對應字元。|  
|[scan\_is](../Topic/ctype::scan_is.md)|尋找範圍中符合指定之遮罩的第一個字元。|  
|[scan\_not](../Topic/ctype::scan_not.md)|尋找範圍中不符合指定之遮罩的第一個字元。|  
|[tolower](../Topic/ctype::tolower.md)|將字元或字元範圍轉換為小寫。|  
|[toupper](../Topic/ctype::toupper.md)|將字元或字元範圍轉換為大寫。|  
|[widen](../Topic/ctype::widen.md)|將原生字元集中 `char` 類型的字元轉換為地區設定使用的 `CharType` 類型的對應字元。|  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<locale\>](../standard-library/locale.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)