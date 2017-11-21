---
title: "對齊 （區段對齊） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs: C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.assetid: f2f8ac24-e90e-4bea-8205-f2960a3b1740
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e620719d5a69c333a45664fba5967a740224d4d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="align-section-alignment"></a>/ALIGN (區段對齊)
```  
/ALIGN[:number]  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `number`  
 對齊值。  
  
## <a name="remarks"></a>備註  
 /ALIGN 選項會指定程式的線性位址空間中的每個區段的對齊方式。 `number`引數是以位元組為單位，且必須是 2 的乘冪。 預設值是 4 K (4096)。 連結器會發出警告，就會產生無效的影像對齊方式。  
  
 除非您正在撰寫的應用程式，例如裝置驅動程式，您應該不需要修改對齊方式。  
  
 可修改的特定區段的對齊參數與對齊[/section](../../build/reference/section-specify-section-attributes.md)選項。  
  
 您指定的對齊值不得小於最大區段記憶體對齊。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)