---
title: -Ge （啟用堆疊探查） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ge
dev_langs:
- C++
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce8b049426eb403e4bc41e842fe1ff2db1617dfc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375294"
---
# <a name="ge-enable-stack-probes"></a>/Ge (啟用堆疊探查)
啟動堆疊探查每個函式呼叫所需要的儲存體的本機變數。  
  
## <a name="syntax"></a>語法  
  
```  
/Ge  
```  
  
## <a name="remarks"></a>備註  
 這項機制是很有用，如果您重新撰寫功能的堆疊探查。 建議您改用[/Gh (啟用 _penter 攔截函式)](../../build/reference/gh-enable-penter-hook-function.md)而不是重寫堆疊探查。  
  
 [/Gs （控制堆疊檢查呼叫）](../../build/reference/gs-control-stack-checking-calls.md)具有相同的效果。  
  
 **/Ge**是已被取代; 從 Visual Studio 2005 中，編譯器會自動產生堆疊檢查。 如需已被取代的編譯器選項的清單，請參閱**已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)