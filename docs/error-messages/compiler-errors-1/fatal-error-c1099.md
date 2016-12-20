---
title: "嚴重錯誤 C1099 | Microsoft Docs"
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
  - "C1099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1099"
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編輯後繼續程式引擎正在終止編譯  
  
 編輯後繼續已載入先行編譯的標頭檔來準備編譯程式碼變更，但後續動作 \(例如，先行編譯的標頭 `#include` 陳述式之前的程式碼變更，或停止偵錯工具\) 防止編輯後繼續使用該程序來完成編譯。 您不需要採取任何動作來修正這個錯誤。