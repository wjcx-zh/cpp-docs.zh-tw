---
title: "方向旗標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.flags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "方向旗標"
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 方向旗標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

方向旗標是 80x86 Intel 處理器特有的 CPU 旗標。  這個屬性適用於任何使用 REP \(repeat\) 前綴的組合語言指令，例如 MOVS 、 MOVSD 、 MOVSW 等。  方向旗標被清除之後，提供給適用指令的位置會增加。  
  
 C 執行階段常式假設方向旗標是清除的狀態。  如果您與其他函式一起使用 C 執行階段函式，您必須確定其他函式不會處理方向旗標或還原到原來的狀態。  在進入時預期方向旗標是清除的狀態可以使執行階段程式嗎執行得更快更有效率。  
  
 C 執行階段程式庫，例如字串修改和緩衝區修改程式，預期方向旗標是清空的狀態。  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)