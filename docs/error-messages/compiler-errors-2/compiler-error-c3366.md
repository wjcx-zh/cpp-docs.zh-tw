---
title: "編譯器錯誤 C3366 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3366"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3366"
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C3366
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable'：Managed 或 WinRT 類型的靜態資料成員必須定義在類別定義內  
  
 您嘗試參考的 WinRT 或 .NET 類別或介面的靜態成員不在該類別或介面的定義範圍內。  
  
 編譯器必須知道類別的完整定義 \(以在一個階段後發出中繼資料\) ，且需要靜態資料成員在該類別內初始化。  
  
 例如，下列範例會產生 C3366，並說明如何加以修正：  
  
```  
// C3366.cpp  
// compile with: /clr /c  
ref class X {  
   public:  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```  
  
 下列範例會產生 C3366，並說明如何加以修正：  
  
```  
// C3366_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc struct X {  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```