---
title: -對應 （產生對應檔） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10f4b23cf8f1c05fb8bd196dc9a6cd54971b1572
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374667"
---
# <a name="map-generate-mapfile"></a>/MAP (產生對應檔)
```  
/MAP[:filename]  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *filename*  
 指定使用者定義的對應名稱。 它會取代預設的名稱。  
  
## <a name="remarks"></a>備註  
 /MAP 選項會告訴連結器，以建立對應檔。  
  
 根據預設，連結器會與基底名稱的程式及延伸.map 命名對應檔。 選擇性*filename*可讓您覆寫對應檔的預設名稱。  
  
 對應檔是文字檔，其中包含程式所連結的下列資訊：  
  
-   模組名稱，這就是基底檔案名稱  
  
-   程式檔案標頭 （不是從檔案系統） 的時間戳記  
  
-   在程式中，具有每個群組的起始位址的群組清單 (做為*區段*:*位移*)，長度、 群組名稱和類別  
  
-   公用符號，但每個地址的清單 (做為*區段*:*位移*)，符號名稱、 一般的地址和符號位置定義的.obj 檔案  
  
-   進入點 (做為*區段*:*位移*)  
  
 [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)選項會指定要包含在對應檔中的其他資訊。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**偵錯**屬性頁。  
  
4.  修改**產生對應檔**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)