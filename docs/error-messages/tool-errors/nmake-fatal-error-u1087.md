---
title: "NMAKE 嚴重錯誤 U1087 | Microsoft Docs"
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
  - "U1087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1087"
ms.assetid: 5236ab54-e117-484d-99c3-852b061fd3d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

相同目標不能有 : 和 :: 相依性  
  
 不可以同時在單冒號 \(**:**\) 和雙冒號 \(`::`\) 相依性中指定目標。  
  
 若要在多個描述區塊 \(Description Block\) 中指定目標，請在每一個相依性列中使用 `::`。