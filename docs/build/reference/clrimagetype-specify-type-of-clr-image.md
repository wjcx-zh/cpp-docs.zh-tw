---
title: "-CLRIMAGETYPE （指定 CLR 映像類型） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs:
- C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8de8abb1602499cea0b1412d4199ea54b3bf601
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (指定 CLR 映像類型)
```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## <a name="remarks"></a>備註  
 連結器接受原生物件，而且也 MSIL 物件都會使用編譯[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。 **/Clr: pure**和**/clr: safe**編譯器選項在 Visual Studio 2015 中已被取代。 在相同組建中傳遞混合物件時，所產生輸出檔案的可驗證性將預設為同等於輸入模組最低層級的可驗證性。 例如，如果您傳遞原生映像和混合的模式映像 (使用編譯的**/clr**)，產生的映像將會以混合的模式映像。  
  
 如果您有需要，您可使用 /CLRIMAGETYPE 來指定較低層級的可驗證性。  
  
 如需如何判斷檔案之 CLR 映像類型的資訊，請參閱 [/CLRHEADER](../../build/reference/clrheader.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**進階**屬性頁。  
  
5.  修改**CLR 映像類型**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)