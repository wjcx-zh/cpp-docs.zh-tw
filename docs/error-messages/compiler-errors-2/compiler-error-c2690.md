---
title: "編譯器錯誤 C2690 | Microsoft Docs"
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
  - "C2690"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2690"
ms.assetid: f165a806-14bd-4942-99b7-8a9fc7dea227
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2690
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator'：無法在 Managed 或 WinRT 陣列上執行指標算術  
  
 不允許在 Managed 或 WinRT 陣列上使用指標算術。  請使用陣列索引標記法來周遊陣列。  
  
 **Managed Extensions for C\+\+**  
  
 不允許在 [\_\_gc](../../misc/gc.md) 陣列上使用指標算術。  請使用陣列索引標記法來周遊陣列。  
  
 下列範例會產生 C2690：  
  
```  
// C2690b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
int main() {  
   String* x[] = new String*[10];  
   x[0] = "test";  
   Console::WriteLine(x[0]);  
   x++;   // C2690  
}  
```