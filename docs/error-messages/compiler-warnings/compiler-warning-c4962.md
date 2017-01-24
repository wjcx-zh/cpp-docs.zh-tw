---
title: "編譯器警告 C4962 | Microsoft Docs"
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
  - "C4962"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4962"
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4962
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 特性指引最佳化已停用，因為最佳化導致分析資料變成不一致  
  
 函式並不是使用 \/LTCG:PGO 進行編譯，因為函式的計數 \(分析\) 資料不可靠。 請重做分析，以重新產生包含該函式不可靠分析資料的 .pgc 檔。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。