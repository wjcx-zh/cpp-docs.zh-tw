---
title: "CL 選項的順序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器, 設定選項"
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CL 選項的順序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

選項可以出現在 CL 命令列的任何位置，只有 \/link 選項是例外，它必須出現在最後。  編譯器會從 [CL 環境變數](../../build/reference/cl-environment-variables.md) 中所指定的選項開始，然後由左向右讀取命令列 — 依照所遭遇的先後順序處理命令檔。  每一選項都套用至命令列上的所有檔案。  如果 CL 碰到衝突的選項，它會採用最右邊的選項。  
  
## 請參閱  
 [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)