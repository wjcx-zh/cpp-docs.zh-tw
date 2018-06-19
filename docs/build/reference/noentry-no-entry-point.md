---
title: -NOENTRY （沒有進入點） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
dev_langs:
- C++
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44f35c995a0c839fdc0d4ccf3d286e332793cf70
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374033"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (沒有進入點)
```  
/NOENTRY  
```  
  
## <a name="remarks"></a>備註  
 必須有 /NOENTRY 選項才能建立不包含可執行程式碼的僅含資源的 DLL。 如需詳細資訊，請參閱[建立 Resource-Only DLL](../../build/creating-a-resource-only-dll.md)。  
  
 使用此選項可防止 LINK 將 `_main` 的參考連結到 DLL 中。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**進階**屬性頁。  
  
4.  修改**沒有進入點**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [建立資源專用 DLL](../../build/creating-a-resource-only-dll.md)   
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)