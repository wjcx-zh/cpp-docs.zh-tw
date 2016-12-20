---
title: "命令列錯誤 D8037 | Microsoft Docs"
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
  - "D8037"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8037"
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令列錯誤 D8037
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法建立暫存 IL 檔案; 清除舊 IL 檔案的暫存目錄  
  
 空間不足，無法建立暫存的編譯器中繼檔案。  若要補救這個錯誤，請移除 **TMP** 環境變數所指定目錄中的任何舊 MSIL 檔。  這些檔案的格式為 \_CL\_hhhhhhhh.ss，其中 h 代表隨機的十六進位數字，而 ss 代表 IL 檔案的類型。  此外，務必用最新的作業系統修補檔更新您的電腦。  
  
## 請參閱  
 [命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [編譯器選項](../../build/reference/compiler-options.md)