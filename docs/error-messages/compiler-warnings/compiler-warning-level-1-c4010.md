---
title: "編譯器警告 (層級 1) C4010 | Microsoft Docs"
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
  - "C4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4010"
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

單行註解包含行接續字元  
  
 以 \/\/ 引入的單行註解，包含一個做為行接續字元 \(Line\-Continuation Character\) 的反斜線 \(\\\)。  編譯器將下一行視為接續，並將它視為註解。  
  
 某些語法導引的編輯器，並不將接續字元之後的程式行標示為註解。  請忽略在產生此警告的程式行上為語法標示的色彩。  
  
 下列範例會產生 C4010：  
  
```  
// C4010.cpp  
// compile with: /WX  
int main() {  
   // the next line is also a comment because of the backslash \  
   int a = 3; // C4010  
   a++;  
}  
```