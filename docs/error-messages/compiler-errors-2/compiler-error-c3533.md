---
title: "編譯器錯誤 C3533 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3533"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3533"
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3533
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 參數不能有包含 'auto' 的型別  
  
 如果預設 [\/Zc:auto](../../build/reference/zc-auto-deduce-variable-type.md) 編譯器選項仍在作用中，則無法以 `auto` 關鍵字來宣告方法或範本參數。  
  
### 更正這個錯誤  
  
1.  移除參數宣告中的 `auto` 關鍵字。  
  
## 範例  
 下列範例會產生 C3535 錯誤，因為使用了 `auto` 關鍵字宣告函式參數，並且使用 **\/Zc:auto** 來編譯。  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## 範例  
 下列範例會產生 C3535 錯誤，因為使用了 `auto` 關鍵字宣告範本參數，並且使用 **\/Zc:auto** 編譯範例。  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [\/Zc:auto \(推算變數類型\)](../../build/reference/zc-auto-deduce-variable-type.md)