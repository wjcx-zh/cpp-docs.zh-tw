---
title: "編譯器警告 (層級 4) C4206 | Microsoft Docs"
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
  - "C4206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4206"
ms.assetid: 3df97812-3ed7-4003-9769-057acf97ce3c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4206
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**使用非標準的擴充：轉譯單位是空白的**  
  
 檔案經過前置處理之後是空的。  
  
 此擴充可避免您的程式碼被帶到其他編譯器。  它在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 之下會產生錯誤，而且只能用在 C 的原始程式碼中。