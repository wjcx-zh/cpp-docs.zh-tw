---
title: "編譯器警告 (層級 4) C4611 | Microsoft Docs"
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
  - "C4611"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4611"
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4611
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' 和 C\+\+ 物件解構間的互動是不可移植的  
  
 在某些平台上，含有 **catch** 的函式，可能在超出範圍時不支援 C\+\+ 物件解構語法。  
  
 若要避免發生非預期的行為，請避免在有建構函式和解構函式 \(Destructor\) 的函式中使用 **catch**。  
  
 此警告只會發出一次；請參閱 [pragma warning](../../preprocessor/warning.md)。