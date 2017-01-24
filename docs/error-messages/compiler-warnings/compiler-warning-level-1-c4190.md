---
title: "編譯器警告 (層級 1) C4190 | Microsoft Docs"
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
  - "C4190"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4190"
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4190
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier1' 已指定 C\-連結，但傳回與 C 不相容的 UDT 'identifier2'  
  
 函式或函式指標以 UDT \(使用者定義型別，其為類別、結構、列舉、同位或 [\_\_value](../../misc/value.md) 型別\) 為傳回型別和 `extern` "C" 連結。  這種情形在下列狀況下是合法的：  
  
-   這個函式的所有呼叫都由 C\+\+ 發出。  
  
-   此函式定義是以 C\+\+ 編寫。  
  
## 範例  
  
```  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```