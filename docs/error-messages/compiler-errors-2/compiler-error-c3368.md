---
title: "編譯器錯誤 C3368 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3368"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3368"
ms.assetid: 5bfd5be4-dfa9-4b33-9612-010561b40955
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3368
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function declaration' : IDL 的無效呼叫慣例  
  
 .idl 檔中只能使用 [\_\_stdcall](../../cpp/stdcall.md) 或 [\_\_cdecl](../../cpp/cdecl.md) 呼叫慣例。  
  
 下列範例會產生 C3368：  
  
```  
// C3368.cpp // processor: x86 [idl_module(name="Name", dllname="Some.dll")]; [idl_module(name="Name")] int __fastcall f1();   // C3368  
```