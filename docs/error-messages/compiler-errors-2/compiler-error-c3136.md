---
title: "編譯器錯誤 C3136 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3136"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3136"
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3136
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'interface' : COM 介面只可以繼承自其他 COM 介面，而 'interface' 不是 COM 介面  
  
 您套用 [interface 屬性](../../windows/interface-attributes.md)的介面繼承自非 COM 介面。  COM 介面最根本繼承自 `IUnknown`。  任何有前置 interface 屬性的介面都是 COM 介面。  
  
 下列範例會產生 C3136：  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```