---
title: "嚴重錯誤 C1383 | Microsoft Docs"
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
  - "C1383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1383"
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器選項 \/GL 與所安裝 Common Language Runtime 的版本不相容  
  
 搭配使用舊版的 Common Language Runtime 與較新的編譯器時，以及使用 **\/clr** 和 **\/GL.** 編譯時，會發生 C1383。  
  
 若要解決，請不要搭配使用 **\/GL** 與 **\/clr**，或安裝編譯器所隨附的 Common Language Runtime 版本。  
  
 如需詳細資訊，請參閱 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 與 [\/GL \(整個程式最佳化\)](../../build/reference/gl-whole-program-optimization.md)。