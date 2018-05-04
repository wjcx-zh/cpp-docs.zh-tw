---
title: -WINMDKEYFILE (指定 winmd 金鑰檔) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
dev_langs:
- C++
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba19ddd7a9ca1c313cc9f72e6cc8b77b4b565ceb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (指定 winmd 金鑰檔)
指定的金鑰或金鑰組簽署 Windows 執行階段中繼資料 (.winmd) 檔案。  
  
```  
/WINMDKEYFILE:filename  
```  
  
## <a name="remarks"></a>備註  
 類似於[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) .winmd 檔案上套用的連結器選項。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**Windows 中繼資料**屬性頁。  
  
4.  在**Windows 中繼資料金鑰檔**方塊中，輸入檔案位置。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)