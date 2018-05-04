---
title: -LARGEADDRESSAWARE （處理大型記憶體位址） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
dev_langs:
- C++
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f81424c49c5d67713cf478f69701c52504cfa8c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (處理大型記憶體位址)
```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## <a name="remarks"></a>備註  
 /LARGEADDRESSAWARE 選項會告訴連結器的應用程式能夠處理 2 gb 以上的位址。 在 64 位元編譯器中，預設會啟用此選項。 在 32 位元編譯器中，如果連結器列未否則指定 /LARGEADDRESSAWARE，會啟用 /largeaddressaware: no。  
  
 如果應用程式連結到 /LARGEADDRESSAWARE，DUMPBIN [/HEADERS](../../build/reference/headers.md)會顯示說明該狀況的資訊。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**系統**屬性頁。  
  
4.  修改**啟用大型記憶體**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)