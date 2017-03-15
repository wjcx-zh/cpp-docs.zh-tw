---
title: "編譯器警告 (層級 4) C4513 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4513"
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 4) C4513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class' : 無法產生解構函式  
  
 編譯器無法為提供的類別產生預設的解構函式；未建立解構函式。  解構函式在基底類別中，但無法被衍生類別存取。  如果該類別有私用的解構函式，請將它設定成公用或保護。