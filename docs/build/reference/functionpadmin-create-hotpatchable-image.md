---
title: "-FUNCTIONPADMIN （建立可線上修補的映像） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /functionpadmin
dev_langs: C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f286cf0cb595f640768f97c1619517f6000fd39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (建立可線上修補的影像)
準備映像進行 hotpatch。  
  
## <a name="syntax"></a>語法  
  
```  
/FUNCTIONPADMIN[:space]  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `space` (選擇性)  
 要加入的每個函式，開頭的填補數量 5、 6 或 16。  x86 映像需要五個位元組填補，x64 映像只需要 6 個位元組，並針對 Itanium 處理器系列建置的映像需要 16 個位元組填補，每個函式的開頭。  
  
 根據預設，編譯器會加入至映像，並根據映像的電腦類型的正確的空間量。  
  
 為了讓連結器產生的可線上修補的映像，.obj 檔中必須有已編譯[/hotpatch （建立可線上修補的影像）](../../build/reference/hotpatch-create-hotpatchable-image.md)。  
  
 當您編譯和連結 cl.exe，一次引動的映像**/hotpatch**意味著**/functionpadmin**。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)