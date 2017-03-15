---
title: "連結器工具警告 LNK4206 | Microsoft Docs"
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
  - "LNK4206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4206"
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4206
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到先行編譯型別資訊；未連結或覆寫 'filename'；當做沒有偵錯資訊，連結物件  
  
 使用 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 編譯的指定目的檔未指定於 LINK 命令，或已被覆寫。  
  
 這項警告的一般常見案例是：在程式庫中使用 \/Yc 編譯 .obj 檔，而其中沒有您程式碼中 .obj 檔的符號參考。在這種情況下，連結器將不會使用 \(甚至是看不見\) .obj 檔。此時，您應該要重新編譯程式碼，然後對其餘物件 \(也就是，不用 \/Yc 編譯的物件\) 使用 [\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)。