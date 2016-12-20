---
title: "編譯器警告 (層級 1) C4445 | Microsoft Docs"
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
  - "C4445"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4445"
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4445
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function'：在 WinRT 或 Managed 類型中，虛擬方法不可為私用  
  
 若是私用虛擬函式，它無法衍生類型存取。  若要修正此錯誤，請將虛擬成員函式的存取範圍變更為受保護或公用。