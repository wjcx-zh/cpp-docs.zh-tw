---
title: "嚴重錯誤 C1191 | Microsoft Docs"
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
  - "C1191"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1191"
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1191
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'dll' 只能在全域範圍匯入  
  
 將 mscorlib.dll 匯入至使用 \/clr 程式設計的程式無法顯示在命名空間 \(Namespace\) 或函式中，但必須出現在全域範圍。  
  
 下列範例會產生 C1191：  
  
```  
// C1191.cpp  
// compile with: /clr  
namespace sample {  
   #using <mscorlib.dll>   // C1191 not at global scope  
}  
```  
  
 可能的解決方案：  
  
```  
// C1191b.cpp  
// compile with: /clr /c  
#using <mscorlib.dll>  
namespace sample {}  
```