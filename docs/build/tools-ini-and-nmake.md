---
title: "Tools.ini 和 NMAKE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE 程式, 讀取檔案"
  - "Tools.ini 和 NMake"
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tools.ini 和 NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除非使用 \/R，否則 NMAKE 在讀取 Makefile 之前先讀取 Tools.ini。  它會先在目前目錄中尋找 Tools.ini，然後在 INIT 環境變數所指定的目錄中尋找。  在初始設定檔案中 NMAKE 設定的區段以 `[NMAKE]` 開頭，可包含任何 Makefile 資訊。  在不同的行上，以數字符號 \(\#\) 為開頭加以指定命令。  
  
## 請參閱  
 [執行 NMAKE](../build/running-nmake.md)