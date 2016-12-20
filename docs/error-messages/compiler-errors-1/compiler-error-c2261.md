---
title: "編譯器錯誤 C2261 | Microsoft Docs"
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
  - "C2261"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2261"
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2261
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'string' : 組件參考無效且無法解析  
  
 值無效。  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 是用來指定 friend 組件。  例如，如果 a.dll 要指定 b.dll 做為 friend 組件，則您要指定 \(在 a.dll 中\)：InternalsVisibleTo\("b"\)。  然後執行階段就會允許 b.dll 存取 a.dll 中的所有項目 \(只有私用型別除外\)。  
  
 如需在指定 Friend 組件時的正確語法之詳細資訊，請參閱 [Friend 組件 \(C\+\+\)](../../dotnet/friend-assemblies-cpp.md)。  
  
## 範例  
 下列範例會產生 C2261。  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```