---
title: "編譯器錯誤 C2128 | Microsoft Docs"
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
  - "c2128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2128"
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2128
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : alloc\_text\/same\_seg 僅適用於使用 C 連結的函式  
  
 `pragma` `alloc_text`  僅適用於宣告為有 C 連結的函式。  
  
 下列範例會產生 C2128：  
  
```  
// C2128.cpp  
// compile with: /c  
  
// Delete the following line to resolve.  
void func();  
// #pragma alloc_text("my segment", func)   // C2128  
  
extern "C" {  
void func();  
}  
  
#pragma alloc_text("my segment", func)  
void func() {}  
```