---
title: "編譯器警告 (層級 4) C4682 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4682"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4682"
ms.assetid: 858ea157-1244-4a61-85df-97b3de43d418
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 4) C4682
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parameter' : 沒有指定方向參數屬性，預設為 \[in\]  
  
 屬性介面中的參數方法沒有方向屬性 [in](../../windows/in-cpp.md) 或 [out](../../windows/out-cpp.md)。 此參數預設為 in。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4682：  
  
```  
// C4682.cpp // compile with: /W4 #pragma warning(default : 4682) #include <windows.h> [module(name="MyModule")]; [ library_block, object, uuid("c54ad59d-d516-41dd-9acd-afda17565c2b") ] __interface IMyIface : IUnknown { HRESULT f1(int i, int *pi); // C4682 // try the following line // HRESULT f1([in] int i, [in] int *pi); }; int main() { }  
```