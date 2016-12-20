---
title: "編譯器警告 (層級 1 和 4) C4223 | Microsoft Docs"
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
  - "C4223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4223"
ms.assetid: 6fc44336-0250-4432-928b-fc5dbe7b7c1c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1 和 4) C4223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：將非左值陣列轉換為指標  
  
 在標準的 C 中，您無法將非左值的陣列轉換成指標。  使用的 Microsoft 擴充功能 \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\)，您就可以這麼做。