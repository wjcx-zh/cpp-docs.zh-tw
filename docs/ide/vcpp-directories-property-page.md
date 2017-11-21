---
title: "VC + + 目錄屬性頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
dev_langs: C++
helpviewer_keywords: VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30a54b1d90585e6433f059acf30991ca53948d60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="vc-directories-property-page"></a>VC++ 目錄屬性頁
指定您要 Visual Studio 用來建置專案的目錄。 若要存取此屬性頁面上，在**方案總管] 中**，開啟專案的捷徑功能表並選擇**屬性**，然後在左窗格的**屬性頁**對話方塊方塊中，展開 [**組態屬性**選取**VC + + 目錄**。  
  
 當您使用 Visual Studio 建立專案時，將會繼承特定目錄。 其中許多值會以巨集呈現。 若要檢查巨集，在右窗格中的目前值**VC + + 目錄**頁面上，選取一個資料列 — 比方說， **Include 目錄**— 選擇右邊的向下鍵按鈕，選擇  **編輯**，然後在出現的對話方塊中，選擇 **巨集** 按鈕。 如需詳細資訊，請參閱部落格文章： [VC + + 目錄](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)，[繼承屬性和屬性工作表](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)，和[Visual Studio 2010 c + + 專案升級指南](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)。  
  
## <a name="directory-types"></a>目錄類型  
 您也可以指定其他目錄，如下所示。  
  
 **可執行檔目錄**  
 要在其中搜尋可執行檔的目錄。 對應至**路徑**環境變數。  
  
 **Include 目錄**  
 要在其中搜尋原始程式碼中所參考之 Include 檔案的目錄。 對應至**INCLUDE**環境變數。  
  
 **參考目錄**  
 要在其中搜尋組件和模組 （中繼資料） 檔案的原始程式碼中所參考目錄[#using](../preprocessor/hash-using-directive-cpp.md)指示詞。 對應至**LIBPATH**環境變數。  
  
 **程式庫目錄**  
 要在其中搜尋程式庫 (.lib) 檔案的目錄；包括執行階段程式庫。 對應至**LIB**環境變數。 此設定不適用於.obj 檔案，若要連結.obj 檔案，在[連結器](../ide/linker-property-pages.md)**一般**屬性頁上，選取**其他程式庫相依性**，然後指定檔案的相對路徑。  
  
 **來源目錄**  
 要在其中搜尋用於 IntelliSense 之來源檔的目錄。  
  
 **排除目錄**  
 檢查組建相依性時不會搜尋的目錄。  
  
#### <a name="to-specify-or-modify-directory-settings"></a>指定或修改目錄設定  
  
1.  在**方案總管 中**，開啟您想要變更，然後選擇專案的捷徑功能表**屬性**。  
  
2.  在左窗格中**屬性頁**對話方塊方塊中，展開 **組態屬性**，然後選取  **VC + + 目錄**。  
  
3.  若要修改其中一個目錄清單中，選取它，選擇向下鍵按鈕，在右側，，然後選擇**編輯**。  
  
     在顯示的對話方塊中，您可以加入或移除值，因此，您可以值出現的順序重新排列。 您也可以變更是否專案會繼承任何設定，以選取或清除**從父代或專案預設值繼承**。  
  
## <a name="sharing-the-settings"></a>共用設定  
 您可以與其他使用者或多部電腦共用專案屬性。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
