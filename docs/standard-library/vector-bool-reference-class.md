---
title: "vector&lt;bool&gt;::reference 類別 | Microsoft Docs"
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
  - "vector<bool>::reference"
  - "std::vector<bool>::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector<bool> 參考類別"
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
caps.latest.revision: 22
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vector&lt;bool&gt;::reference 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`vector<bool>::reference` 類別是 [vector\<bool\> 類別](../standard-library/vector-bool-class.md)提供的 Proxy 類別來模擬 `bool&`。  
  
## 備註  
 需要模擬參考，因為 C\+\+ 原生不允許對位元的直接參考。  `vector<bool>` 對每個項目只使用一個位元，您可以使用這個 Proxy 類別來參考位元。  不過，因為某些指派無效，參考模擬不完整。  例如，，因為 `vector<bool>::reference` 物件位址無法採用，使用 [vector\<bool\>::operator&#91;&#93;](../Topic/vector%3Cbool%3E::operator.md) 的下列程式碼不正確：  
  
```cpp  
    vector<bool> vb;  
...  
    bool* pb = &vb[1]; // conversion error - do not use  
    bool& refb = vb[1];   // conversion error - do not use  
  
```  
  
### 成員函式  
  
|||  
|-|-|  
|[flip](../standard-library/vector-bool-reference-flip.md)|反轉向量項目的布林值。|  
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|提供從 `vector<bool>::reference` 至 `bool` 的隱含轉換。|  
|[operator\=](../standard-library/vector-bool-reference-operator-assign.md)|將布林值指派給位元，或是將參考的項目所表示的值指派給位元。|  
  
## 需求  
 **標頭**：\<vector\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<vector\>](../standard-library/vector.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)