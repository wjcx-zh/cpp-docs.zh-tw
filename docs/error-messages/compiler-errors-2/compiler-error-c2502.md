---
title: "編譯器錯誤 C2502 | Microsoft Docs"
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
  - "C2502"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2502"
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2502
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 在基底類別上有太多存取修飾詞  
  
 基底類別有一個以上的存取修飾詞 \(Modifier\)。  只允許有一個存取修飾詞 \(`public`、`private` 或 `protected`\)。  
  
 下列範例會產生 C2502：  
  
```  
// C2502.cpp  
// compile with: /c  
class A { };  
class B { };  
class C : private public A { };   // C2502  
  
// OK  
class D : private A {};  
class E : public A, private B {};  
```