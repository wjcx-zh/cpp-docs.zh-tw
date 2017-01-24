---
title: "編譯器警告 (層級 1) C4027 | Microsoft Docs"
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
  - "C4027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4027"
ms.assetid: f30d57b9-20c4-4284-8686-566d9f0ca7fc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

宣告沒有型式參數清單的函式  
  
 函式宣告沒有型式參數，但在函式定義中有型式參數或在呼叫中有實質參數存在。 之後對這個函式的呼叫會假設函式使用在函式定義或呼叫中找到之類型的實質參數。