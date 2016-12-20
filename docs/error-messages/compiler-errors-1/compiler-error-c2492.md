---
title: "編譯器錯誤 C2492 | Microsoft Docs"
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
  - "C2492"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2492"
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2492
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : 'thread' 資料可能沒有 DLL 介面  
  
 變數是以 [thread](../../cpp/thread.md) 屬性和 DLL 介面來宣告。  `thread` 變數的位址需等到執行階段才會知道，因此它無法連結至 DLL 匯入或匯出。  
  
 下列範例會產生 C2492：  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```