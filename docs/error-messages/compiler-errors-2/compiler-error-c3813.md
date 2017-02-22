---
title: "編譯器錯誤 C3813 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3813"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3813"
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C3813
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

屬性宣告只可以出現於 managed 或 WinRT 類型的定義中  
  
 [屬性](../../misc/property.md)只能在 Managed 或 Windows Runtime 類型中宣告。  原生類型不支援 `property` 關鍵字。  
  
 下列範例會產生 C3813，並說明如何加以修正：  
  
```  
// C3813.cpp  
// compile by using: cl /c /clr C3813.cpp  
class A  
{  
   property int Int; // C3813  
};  
  
ref class B  
{  
   property int Int; // OK - declared within managed type  
};  
```