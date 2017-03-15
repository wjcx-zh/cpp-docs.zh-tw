---
title: "編譯器警告 (層級 1) C4518 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4518"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4518"
ms.assetid: 4ad21004-f076-43fd-99f4-4bf1f9be4c0b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4518
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'specifier' : 此處未預期儲存類別或型別規範; 已忽略  
  
 下列範例會產生 C4518：  
  
```  
// C4518.cpp  
// compile with: /c /W1  
_declspec(dllexport) extern "C" void MyFunction();   // C4518  
  
extern "C" void MyFunction();   // OK  
```