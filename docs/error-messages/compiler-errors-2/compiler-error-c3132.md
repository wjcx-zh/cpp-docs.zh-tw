---
title: "編譯器錯誤 C3132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3132"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3132"
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C3132
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function\-parameter' : 參數陣列只可套用至型別 'single\-dimensional managed array' 的型式引數  
  
 [ParamArray](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx) 屬性是套用至非一維陣列的參數。  
  
 下列範例會產生 C3132：  
  
```  
// C3132.cpp  
// compile with: /clr /c  
using namespace System;  
void f( [ParamArray] Int32[,] );   // C3132  
void g( [ParamArray] Int32[] );   // C3132  
  
void h( [ParamArray] array<Char ^> ^ MyArray );   // OK  
  
```