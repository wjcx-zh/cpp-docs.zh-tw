---
title: -WINMDFILE (指定 winmd 檔案) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eaf1bfc805db568a012c28d66361bbd99745a95
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (指定 winmd 檔案)
指定所產生的 Windows 執行階段中繼資料 (.winmd) 輸出檔的檔案名稱[/WINMD](../../build/reference/winmd-generate-windows-metadata.md)連結器選項。  
  
```  
/WINMDFILE:filename  
```  
  
## <a name="remarks"></a>備註  
 使用 `filename` 中指定的值來覆寫預設的 .winmd 檔案名稱 (`binaryname` .winmd)。 請注意，您無法附加".winmd 」 到`filename`。  如果多個值會列在 **/WINMDFILE**命令列的最後一個的優先順序。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**Windows 中繼資料**屬性頁。  
  
4.  在**Windows 中繼資料檔案**方塊中，輸入檔案位置。  
  
## <a name="see-also"></a>另請參閱  
 [/WINMD （產生 Windows 中繼資料）](../../build/reference/winmd-generate-windows-metadata.md)   
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)