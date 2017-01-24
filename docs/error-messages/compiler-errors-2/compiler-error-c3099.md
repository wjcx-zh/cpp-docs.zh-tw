---
title: "Compiler Error C3099 | Microsoft Docs"
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
  - "C3099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3099"
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'keyword': 對 Managed 屬性使用 \[System::AttributeUsageAttribute\]；對 WinRT 屬性使用 \[Windows::Foundation::Metadata::AttributeUsageAttribute\]  
  
 使用 <xref:System.AttributeUsageAttribute> 宣告 **\/clr** 屬性。  使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 宣告 Windows 執行階段屬性。  
  
 如需 \/CLR 屬性的詳細資訊，請參閱[User\-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  如需 Windows 執行階段中支援的屬性，請參閱 [Windows.Foundation.Metadata 命名空間](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
## 範例  
 下列範例會產生 C3099，並示範如何修正此問題。  
  
```  
// C3099.cpp  
// compile with: /clr /c  
using namespace System;  
[usage(10)]   // C3099  
// try the following line instead  
// [AttributeUsageAttribute(AttributeTargets::All)]  
ref class A : Attribute {};  
```