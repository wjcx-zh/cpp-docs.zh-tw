---
title: "編譯器錯誤 C3385 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3385"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3385"
ms.assetid: 5f1838c1-986e-47db-8dbc-e06976b83cf3
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3385
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class::function' : 具有 DllImport 自訂屬性的函式不能傳回類別的執行個體  
  
 定義於使用 `DllImport` 屬性指定之 .dll 檔中的函式不能傳回類別的執行個體。  
  
 下列範例會產生 C3385：  
  
```  
// C3385.cpp // compile with: /clr /c using namespace System; using namespace System::Runtime::InteropServices; struct SomeStruct1 {}; public ref struct Wrap { [ DllImport("somedll.dll", CharSet=CharSet::Unicode) ] static SomeStruct1 f1([In, Out] SomeStruct1 *pS);   // C3385 };  
```  
  
 下列範例會產生 C3385：  
  
```  
// C3385_2.cpp // compile with: /clr:oldSyntax /c using namespace System; using namespace System::Runtime::InteropServices; struct SomeStruct1 {}; public __gc struct Wrap { [ DllImport("somedll.dll", CharSet=CharSet::Unicode) ] static SomeStruct1 f1([In, Out] SomeStruct1 *pS);   // C3385 };  
```