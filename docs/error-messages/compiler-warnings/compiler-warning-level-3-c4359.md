---
title: "編譯器警告 (層級 3) C4359 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4359"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4359"
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4359
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 實際對齊 \(8\) 大於 \_\_declspec\(align\(\)\) 中指定的值  
  
 為型別指定的對齊小於為其中一個資料成員之型別的對齊。如需詳細資訊，請參閱[align](../../cpp/align-cpp.md)。  
  
## 範例  
 下列範例會產生 C4359。  
  
```  
// C4359.cpp  
// compile with: /W3 /c  
struct __declspec(align(8)) C8 { __int64 i; };  
struct __declspec(align(4)) C4  { C8 m8; };   // C4359  
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK  
struct __declspec(align(16)) C16  { C8 m8; };   // OK  
```