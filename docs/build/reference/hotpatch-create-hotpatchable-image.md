---
title: -hotpatch （建立可線上修補的映像） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad7ab4e6450d33923b728f20c8a35185edd2b05e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (建立可線上修補的影像)
準備映像進行 Hotpatch。  
  
## <a name="syntax"></a>語法  
  
```  
/hotpatch  
```  
  
## <a name="remarks"></a>備註  
 當**/hotpatch**會使用在編譯中，編譯器會確保每個函式的第一個指令是至少兩個位元組，這是 hotpatch 所需要的。  
  
 若要完成準備進行映像可線上修補，在使用後**/hotpatch**進行編譯時，您必須使用[/FUNCTIONPADMIN （建立可線上修補的影像）](../../build/reference/functionpadmin-create-hotpatchable-image.md)連結。 當您編譯和連結映像使用一個引動過程 cl.exe， **/hotpatch**意味著**/functionpadmin**。  
  
 因為指令永遠是兩個位元組或更大的 ARM 架構上，而且因為 x64 編譯永遠會被視為一樣**/hotpatch**已指定，您不必指定**/hotpatch**時您為這些目標; 編譯不過，您必須仍使用連結**/functionpadmin**以建立可進行 hotpatch 的映像。 **/Hotpatch**編譯器選項只會影響 x86 編譯。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  加入至編譯器選項**其他選項**方塊。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="guidance"></a>指引  
 更新管理的詳細資訊，請參閱 < 安全性指引的更新管理 >，網址[http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx)。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)