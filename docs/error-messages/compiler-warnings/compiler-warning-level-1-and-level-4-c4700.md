---
title: "編譯器警告 (層級 1 和層級 4) C4700 | Microsoft Docs"
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
  - "C4700"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4700"
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1 和層級 4) C4700
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了未初始化的區域變數 'name'  
  
 您沒有在使用區域變數 *name* 之前先指派其值，這樣會導致無法預期的結果。  
  
 下列範例會產生 C4700：  
  
```  
// C4700.cpp  
// compile with: /W1  
int main() {  
   int i;  
   return i;   // C4700  
}  
```  
  
 在 [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 之下，這個警告屬於層級 4。下列範例會產生 C4700：  
  
```  
// C4700b.cpp  
// compile with: /W4 /clr:safe /c  
using namespace System;  
int main() {  
   Int32^ bi;  
   return *bi;   // C4700  
}  
```