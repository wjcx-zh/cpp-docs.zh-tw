---
title: "-WINMD （產生 Windows 中繼資料） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7517ec459677659067e80930ee48caccf84d52f3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (產生 Windows 中繼資料)
啟用產生 Windows 執行階段中繼資料 (.winmd) 檔案。  
  
```  
/WINMD[:{NO|ONLY}]  
```  
  
## <a name="remarks"></a>備註  
 /WINMD  
 通用 Windows 平台應用程式的預設設定。 連結器會產生二進位可執行檔和.winmd 中繼資料檔案。  
  
 /WINMD:NO  
 連結器會產生只有二進位可執行檔，但不是.winmd 檔案。  
  
 / WINMD： 只有  
 連結器會產生只有.winmd 檔案，但不是二進位可執行檔。  
  
 根據預設，輸出檔名稱的形式`binaryname`.winmd。 若要指定不同的檔案名稱，請使用[/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)選項。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**Windows 中繼資料**屬性頁。  
  
4.  在**產生 Windows 中繼資料**下拉式清單方塊中，選取您想要的選項。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)