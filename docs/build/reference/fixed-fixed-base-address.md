---
title: -FIXED （固定的基底位址） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08b1193b7cfe58aed45e4feec598a49227eafc87
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="fixed-fixed-base-address"></a>/FIXED (固定基底位址)
```  
/FIXED[:NO]  
```  
  
## <a name="remarks"></a>備註  
 告知作業系統只載入位於慣用基底位址的程式。 如果無法使用慣用的基底位址，作業系統就不會載入檔案。 如需詳細資訊，請參閱 [/BASE (基底位址)](../../build/reference/base-base-address.md)。  
  
 /FIXED:NO 是 DLL 的預設值，而 /FIXED 則是其他專案類型的預設值。  
  
 /Fixed 則指定時，則連結不會產生重新配置區段的程式。 在執行階段時，如果作業系統無法在指定的位址載入程式，它便會發出錯誤訊息而且不會載入程式。  
  
 指定在程式中產生重新配置區段的 /fixed: no。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  輸入選項名稱，並在設定**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)