---
title: "連結器工具警告 LNK4014 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4014"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4014"
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具警告 LNK4014
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到成員物件 "objectname"  
  
 LIB 在程式庫中找不到 `objectname`。  
  
 **\/REMOVE** 和 **\/EXTRACT** 選項必須要有將刪除或複製至檔案之成員物件的完整名稱。  完整名稱包含了原始目的檔的路徑。  如需參閱程式庫成員目的檔的完整名稱，請使用 DUMPBIN [\/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) 或 LIB [\/LIST](../../build/reference/managing-a-library.md)。