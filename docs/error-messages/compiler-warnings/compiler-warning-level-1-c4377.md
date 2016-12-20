---
title: "編譯器警告 (層級 1) C4377 | Microsoft Docs"
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
  - "C4377"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4377"
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4377
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

原生型別預設為私用，\-d1PrivateNativeTypes 已被取代  
  
 在舊版產品中，組件的原生型別是預設為公用，並且使用沒有文件記錄的內部編譯器選項 \(**\/d1PrivateNativeTypes**\) 將它們變成私用。  
  
 所有型別 \(包括原生和 CLR\) 現在在組件中都預設為私用，因此不再需要 **\/d1PrivateNativeTypes**。  
  
## 範例  
 下列範例會產生 C4377。  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```