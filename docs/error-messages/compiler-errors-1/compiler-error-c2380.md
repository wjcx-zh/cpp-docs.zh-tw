---
title: "編譯器錯誤 C2380 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2380"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2380"
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2380
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 'identifier' 前定義型別 \(具有傳回型別的建構函式，或目前類別名稱的重新定義不合法?\)  
  
 建構函式傳回一數值，或重新定義類別名稱。  
  
 下列範例會產生 C2326：  
  
```  
// C2380.cpp  
// compile with: /c  
class C {  
public:  
   int C();   // C2380, specifies an int return  
   int C;   // C2380, redefinition of i  
   C();   // OK  
};  
```