---
title: "/PDBPATH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/pdbpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 檔案, 路徑"
  - "/PDBPATH dumpbin 選項"
  - "PDB 檔案, 路徑"
  - "PDBPATH dumpbin 選項"
  - "-PDBPATH dumpbin 選項"
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /PDBPATH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBPATH[:VERBOSE] filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 您要尋找相符的 .pdb 檔之 .dll 或 .exe 檔的名稱。  
  
 VERBOSE \(選擇項\)  
 報告已在其中嘗試尋找 .pdb 檔的所有目錄。  
  
## 備註  
 \/PDBPATH 會根據偵錯工具搜尋 .pdb 檔的相同路徑來搜尋您的電腦，並回報對應於 *filename* 指定之檔案的 .pdb 檔 \(如果有的話\)。  
  
 在使用 Visual Studio 偵錯工具時，由於偵錯工具使用的 .pdb 檔和您偵錯的檔案版本不同，因此您可能會遇到問題。  
  
 \/PDBPATH 將會根據下列路徑搜尋 .pdb 檔：  
  
-   檢查可執行檔所在的位置。  
  
-   檢查寫入可執行檔之 PDB 的位置。  這個位置通常是影像檔連結時的位置。  
  
-   根據 Visual Studio IDE 中設定的搜尋路徑檢查。  
  
-   根據 \_NT\_SYMBOL\_PATH 和 \_NT\_ALT\_SYMBOL\_PATH 環境變數 \(Environment Variable\) 中的路徑檢查。  
  
-   檢查 Windows 目錄。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)   
 [\/PDBALTPATH \(使用替代 PDB 路徑\)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)