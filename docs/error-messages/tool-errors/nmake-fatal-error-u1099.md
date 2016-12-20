---
title: "NMAKE 嚴重錯誤 U1099 | Microsoft Docs"
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
  - "U1099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1099"
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆疊溢位  
  
 處理的 Makefile 對 NMAKE 中目前的堆疊配置 \(Stack Allocation\) 而言太複雜。  NMAKE 配置了 0x3000 \(12K\)。  
  
 若要增加 NMAKE 的堆疊配置，請以較大的堆疊選項執行 [editbin \/stack](../../build/reference/stack.md) 公用程式：  
  
 **editbin \/STACK:reserve NMAKE.EXE**  
  
 其中的 *reserve* 是大於在 NMAKE 中目前堆疊配置的數字。