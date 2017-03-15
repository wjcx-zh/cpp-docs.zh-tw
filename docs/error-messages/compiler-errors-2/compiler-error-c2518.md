---
title: "編譯器錯誤 C2518 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2518"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2518"
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2518
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在基底類別清單中的關鍵字 'keyword' 不合法; 已忽略  
  
 `class` 和 `struct` 關鍵字不應出現在基底類別清單中。  
  
 下列範例會產生 C2518：  
  
```  
// C2518.cpp  
// compile with: /c  
class B {};  
class C : public class B {};   // C2518  
class D: public B {};   // OK  
```