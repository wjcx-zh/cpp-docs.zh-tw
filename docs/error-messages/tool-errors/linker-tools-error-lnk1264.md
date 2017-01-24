---
title: "連結器工具錯誤 LNK1264 | Microsoft Docs"
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
  - "LNK1264"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1264"
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1264
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定了 \/LTCG:PGINSTRUMENT，但未要求程式碼產生。檢測失敗  
  
 已指定 **\/LTCG:PGINSTRUMENT**，但找不到以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯的 .obj 檔。  無法檢測 \(Instrumentation\)，連結失敗。  命令列中至少要有一個以 **\/GL** 編譯的 .obj 檔才能進行檢測。  
  
 特性指引最佳化 \(PGO\) 只適用於 64 位元編譯器。