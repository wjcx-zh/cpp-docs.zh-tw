---
title: "編譯器警告 (層級 2) C4826 | Microsoft Docs"
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
  - "C4826"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4826"
ms.assetid: 286f5c1d-8c14-43f7-aaa6-a891db2fdc64
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2) C4826
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 'type1 ' 至 'type\_2' 的轉換是 sign\-extended。這可能會造成未預期的執行階段行為。  
  
 這個警告訊息是表示編譯器在 32 位元指標轉換成 64 位元變數時執行正負號擴張 \(Sign Extension\)。  
  
 如果擴張是在 Windows HANDLE 型別上執行，則忽略這個警告訊息並不會發生問題。  如果擴張是在指標型別 \(Pointer Type\) 上執行，您應該要修改此轉換，避免發生正負號擴張的情形 \(請參閱下面範例\)。  
  
 C4826 預設為關閉。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 範例  
 下列範例會產生 C4826：  
  
```  
// C4826.cpp  
// compile with: /W2 /c  
#include <windows.h>  
#pragma warning(default: 4826)  
  
void * __ptr64 F1 (void * __ptr32 P ) {  
   return (void * __ptr64)P;   // C4826  
   // try the following line instead  
   // return (void * __ptr64)(ULONGLONG)(ULONG)P;  
}  
  
void * __ptr64 F2 ( void * P ) {  
   return (void * __ptr64)P;   // C4826  
   // try the following line instead  
   // return (void * __ptr64)(ULONGLONG)(ULONG)P;  
}  
  
unsigned __int64 F3r ( void * P ) {  
   return (unsigned __int64)P;   // C4826  
   // try the following line instead  
   // return (unsigned __int64)(ULONGLONG)(ULONG)P;  
}  
```