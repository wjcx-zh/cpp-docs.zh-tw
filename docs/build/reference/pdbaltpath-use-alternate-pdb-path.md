---
title: -PDBALTPATH （使用替代 PDB 路徑） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbaltpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dec06c3d6a8a981a059f173700e716431acc53a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374085"
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (使用替代 PDB 路徑)
```  
/PDBALTPATH:pdb_file_name  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *pdb_file_name*  
 .pdb 檔案的路徑及檔案名稱。  
  
## <a name="remarks"></a>備註  
 使用此選項，可以提供已編譯二進位檔案中程式資料庫 (.pdb) 檔的替代位置。 一般而言，連結器會在其所產生的二進位檔中，記錄 .pdb 檔案的位置。 您可以使用此選項，來提供 .pdb 檔案的不同路徑及檔案名稱。 隨附於 /PDBALTPATH 的資訊不會變更實際 .pdb 檔案的位置或名稱；它會變更連結器寫入二進位檔的資訊。 這可讓您提供與建置電腦檔案結果無關的路徑。 此選項的兩個常用用法是提供網路路徑或沒有路徑資訊的檔案。  
  
 值*pdb_file_name*可以是任意字串、 環境變數，或 **_PDB %**。 連結器會展開環境變數，如 **%systemroot%**，其值。 連結器會定義環境變數 **_PDB %** 和 **_EXT %**。 **_PDB %** 會展開至實際.pdb 檔案不含任何路徑資訊的檔案名稱和 **_EXT %** 是產生可執行檔的副檔名。  
  
## <a name="see-also"></a>另請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)   
 [/PDBPATH](../../build/reference/pdbpath.md)