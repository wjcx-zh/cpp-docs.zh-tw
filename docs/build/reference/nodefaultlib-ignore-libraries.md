---
title: -NODEFAULTLIB （忽略程式庫） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
dev_langs:
- C++
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51caac10218d5f4d1787b2256875001ac32dc2b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375710"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (忽略程式庫)
```  
/NODEFAULTLIB[:library]   
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *程式庫*  
 您要連結器解析外部參考時，忽略程式庫。  
  
## <a name="remarks"></a>備註  
 /NODEFAULTLIB 選項會告訴連結器解析外部參考時所搜尋的程式庫的清單中移除一或多個預設程式庫。  
  
 若要建立的.obj 檔案，未包含預設程式庫的參考，請使用[/Zl （省略預設程式庫名稱）](../../build/reference/zl-omit-default-library-name.md)。  
  
 根據預設，/NODEFAULTLIB 從解析外部參考時，它會搜尋文件庫清單中移除所有預設程式庫。 選擇性*文件庫*參數可讓您解析外部參考時所搜尋的程式庫的清單中移除指定的程式庫或程式庫。 指定您想要排除的每個程式庫的一個 /NODEFAULTLIB 選項。  
  
 連結器解析外部定義的參考之您明確指定，則程式庫 /DEFAULTLIB 選項，以指定的預設程式庫中，然後在名為.obj 檔中的預設程式庫中，請搜尋第一次。  
  
 /NODEFAULTLIB:*文件庫*會覆寫[/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*文件庫*時相同*文件庫*中同時指定名稱。  
  
 如果您使用 /NODEFAULTLIB，比方說，若要建置您的程式不使用 C 執行階段程式庫中，您可能也使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)程式中指定的進入點 （函式）。 如需詳細資訊，請參閱 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**輸入**屬性頁。  
  
4.  選取**忽略所有預設程式庫**屬性指定您想要忽略中的程式庫的清單或**忽略特定程式庫**屬性。 **命令列**屬性頁面會顯示這些屬性所做的變更的效果。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)