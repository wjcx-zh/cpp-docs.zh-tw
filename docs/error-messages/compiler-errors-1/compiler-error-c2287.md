---
title: "編譯器錯誤 C2287 | Microsoft Docs"
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
  - "C2287"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2287"
ms.assetid: 64556299-4e1f-4437-88b7-2464fc0b95bb
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2287
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': 繼承表示: 此處不可用 'representation1'，必須用 'representation2'  
  
 使用了簡單於所需的表示來宣告類別。  
  
 下列範例會產生 C2287：  
  
```  
// C2287.cpp  
// compile with: /vmg /c  
class __single_inheritance X;  
class __single_inheritance Y;  
  
struct A { };  
struct B { };  
struct X : A, B { };  // C2287  X uses multiple inheritance  
struct Y : A { };  // OK  
```