---
title: "連結器工具錯誤 LNK1166 | Microsoft Docs"
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
  - "LNK1166"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1166"
ms.assetid: d69548a8-0efb-44e1-90b7-b27636a4b575
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1166
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法調整位於位移 \= offset，數值 \= value 的程式碼  
  
 LINK 無法填補 \(Pad\) 必要的程式碼。  
  
 特定處理器不允許某些指令跨頁面界限。  LINK 嘗試加入填補以修正這種情況。  在本例中，LINK 無法解決這個問題。