---
title: "編譯器錯誤 C2600 | Microsoft Docs"
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
  - "C2600"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2600"
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2600
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function'：無法定義編譯器產生的特殊成員函式 \(必須先在類別中宣告\)  
  
 必須先在類別中宣告建構函式或解構函式之類的成員函式，才可以將它們定義給該類別。  如果未在類別中宣告任何建構函式和解構函式，則編譯器可以產生預設建構函式和解構函式 \(稱為特殊成員函式\)。  不過，如果您在類別中定義這其中一個函式但沒有相符的宣告，編譯器會偵測到衝突。  
  
 若要修正這個錯誤，請在類別宣告中，宣告您在類別宣告之外定義的每個成員函式。  
  
 下列範例會產生 C2600：  
  
```  
// C2600.cpp  
// compile with: /c  
class C {};  
C::~C() {}   // C2600  
  
class D {  
   D::~D();  
};  
  
D::~D() {}  
```