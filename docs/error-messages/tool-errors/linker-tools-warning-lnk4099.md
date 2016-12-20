---
title: "連結器工具警告 LNK4099 | Microsoft Docs"
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
  - "LNK4099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4099"
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到 PDB 'filename' \(有 'object\/library' 或位於 'path'\)；當做沒有偵錯資訊，連結物件  
  
 連結器無法找到您的 .pdb 檔。  將它複製到包含 `object/library` 的目錄中。  
  
 若要尋找與目的檔相關聯的 .pdb 檔名稱：  
  
1.  使用 [lib](../../build/reference/lib-reference.md) **\/extract:**`objectname`**.obj** `xyz`**.lib** 從程式庫抽取目的檔。  
  
2.  以 **dumpbin \/section:.debug$T \/rawdata** `objectname`**.obj** 檢查至 .pdb 檔的路徑。  
  
 您也可以使用 [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) 編譯，就不需要使用 pdb，或是如果您沒有所要連結物件的 .pdb 檔，就移除 [\/DEBUG](../../build/reference/debug-generate-debug-info.md) 連結器選項。