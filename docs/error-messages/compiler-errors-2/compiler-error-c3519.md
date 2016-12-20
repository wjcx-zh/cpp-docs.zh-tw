---
title: "編譯器錯誤 C3519 | Microsoft Docs"
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
  - "C3519"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3519"
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3519
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'invalid\_param' : 對 embedded\_idl 屬性無效的參數  
  
 傳遞了參數給 [\#import](../../preprocessor/hash-import-directive-cpp.md) 的 `embedded_idl` 屬性，但編譯器無法辨識該參數。  
  
 `embedded_idl` 唯一允許的參數是 `emitidl` 和 `no_emitidl`。  
  
 下列範例會產生 C3519：  
  
```  
// C3519.cpp  
// compile with: /LD  
[module(name="MyLib2")];  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")     
// C3519  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")     
// OK  
```