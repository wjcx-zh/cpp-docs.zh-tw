---
title: "NMAKE 嚴重錯誤 U1056 | Microsoft Docs"
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
  - "U1056"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1056"
ms.assetid: da855728-b69e-413c-83ed-df912126215e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1056
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到命令處理器  
  
 在 **COMSPEC** 或 **PATH** 環境變數指定的路徑中找不到命令處理器。  
  
 執行命令時，NMAKE 使用 COMMAND.COM 或 CMD.EXE 做為命令處理器。  它會先在 **COMSPEC** 設定的路徑中尋找命令處理器，  如果 **COMSPEC** 不存在，NMAKE 將搜尋 **PATH** 中指定的目錄。