---
title: "編譯器錯誤 C2693 | Microsoft Docs"
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
  - "C2693"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2693"
ms.assetid: b7364ca8-b6be-48c0-97d6-6029787fb171
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2693
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 對 Managed 或 WinRT 陣列參考的非法比較  
  
 您不能測試 Managed 或 WinRT 陣列是否有任何種類的不相等。  例如，您可以測試以查看 Managed 陣列是否相等，但是您不能測試以查看一個陣列是否大於或小於另一個陣列。  
  
 **Managed Extensions for C\+\+**  
  
 您不能測試 [\_\_gc](../../misc/gc.md) 陣列是否有任何種類的不相等。  例如，您可以測試以查看 Managed 陣列是否相等，但是您不能測試以查看一個陣列是否大於或小於另一個陣列。  
  
 下列範例會產生 C2693：  
  
```  
// C2693b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
int func3(int a __gc[], int b __gc[]) {  
   return a < b;    // C2693  
}  
int func1(int a __gc[], int b __gc[]) {  
   return a != b;   // OK  
}  
  
int func2(int a __gc[], int b __gc[]) {  
   return a == b;   // OK  
}  
```