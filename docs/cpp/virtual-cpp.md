---
title: "virtual (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "virtual_cpp"
  - "virtual"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基底類別, 虛擬"
  - "虛擬基底類別, 宣告"
  - "虛擬函式, 宣告"
  - "virtual 關鍵字 [C++]"
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# virtual (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`virtual` 關鍵字宣告虛擬函式或虛擬基底類別。  
  
## 語法  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### 參數  
 `type-specifiers`  
 指定虛擬成員函式的傳回類型。  
  
 `member-function-declarator`  
 宣告成員函式。  
  
 `access-specifier`  
 定義對基底類別的存取層級：`public`、`protected` 或 `private`。  可能出現在 `virtual` 關鍵字之前或之後。  
  
 `base-class-name`  
 識別先前宣告的類別類型。  
  
## 備註  
 如需詳細資訊，請參閱[虛擬函式](../cpp/virtual-functions.md)和[虛擬基底類別](../misc/virtual-base-classes.md)。  
  
 請參閱下列關鍵字：[class](../cpp/class-cpp.md)、[private](../cpp/private-cpp.md)、[public](../cpp/public-cpp.md) 和 [protected](../cpp/protected-cpp.md)。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)