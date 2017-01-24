---
title: "編譯器警告 (層級 1) C4216 | Microsoft Docs"
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
  - "C4216"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4216"
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4216
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充 : float long  
  
 預設的 Microsoft 擴充功能 \(\/Ze\) 將 **float long** 視同 **double** 使用，  ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 則否。  請使用 **double** 維持相容性。  下列範例會產生 C4216：  
  
```  
// C4216.cpp  
// compile with: /W1  
float long a;   // C4216  
  
// use the line below to resolve the warning  
// double a;  
  
int main() {  
}  
```