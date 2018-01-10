---
title: "-PDB （使用程式資料庫） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
dev_langs: C++
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b8b255e88a199397463d26d408d425234571552
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pdb-use-program-database"></a>/PDB (使用程式資料庫)
```  
/PDB:filename  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *filename*  
 使用者指定連結器建立的程式資料庫 (PDB) 名稱。 它會取代預設的名稱。  
  
## <a name="remarks"></a>備註  
 根據預設，當[偵錯](../../build/reference/debug-generate-debug-info.md)指定，則連結器會建立保留偵錯資訊的程式資料庫 (PDB)。 PDB 的預設檔案名稱具有基底名稱的程式和副檔名.pdb。  
  
 使用 /PDB:*filename*指定 PDB 檔的名稱。 如果未指定 /DEBUG，則會忽略 /PDB 選項。  
  
 PDB 檔案可以是 2 GB。  
  
 如需詳細資訊，請參閱[.pdb 檔做為連結器輸入](../../build/reference/dot-pdb-files-as-linker-input.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**偵錯**屬性頁。  
  
4.  修改**產生程式資料庫檔**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)