---
title: "編譯器警告 (層級 4) C4232 | Microsoft Docs"
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
  - "C4232"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4232"
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4232
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充 : 'identifier' : dllimport 'dllimport' 的位址不是靜態的，不保證唯一  
  
 在 Microsoft 擴充功能 \(\/Ze\) 之下，您可以提供非靜態的值做為以 **dllimport** 修飾詞宣告的函式之位址。  在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 之下，這會引起錯誤。  
  
 下列範例會產生 C4232：  
  
```  
// C4232.c  
// compile with: /W4 /Ze /c  
int __declspec(dllimport) f();  
int (*pfunc)() = &f;   // C4232  
```