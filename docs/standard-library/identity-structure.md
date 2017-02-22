---
title: "identity 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::identity"
  - "utility/std::identity"
  - "identity"
  - "std.identity"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "identity 類別"
  - "identity 結構"
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# identity 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供型別定義為範本參數的結構。  
  
## 語法  
  
```  
template<class Type>  
   struct identity {  
      typedef Type type;  
      Type operator()(const Type& _Left) const;  
   };  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`_Left`|識別的值。|  
  
## 備註  
 類別包含公用型別定義 `type`，與範本參數型別。  它與樣板函式 [forward](../Topic/forward.md) 一起用來確定函式參數具有所需型別。  
  
 為了與舊版程式碼的相容性，類別也會定義傳回其引數 `_Left`的 Identity 函式 `operator()` 。  
  
## 需求  
 **標題:** \<公用程式\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<utility\>](../standard-library/utility.md)