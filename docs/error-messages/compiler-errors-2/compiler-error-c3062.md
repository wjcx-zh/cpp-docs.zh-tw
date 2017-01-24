---
title: "編譯器錯誤 C3062 | Microsoft Docs"
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
  - "C3062"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3062"
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3062
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'enum': 列舉值必須有值，因為基礎型別是 'type'  
  
 您可以指定列舉值的基礎型別。  但是有些型別要求您指定值給每一個列舉值。  
  
 如需列舉的詳細資訊，請參閱[列舉類別](../../windows/enum-class-cpp-component-extensions.md)。  
  
 下列範例會產生 C3062：  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```