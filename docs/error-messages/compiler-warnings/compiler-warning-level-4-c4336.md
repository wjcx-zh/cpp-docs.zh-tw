---
title: "編譯器警告 (層級 4) C4336 | Microsoft Docs"
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
  - "C4336"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4336"
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4336
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在匯入 'type\_lib2' 之前，匯入交互參考型別程式庫 'type\_lib1'  
  
 已使用 [\#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞參考了型別程式庫。  然而，此型別程式庫包含對其他型別程式庫之參考，且不是以 `#import` 參考該型別程式庫。  編譯器發現另一個 .tlb 檔。  
  
 假設磁碟上有兩個型別程式庫是根據下列兩個檔案建立的 \(用 midl.exe 編譯\)：  
  
```  
// c4336a.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]  
library c4336aLib  
{  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]  
   enum E_C4336  
   {  
      one, two, three  
   };  
};  
```  
  
 第二個型別程式庫：  
  
```  
// c4336b.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]  
library C4336bLib  
{  
   importlib ("c4336a.tlb");  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]  
   struct S_C4336  
   {  
      enum E_C4336 e;  
   };  
};  
```  
  
 下列範例會產生 C4336：  
  
```  
// C4336.cpp  
// compile with: /W4 /LD  
// #import "C4336a.tlb"  
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve  
```