---
title: "連結器工具錯誤 LNK1188 | Microsoft Docs"
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
  - "LNK1188"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1188"
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1188
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

BADFIXUPSECTION:: 修復目標 'symbol' 無效；可能是區段的長度為零  
  
 在 VxD 連結期間，重新配置的目標沒有區段。  在 LINK386 \(舊版\) 中，OMF GROUP 記錄 \(由 MASM GROUP 指示詞所產生\) 可能會被用來結合長度為零的區段和另一個長度不為零的區段。  COFF 格式不支援 GROUP 指示詞與長度為零的區段。  當 LINK 自動將這種型別的 OMF 目的檔轉換成 COFF 時，便可能會發生這種錯誤。