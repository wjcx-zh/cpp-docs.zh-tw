---
title: "編譯器警告 (層級 1) C4326 | Microsoft Docs"
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
  - "C4326"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4326"
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4326
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' 的傳回型別應該是 'type1'，而非 'type2'  
  
 函式傳回 ***type1*** 之外的型別。  例如，使用 [\/Za](../../build/reference/za-ze-disable-language-extensions.md)，main 不會傳回 `int`。  
  
 下列範例會產生 C4326：  
  
```  
// C4326.cpp  
// compile with: /Za /W1  
char main()  
{   // C4326 try int main  
}  
```