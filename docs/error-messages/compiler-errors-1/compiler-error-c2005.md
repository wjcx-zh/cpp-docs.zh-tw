---
title: "編譯器錯誤 C2005 | Microsoft Docs"
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
  - "C2005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2005"
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#line 必須是行號，但找到 'token'  
  
 `#line` 指示詞後面必須跟著一個行號。  
  
 下列範例會產生 C2005：  
  
```  
// C2005.cpp  
int main() {  
   int i = 0;  
   #line i   // C2005  
}  
```  
  
 可能的解決方案：  
  
```  
// C2005b.cpp  
int main() {  
   int i = 0;  
   #line 0  
}  
```