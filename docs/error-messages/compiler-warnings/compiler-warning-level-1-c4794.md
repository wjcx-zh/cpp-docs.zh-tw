---
title: "編譯器警告 (層級 1) C4794 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4794"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4794"
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器警告 (層級 1) C4794
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行緒區域儲存區變數 'variable' 的區段已從 ''section name' 變更為 '.tls$'  
  
 您使用了 [\#pragma data\_seg](../../preprocessor/data-seg.md)，將 tls 變數放在開頭不是 .tls$ 的區段中。  
  
 已定義 [\_\_declspec\(thread\)](../../cpp/thread.md) 變數的目的檔中將會有 .tls$*x* 區段。 EXE 或 DLL 中的.tls 區段將會從這些區段產生。  
  
## 範例  
 下列範例會產生 C4794：  
  
```  
// C4794.cpp // compile with: /W1 /c #pragma data_seg(".someseg") __declspec(thread) int i;   // C4794 // OK #pragma data_seg(".tls$9") __declspec(thread) int j;  
```