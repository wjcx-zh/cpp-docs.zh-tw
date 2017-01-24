---
title: "編譯器錯誤 C2086 | Microsoft Docs"
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
  - "C2086"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2086"
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2086
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 重複定義  
  
 識別項被定義超過一次以上，或是後來的宣告和先前的宣告不同。  
  
 C2086 可能會因所參考 C\# 組件之累加建置的結果而產生。  請重新建置 C\# 組件，以消除這項錯誤。  
  
 下列範例會產生 C2086：  
  
```  
// C2086.cpp  
main() {  
  int a;  
  int a;   // C2086 not an error in ANSI C  
}  
```