---
title: "編譯器錯誤 C3195 | Microsoft Docs"
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
  - "C3195"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3195"
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3195
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator': 已被保留，不能做為 ref 類別或實值型別的成員。必須使用 'operator' 關鍵字定義 CLR 或 WinRT 運算子  
  
 編譯器偵測到使用 Managed Extensions for C\+\+ 語法的運算子定義。  
  
 請使用新的 C\+\+ 語法或使用 **\/clr:oldSyntax** 編譯器選項，啟用 Managed Extensions for C\+\+ 語法。  
  
 下列範例會產生 C3195，並示範如何修正此問題：  
  
```  
// C3195.cpp  
// compile with: /clr /LD  
#using <mscorlib.dll>  
value struct V {  
   static V op_Addition(V v, int i);   // C3195  
   static V operator +(V v, char c);   // OK for new C++ syntax   
};  
```