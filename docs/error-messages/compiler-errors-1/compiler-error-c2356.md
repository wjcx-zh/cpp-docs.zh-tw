---
title: "編譯器錯誤 C2356 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2356"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2356"
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2356
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在轉譯單位中不需要變更初始化區段  
  
 可能的原因：  
  
-   `#pragma init_seg` 之前有區段初始化程式碼  
  
-   `#pragma init_seg` 之前有另一個 `#pragma init_seg`  
  
 若要解決問題，請將該區段初始化程式碼移到模組開頭。  如果需要初始化多個區域，則將它們移到個別的模組。  
  
 下列範例會產生 C2356：  
  
```  
// C2356.cpp  
#pragma warning(disable : 4075)  
  
int __cdecl myexit(void (__cdecl *)());  
int __cdecl myexit2(void (__cdecl *)());  
  
#pragma init_seg(".mine$m",myexit)  
#pragma init_seg(".mine$m",myexit2)   // C2356  
```