---
title: "編譯器錯誤 C3624 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3624"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3624"
ms.assetid: eaac6a4f-eb11-4e4d-ab12-124ba995c5cf
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C3624
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 使用這個型別必須有 assembly 'assembly' 的參考  
  
 未指定編譯您的程式碼所需之組件 \(參考\)；請將組件傳遞至 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指示詞。  
  
 下列範例會產生 C3624：  
  
```  
// C3624.cpp  
// compile with: /clr /c  
#using <System.Windows.Forms.dll>  
  
// Uncomment the following 2 lines to resolve.  
// #using <System.dll>  
// #using <System.Drawing.dll>  
  
using namespace System;  
  
public ref class MyForm : public Windows::Forms::Form {};   // C3624  
```  
  
 下列範例會產生 C3624：  
  
```  
// C3624_b.cpp  
// compile with: /clr:oldSyntax /c  
#using <System.Windows.Forms.dll>  
  
// Uncomment the following 2 lines to resolve.  
// #using <System.dll>  
// #using <System.Drawing.dll>  
  
using namespace System;  
  
public __gc class MyForm : public Windows::Forms::Form {};   // C3624  
```