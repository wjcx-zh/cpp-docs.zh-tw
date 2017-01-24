---
title: "編譯器錯誤 C2081 | Microsoft Docs"
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
  - "C2081"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2081"
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2081
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 在型式參數清單中的名稱不合法  
  
 識別項導致語法錯誤。  
  
 這項錯誤可能會因為使用舊樣式的型式參數清單而造成。  您必須在型式參數清單中指定型式參數的型別。  
  
 下列範例會產生 C2081：  
  
```  
// C2081.c  
void func( int i, j ) {}  // C2081, no type specified for j  
```  
  
 可能的解決方案：  
  
```  
// C2081b.c  
// compile with: /c  
void func( int i, int j ) {}  
```