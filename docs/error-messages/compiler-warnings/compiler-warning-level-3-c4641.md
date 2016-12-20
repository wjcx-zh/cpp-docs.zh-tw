---
title: "編譯器警告 (層級 3) C4641 | Microsoft Docs"
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
  - "C4641"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4641"
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4641
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文件註解有模稜兩可的交互參考  
  
 編譯器無法清楚明確地解析參考。  若要解除這項警告，請指定必要的參數資訊，讓參考不致於模稜兩可。  
  
 如需詳細資訊，請參閱[XML 文件](../../ide/xml-documentation-visual-cpp.md)。  
  
## 範例  
 下列範例會產生 C4641。  
  
```  
// C4641.cpp  
// compile with: /W3 /doc /clr /c  
  
/// <see cref="f" />   // C4641  
// try the following line instead  
// /// <see cref="f(int)" />  
public ref class GR {  
public:  
   void f( int ) {}  
   void f( char ) {}  
};  
```