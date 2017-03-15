---
title: "編譯器警告 C4958 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4958"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4958"
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4958
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operation' : 指標算術無法驗證  
  
 使用指標算術會產生未經驗證的影像。  
  
 如需詳細資訊，請參閱[純粹的和可驗證的程式碼](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [\/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。  
  
 下列範例會產生 C4958：  
  
```  
// C4958.cpp // compile with: /clr:safe // #pragma warning( disable : 4958 ) using namespace System; int main( ) { Int32 arr[] = new Int32[10]; Int32* p = &arr[0]; p++;   // C4958 }  
```  
  
 編譯器使用指標算術來實作陣列運算。 因此，無法驗證原生陣列。請改用 CLR 陣列。 如需詳細資訊，請參閱[陣列](../../windows/arrays-cpp-component-extensions.md)。  
  
 下列範例會產生 C4958：  
  
```  
// C4958b.cpp // compile with: /clr:safe // #pragma warning( disable : 4958 ) int main() { int array[5]; array[4] = 0;   // C4958 }  
```