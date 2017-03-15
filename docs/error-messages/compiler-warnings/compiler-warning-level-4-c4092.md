---
title: "編譯器警告 (層級 4) C4092 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4092"
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 4) C4092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

sizeof 傳回 'unsigned long'  
  
 `sizeof` 運算子的運算元非常大，因此 `sizeof` 傳回不帶正負號的 **long**。  這項警告是發生於 Microsoft Extensions \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\) 之下。  在 ANSI 相容性 \(\/Za\) 之下，以截斷的結果替代。