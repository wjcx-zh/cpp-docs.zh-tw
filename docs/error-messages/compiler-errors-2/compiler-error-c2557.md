---
title: "編譯器錯誤 C2557 | Microsoft Docs"
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
  - "C2557"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2557"
ms.assetid: 48a33d82-aa16-4658-b346-2311fcb39864
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2557
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 沒有建構函式無法初始化 private 和 protected 成員  
  
 只有成員和 Friend 才能將值指派給 private 和 protected 成員。 應該在類別建構函式中初始化非公用成員。