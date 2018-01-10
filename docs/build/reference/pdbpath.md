---
title: "-PDBPATH |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /pdbpath
dev_langs: C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0ccbcedbf9cdd376fa7d9bced5c9d49542cee9f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pdbpath"></a>/PDBPATH
```  
/PDBPATH[:VERBOSE] filename  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *filename*  
 您要尋找相符的.pdb 檔案的.dll 或.exe 檔案的名稱。  
  
 （選擇性） 的詳細資訊  
 報告所有嘗試已對找到.pdb 檔案的目錄。  
  
## <a name="remarks"></a>備註  
 / 搜尋電腦依循的相同路徑偵錯工具會搜尋.pdb 檔案，而且會將報告的如果有的話，.pdb 檔案會對應至指定的檔案 PDBPATH *filename*。  
  
 當使用 Visual Studio 偵錯工具時，您可能會遇到的問題，因為，偵錯工具使用不同版本的檔案進行偵錯的.pdb 檔案。  
  
 /PDBPATH 會搜尋.pdb 檔案，依照下列路徑：  
  
-   請檢查可執行檔所在的位置。  
  
-   檢查 PDB 寫入可執行檔的位置。 這通常是在映像已連結的位置。  
  
-   檢查 Visual Studio IDE 中設定在搜尋路徑。  
  
-   沿著路徑的 _NT_SYMBOL_PATH 和 _NT_ALT_SYMBOL_PATH 檢查環境變數。  
  
-   請檢查 Windows 目錄中。  
  
## <a name="see-also"></a>請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)   
 [/PDBALTPATH （使用替代 PDB 路徑）](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)