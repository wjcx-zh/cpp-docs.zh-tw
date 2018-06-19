---
title: -ALLOWBIND （阻止 DLL 繫結） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31968e27c46cb5ea220a4cfe19c36820c4cf8444
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369636"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (阻止 DLL 繫結)
```  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>備註  
 /ALLOWBIND:NO 在 DLL 的標頭中設定一個位元，向 Bind.exe 表示不允許繫結影像。 如果 DLL 已數位簽署，您便可能不想要繫結 DLL (繫結會使簽章無效)。  
  
 您可以編輯現有的 DLL，以使用 /ALLOWBIND 功能[/ALLOWBIND](../../build/reference/allowbind.md) EDITBIN 公用程式選項。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**，**連結器**，然後選取**命令列**。  
  
3.  輸入`/ALLOWBIND:NO`到**其他選項**。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [BindImage 函式](http://msdn.microsoft.com/library/windows/desktop/ms679278.aspx)   
 [BindImageEx 函式](http://msdn.microsoft.com/library/windows/desktop/ms679279.aspx)