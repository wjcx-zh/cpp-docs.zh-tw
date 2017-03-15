---
title: "Compiler Error C2394 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2394"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2394"
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Compiler Error C2394
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'your\_type::operator'op'" : CLR 或 WinRT 運算子無效。至少一個參數必須是下列類型：'T^'、'T^%'、'T^&'，其中 T \= 'your\_type'  
  
 Windows 執行階段或 Managed 類型中的運算子沒有至少一個參數，其類型與運算子傳回值的類型相同。  
  
 下列範例會產生 C2394：  
  
```  
// C2394.cpp  
// compile with: /clr /c  
ref struct Y {  
   static Y^ operator -(int i, char c);   // C2394  
  
   // OK  
   static Y^ operator -(Y^ hY, char c);  
   // or  
   static Y^ operator -(int i, Y^& rhY);  
};  
```