---
title: "編譯器警告 (層級 1) C4508 | Microsoft Docs"
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
  - "C4508"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4508"
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4508
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 函式應傳回值; 假定 'void' 傳回型別  
  
 函式未指定傳回型別。  在此情況下，也應該會引發 C4430，而編譯器會實作由 C4430 報告的修復 \(預設值為 int\)。  
  
 若要解除這項警告，請明確宣告函式的傳回型別。  
  
 下列範例會產生 C4508：  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```