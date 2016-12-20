---
title: "編譯器警告 C4687 | Microsoft Docs"
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
  - "C4687"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4687"
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4687
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': 密封抽象類別無法實作介面 'interface'  
  
 密封抽象類別一般來說只能用來存放靜態成員函式。  
  
 如需詳細資訊，請參閱 [abstract](../../windows/abstract-cpp-component-extensions.md) 和 [sealed](../../windows/sealed-cpp-component-extensions.md)。  
  
 C4687 是預設做為錯誤訊息發出。  您可以利用 [warning](../../preprocessor/warning.md) pragma 抑制 C4687。  如果確定您要在密封抽象類別中實作介面，您可以抑制 C4687。  
  
## 範例  
 下列範例會產生 C4687。  
  
```  
// C4687.cpp  
// compile with: /clr /c  
interface class A {};  
  
ref struct B sealed abstract : A {};   // C4687  
ref struct C sealed : A {};   // OK  
ref struct D abstract : A {};   // OK  
```