---
title: "嚴重錯誤 C1902 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1902"
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1902
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

程式資料庫管理員不相符；請檢查您的安裝  
  
 程式資料庫檔 \(.pdb\) 建立時所使用的 mspdb*XX*.dll 版本，比系統上找到的編譯器還新。  這個錯誤通常表示找不到 mspdbsrv.exe 或 mspdbcore.dll，或其版本與 mspdb*XX*.dll 的版本不同 \(mspdb*XX*.dll 檔名中的 *XX* 替代符號會隨著每個產品發行而變更。  例如，在 [!INCLUDE[vsprvslong](../../error-messages/compiler-errors-1/includes/vsprvslong_md.md)] 中檔名為 mspdb80.dll\)。  
  
 請確定系統上所安裝的 mspdbsrv.exe、mspdbcore.dll 和 mspdb*XX*.dll 版本相符。  請確定沒有將不相符的版本，複製到目標平台中包含編譯器和連結工具的目錄。  舉例來說，您可能複製過這些檔案，但卻沒有跟著設定 **PATH** 環境變數，而從命令提示字元叫用編譯器或連結工具。