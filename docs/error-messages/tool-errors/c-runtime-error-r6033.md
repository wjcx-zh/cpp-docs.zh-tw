---
title: "C 執行階段錯誤 R6033 | Microsoft Docs"
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
  - "R6033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6033"
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
caps.latest.revision: 4
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 執行階段錯誤 R6033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

於機器碼初始設定期間，嘗試在這個組件中使用 MSIL 程式碼。這表示應用程式中有錯誤。最可能的原因是從原生建構函式或從 DllMain 中呼叫 MSIL 編譯的 \(\/clr\) 函式所致。  
  
 這項診斷表示在載入器鎖定期間執行了 MSIL 指令。  如需詳細資訊，請參閱[混合組件的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。