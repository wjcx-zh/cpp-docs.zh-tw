---
title: "-RELEASE （設定總和檢查碼） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
dev_langs: C++
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b961c55f04b4f830de30c3d886d9aaee9ef71ea2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="release-set-the-checksum"></a>/RELEASE (設定總和檢查碼)
```  
/RELEASE  
```  
  
## <a name="remarks"></a>備註  
 /RELEASE 選項的.exe 檔的標頭中設定總和檢查碼。  
  
 作業系統的裝置驅動程式需要總和檢查碼。 設定總和檢查碼的發行版本的裝置驅動程式才能確保相容於未來的作業系統。  
  
 /RELEASE 選項預設設定時[了](../../build/reference/subsystem-specify-subsystem.md)指定選項。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**進階**屬性頁。  
  
4.  修改**設定總和檢查碼**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)