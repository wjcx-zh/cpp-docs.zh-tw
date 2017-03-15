---
title: "/PDBALTPATH (使用替代 PDB 路徑) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/pdbaltpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 檔案, 路徑"
  - "/PDBALTPATH dumpbin 選項"
  - "PDB 檔案, 路徑"
  - "PDBALTPATH dumpbin 選項"
  - "-PDBALTPATH dumpbin 選項"
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /PDBALTPATH (使用替代 PDB 路徑)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBALTPATH:pdb_file_name  
```  
  
## 備註  
 其中：  
  
 *pdb\_file\_name*  
 .pdb 檔案的路徑及檔案名稱。  
  
## 備註  
 使用此選項，可以提供已編譯二進位檔案中程式資料庫 \(.pdb\) 檔的替代位置。  一般而言，連結器會在其所產生的二進位檔中，記錄 .pdb 檔案的位置。  您可以使用此選項，來提供 .pdb 檔案的不同路徑及檔案名稱。  隨附於 \/PDBALTPATH 的資訊不會變更實際 .pdb 檔案的位置或名稱；它會變更連結器寫入二進位檔的資訊。  這可讓您提供與建置電腦檔案結果無關的路徑。  此選項的兩個常用用法是提供網路路徑或沒有路徑資訊的檔案。  
  
 *pdb\_file\_name* 的值可以是任意字串、環境變數或 **%\_PDB%**。  連結器會展開環境變數 \(如 **%SystemRoot%**\) 至其值。  連結器會定義環境變數 **%\_PDB%** 及 **%\_EXT%**。  **%\_PDB%** 會展開至實際 .pdb 的檔案名稱而不帶任何路徑資訊，而 **%\_EXT%** 是所產生可執行檔的副檔名。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)   
 [\/PDBPATH](../../build/reference/pdbpath.md)