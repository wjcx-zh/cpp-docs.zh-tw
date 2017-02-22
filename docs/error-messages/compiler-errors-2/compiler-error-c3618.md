---
title: "編譯器錯誤 C3618 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3618"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3618"
ms.assetid: cacc105d-4389-4cb8-ae6c-41a3622e9a86
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C3618
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 無法定義標記為 DllImport 的方法  
  
 標記為 <xref:System.Runtime.InteropServices.DllImportAttribute> 的方法已經定義在指定的 .DLL 中。  
  
## 範例  
 下列範例會產生 C3618。  
  
```  
// C3618.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[ DllImport("user32.dll", EntryPoint="MessageBox", CharSet=CharSet::Ansi) ]  // CHANGED   
void Func();   
  
void Func() {}   // C3618, remove this function definition to resolve  
```