---
title: "檔名巨集 | Microsoft Docs"
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
  - "NMAKE 中的檔名巨集"
  - "巨集, NMAKE"
  - "NMAKE 程式, 檔名巨集"
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 檔名巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檔名巨集會預先定義成相依性中所指定的檔名 \(並非在磁碟中的完整檔名規格\)。  叫用時不需要將這些巨集放在括號之中，只需指定 $，如下所示。  
  
|巨集|意義|  
|--------|--------|  
|**$@**|目前目標的完整名稱 \(路徑、主檔名、副檔名\)，如目前所指定的。|  
|**$$@**|目前目標的完整名稱 \(路徑、主檔名、副檔名\)，如目前所指定的。  只在當做相依性中的相依才有效。|  
|**$\***|目前目標的路徑和主檔名，不包含副檔名。|  
|**$\*\***|目前目標的所有相依性。|  
|**$?**|具有比目前目標較晚之時間戳記的所有相依性。|  
|**$\<**|具有比目前目標較晚之時間戳記的相依性檔案。  只有在介面規則的命令中才有效。|  
  
 若要指定部分預先定義的檔名巨集，請附加巨集修飾詞，並以括號括住修飾詞巨集。  
  
|修飾詞|產生的檔名部分|  
|---------|-------------|  
|**D**|磁碟加目錄。|  
|**B**|主檔名。|  
|**F**|主檔名加副檔名。|  
|**R**|磁碟加目錄加主檔名。|  
  
## 請參閱  
 [特殊的 NMAKE 巨集](../build/special-nmake-macros.md)