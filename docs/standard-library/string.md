---
title: "&lt;string&gt; | Microsoft Docs"
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
  - "std::<string>"
  - "string/std::<string>"
  - "std.<string>"
  - "<string>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "string 標頭"
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;string&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義容器範本類別 `basic_string` 和各種支援的範本。  
  
 如需 `basic_string` 的詳細資訊，請參閱 [basic\_string 類別](../standard-library/basic-string-class.md)。  
  
## 語法  
  
```  
#include <string>  
```  
  
## 備註  
 C\+\+ 語言和標準 C\+\+ 程式庫支援兩種字串類型：  
  
-   以 Null 結束的字元陣列，通常稱為 C 字串。  
  
-   類型 `basic_string` 的範本類別物件，處理所有 `char` 之類的範本引數。  
  
### Typedef  
  
|||  
|-|-|  
|[string](../Topic/string%20\(C++%20STL%20%3Cstring%3E\).md)|類型，以類型 `char` 的元素做為 `string`，描述範本類別 `basic_string` 的特製化。|  
|[wstring](../Topic/wstring.md)|類型，以類型 `wchar_t` 的元素做為 `wstring`，描述範本類別 `basic_string` 的特製化。|  
|[u16string](../Topic/u16string.md)|類型，根據類型 `char16_t` 的元素，描述範本類別 `basic_string` 的特製化。|  
|[u32string](../Topic/u32string.md)|類型，根據類型 `char32_t` 的元素，描述範本類別 `basic_string` 的特製化。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\+](../Topic/operator+%20\(%3Cstring%3E\).md)|串連兩個字串物件。|  
|[operator\!\=](../Topic/operator!=%20\(%3Cstring%3E\).md)|測試運算子左邊的字串物件是否不等於右邊的字串物件。|  
|[operator\=\=](../Topic/operator==%20\(%3Cstring%3E\).md)|測試運算子左邊的字串物件是否等於右邊的字串物件。|  
|[運算子 \<](../Topic/operator%3C%20\(%3Cstring%3E\).md)|測試運算子左邊的字串物件是否小於右邊的字串物件。|  
|[運算子 \<\=](../Topic/operator%3C=%20\(in%20%3Cstring%3E\).md)|測試運算子左邊的字串物件是否小於或等於右邊的字串物件。|  
|[運算子 \<\<](../Topic/operator%3C%3C%20\(%3Cstring%3E\).md)|將字串插入至輸出資料流的範本函式。|  
|[運算子 \>](../Topic/operator%3E%20\(%3Cstring%3E\).md)|測試運算子左邊的字串物件是否大於右邊的字串物件。|  
|[運算子 \>\=](../Topic/operator%3E=%20\(%3Cstring%3E\).md)|測試運算子左邊的字串物件是否大於或等於右邊的字串物件。|  
|[運算子 \>\>](../Topic/operator%3E%3E%20\(%3Cstring%3E\).md)|從輸入資料流擷取字串的範本函式。|  
  
### 特製化樣板函式  
  
|||  
|-|-|  
|[交換](../Topic/swap%20\(C++%20STL%20%3Cstring%3E\).md)|交換兩個字串的字元陣列。|  
|[stod](../Topic/stod.md)|將字元序列轉換為 `double.`|  
|[stof](../Topic/stof.md)|將字元序列轉換為 `float`。|  
|[stoi](../Topic/stoi.md)|將字元序列轉換為整數。|  
|[stold](../Topic/stold.md)|將字元序列轉換為 `long double`。|  
|[stoll](../Topic/stoll.md)|將字元序列轉換為 `long long`。|  
|[stoul](../Topic/stoul.md)|將字元序列轉換為 `unsigned long`。|  
|[stoull](../Topic/stoull.md)|將字元序列轉換為 `unsigned long long`。|  
|[to\_string](../Topic/to_string.md)|將值轉換成 `string`。|  
|[to\_wstring](../Topic/to_wstring.md)|將值轉換成寬 `string`。|  
  
### 函式  
  
|||  
|-|-|  
|[getline](../Topic/getline%20Template%20Function.md)|從輸入資料流一行一行地擷取字串。|  
  
### 類別  
  
|||  
|-|-|  
|[basic\_string 類別](../standard-library/basic-string-class.md)|範本類別，描述可以儲存一連串任意類似字元之物件的物件。|  
|[char\_traits 結構](../standard-library/char-traits-struct.md)|範本類別，描述與 CharType 類型的字元相關聯的屬性。|  
  
### 特製化  
  
|||  
|-|-|  
|[char\_traits\<char\> 結構](../standard-library/char-traits-char-struct.md)|結構，其為類型 `char` 之元素的範本結構 `char_traits`\<CharType\> 的特製化。|  
|[char\_traits\<wchar\_t\> 結構](../standard-library/char-traits-wchar-t-struct.md)|結構，其為類型 `wchar_t` 之元素的範本結構 `char_traits`\<CharType\> 的特製化。|  
|[char\_traits\<char16\_t\> 結構](../standard-library/char-traits-char16-t-struct.md)|結構，其為類型 `char16_t` 之元素的範本結構 `char_traits`\<CharType\> 的特製化。|  
|[char\_traits\<char32\_t\> 結構](../standard-library/char-traits-char32-t-struct.md)|結構，其為類型 `char32_t` 之元素的範本結構 `char_traits`\<CharType\> 的特製化。|  
  
## 需求  
  
-   **標頭：**\<string\>  
  
-   **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)