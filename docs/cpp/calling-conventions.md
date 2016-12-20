---
title: "呼叫慣例 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "呼叫慣例"
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 呼叫慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\/C\+\+ 編譯器提供數個用於呼叫內部和外部函式的不同慣例。  了解這些不同的方法可協助您偵錯程式，並將您的程式碼與組合語言常式連結。  
  
 與此主旨有關的主題將說明呼叫慣例之間的差異、引數傳遞方式，以及函式傳回值的方式。  並且也會探討 naked 函式呼叫，這是一個讓您自行撰寫初構和終解程式碼的進階功能。  
  
 如需關於 x64 處理器呼叫慣例的詳細資訊，請參閱[呼叫慣例](../build/calling-convention.md)。  
  
## 本節主題  
  
-   [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md) \(\_\_`cdecl`、\_\_**stdcall**、\_\_**fastcall** 等等\)  
  
-   [呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)  
  
-   [使用 naked 函式呼叫撰寫自訂初構\/終解程式碼](../cpp/naked-function-calls.md)  
  
-   [浮點副處理器和呼叫慣例](../cpp/floating-point-coprocessor-and-calling-conventions.md)  
  
-   [過時呼叫慣例](../cpp/obsolete-calling-conventions.md)  
  
## 請參閱  
 [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)