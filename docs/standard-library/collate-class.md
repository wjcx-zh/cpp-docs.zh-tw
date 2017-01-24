---
title: "collate 類別 | Microsoft Docs"
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
  - "std::collate"
  - "locale/std::collate"
  - "std.collate"
  - "collate"
  - "Collate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collate 類別"
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
caps.latest.revision: 18
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# collate 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別，描述可做為地區設定 facet 的物件，以控制字串內的字元順序和群組、字串比較，以及字串雜湊。  
  
## 語法  
  
```  
template <class CharType >  
   class collate : public locale::facet;  
```  
  
#### 參數  
 `CharType`  
 用於程式內部字元編碼的類型。  
  
## 備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。  第一次嘗試存取它的儲存值時，會在 **id** 中儲存唯一的正值。在某些語言中，字元視為單一字元群組及處理，而且在其他語言中，個別字元視為兩個字元。  collate 類別提供的定序服務提供排序這些案例的方式。  
  
### 建構函式  
  
|||  
|-|-|  
|[collate](../Topic/collate::collate.md)|做為地區設定 facet 處理字串排序慣例之 `collate` 類別物件的建構函式。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/collate::char_type.md)|類型，描述 `CharType` 類型之字元。|  
|[string\_type](../Topic/collate::string_type.md)|類型，描述包含 `CharType` 類型字元的 `basic_string` 類型字串。|  
  
### 成員函式  
  
|||  
|-|-|  
|[compare](../Topic/collate::compare.md)|根據其 facet 特定規則，比較兩個字元序列相等或不等。|  
|[do\_compare](../Topic/collate::do_compare.md)|虛擬函式，呼叫以根據其 facet 特定規則，比較兩個字元序列相等或不等。|  
|[do\_hash](../Topic/collate::do_hash.md)|虛擬函式，呼叫以根據其 facet 特定規則，決定序列的雜湊值。|  
|[do\_transform](../Topic/collate::do_transform.md)|虛擬函式，呼叫以將地區設定的字元序列轉換為字串，可用來與從相同地區設定轉換的其他字元序列進行語彙比較。|  
|[hash](../Topic/collate::hash.md)|根據其 facet 特定規則，決定序列的雜湊值。|  
|[Transform \- 轉換](../Topic/collate::transform.md)|將地區設定的字元序列轉換為字串，可用來與從相同地區設定轉換的其他字元序列進行語彙比較。|  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<locale\>](../standard-library/locale.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)