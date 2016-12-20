---
title: "編譯器錯誤 C2758 | Microsoft Docs"
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
  - "C2758"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2758"
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2758
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member'：必須初始化參考類型的成員  
  
 當建構函式未初始化初始設定式清單中參考類型的成員時，會產生編譯器錯誤 C2758。  編譯器會將成員保持未定義的狀態。  在建構函式的初始化清單中宣告參考成員變數或提供值時，必須初始化。  
  
 下列範例會產生 C2758：  
  
```  
// C2758.cpp  
// Compile by using: cl /W3 /c C2758.cpp  
struct A {  
   const int i;  
  
   A(int n) { };   // C2758  
   // try the following line instead  
   // A(int n) : i{n} {};  
};  
```