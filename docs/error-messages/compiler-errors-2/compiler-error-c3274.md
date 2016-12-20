---
title: "編譯器錯誤 C3274 | Microsoft Docs"
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
  - "C3274"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3274"
ms.assetid: 1f03f18e-b569-48eb-9249-11c70122a305
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3274
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_finally\/finally 缺少對應的 try  
  
 找到缺少對應之 `try` 的 [\_\_finally](../../cpp/try-finally-statement.md) 或 [finally](../../dotnet/finally.md) 陳述式。 若要解決這個問題，請刪除 `__finally` 陳述式，或為 `__finally` 加入 `try` 陳述式。  
  
 下列範例會產生 C3274：  
  
```  
// C3274.cpp // compile with: /clr // C3274 expected using namespace System; int main() { try { try { throw gcnew ApplicationException(); } catch(...) { Console::Error->WriteLine(L"Caught an exception"); } finally { Console::WriteLine(L"In finally"); } } finally { Console::WriteLine(L"In finally"); } // Uncomment the following 3 lines to resolve. // try { //   throw gcnew ApplicationException(); // } finally { Console::WriteLine(L"In finally"); } Console::WriteLine(L"**FAIL**"); }  
```