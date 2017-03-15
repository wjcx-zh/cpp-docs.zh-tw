---
title: "編譯器警告 (層級 4) C4634 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4634"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4634"
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 編譯器警告 (層級 4) C4634
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文件註解: 無法套用: 原因  
  
 XML 文件標記無法套用至所有 C\+\+ 建構。  例如，您無法將文件註解加入命名空間或範本。  
  
 如需詳細資訊，請參閱[XML 文件](../../ide/xml-documentation-visual-cpp.md)。  
  
## 範例  
 下列範例會產生 C4634。  
  
```  
// C4634.cpp // compile with: /W4 /doc /c /// This is a namespace.   // C4634 namespace hello { class MyClass  {}; };  
```  
  
## 範例  
 下列範例會產生 C4634。  
  
```  
// C4634_b.cpp // compile with: /W4 /doc /c /// This is a template.   // C4634 template <class T> class MyClass  {};  
```