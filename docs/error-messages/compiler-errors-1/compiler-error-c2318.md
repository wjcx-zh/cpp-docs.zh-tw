---
title: "編譯器錯誤 C2318 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2318"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2318"
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2318
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

沒有和 catch 處理常式關聯的 try 區塊  
  
 已定義 `catch` 處理常式，但它前面沒有 `try` 區塊。  
  
 下列範例會產生 C2318：  
  
```  
// C2318.cpp // compile with: /EHsc #include <eh.h> int main() { // no try block catch( int ) {}   // C2318 }  
```  
  
 可能的解決方式：  
  
```  
// C2318b.cpp // compile with: /EHsc #include <eh.h> int main() { try{} catch( int ) {} }  
```