---
title: "編譯器警告 (層級 4) C4960 | Microsoft Docs"
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
  - "C4960"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4960"
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4960
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' 太大而無法分析  
  
 使用 [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) 時，編譯器偵測到函式大於 65,535 個指令的輸入模組。 這類大型函式不適用於特性指引最佳化。  
  
 若要解決這個警告，請減少函式的大小。