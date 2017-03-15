---
title: "編譯器警告 (層級 3) C4638 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4638"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4638"
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 3) C4638
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文件註解目標：未知符號 'symbol' 的參考  
  
 編譯器無法解析符號 \(***符號***\)。 符號在編譯中必須有效。  
  
 下列範例會產生 C4638：  
  
```  
// C4638.cpp // compile with: /clr /doc /LD /W3 using namespace System; /// Text for class MyClass. public ref class MyClass { public: /// <summary> Text </summary> /// <see cref="aSymbolThatAppearsNowhereInMyProject"/> // Try the following line instead: // /// <see cref="System::Console::WriteLine"/> void MyMethod() {} };   // C4638  
```