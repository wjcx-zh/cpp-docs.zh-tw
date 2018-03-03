---
title: "VC + + 目錄屬性頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
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
dev_langs:
- C++
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c92a97ccd28a1bc7d1fae518cf499b45d339dae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vc-directories-property-page-windows"></a>VC + + 目錄屬性頁 (Windows)

使用此屬性頁面來告知 Visual Studio 建置目前選取的專案時使用的目錄。 若要在方案中設定多個專案的目錄，請使用自訂的屬性工作表中所述[建立可重複使用的屬性設定](working-with-project-properties.md#bkmkPropertySheets)。

此頁面的 Linux 版本，請參閱[VC + + 目錄 （Linux c + +）](../linux/prop-pages/directories-linux.md)。   

若要存取**VC + + 目錄**屬性頁：

1. 從主要功能表選擇 [**檢視 |方案總管]**
1. 以滑鼠右鍵按一下專案節點 （而不是最上層方案），然後選擇 **屬性**
1. 在左窗格中**屬性頁**對話方塊方塊中，展開 **組態屬性**選取**VC + + 目錄**。  

VC + + 目錄屬性會套用至專案，而不是最上層方案節點：

![選取專案節點](media/vcppdir.png "選取專案節點，請參閱 VC + + 目錄屬性")

如果您沒有看到屬性頁上，確定您有中選取專案節點**方案總管 中**。 請注意， **VC + + 目錄**跨平台專案屬性頁看起來不同。 對於非 Windows 的專案，請參閱[VC + + 目錄 （Linux c + +）](../linux/prop-pages/directories-linux.md)或。 
 
如果您不熟悉*專案屬性*在 Visual Studio 中，您也許會很有幫助第一次讀取[使用專案屬性](working-with-project-properties.md)。 
 
VC + + 目錄的預設設定是根據專案類型而定。 對於傳統型專案它們包含特定的平台工具組的 VC + + 工具位置和 Windows SDK 的位置。 您可以變更**平台工具組**和**Windows SDK 版本**上**組態屬性 – 一般**頁面。 若要檢視的任何目錄的值：

1. 在右窗格中**VC + + 目錄**頁面上，選取一個資料列。 例如，**程式庫目錄**
1. 選擇右邊的向下箭頭按鈕
1. 選擇**編輯**。

![編輯程式庫目錄](media/vcppdir_libdir_edit.png "對話方塊，以編輯的程式庫路徑")

現在，您會看到一個對話方塊，像這樣： 

![顯示程式庫目錄](media/vcppdir_libdir.png "對話方塊來新增或移除程式庫路徑")

您可以使用此對話方塊來檢視目前的目錄。 不過，如果您想要變更或新增一個目錄，最好是使用**屬性管理員**建立屬性工作表，或修改預設使用者屬性工作表。 如需詳細資訊，請參閱[建立可重複使用的屬性設定](working-with-project-properties.md#bkmkPropertySheets)。

如上所示，許多的繼承路徑會提供為巨集。  若要檢查巨集的目前值，請選擇**巨集**對話方塊右下角中的按鈕。 請注意，許多巨集就會取決於組態類型。 偵錯組建中的巨集可能會評估為相同的巨集的發行組建中不同的路徑。 

您可以搜尋部分或完整比對，在編輯方塊中。 下圖顯示包含字串"WindowsSDK"的所有巨集，它也會顯示目前的路徑巨集判斷值為：

![請參閱巨集值](media/vcppdir_libdir_macros.png "對話方塊，以編輯巨集")

注意： 當您輸入時，將會填入清單。 請勿按**Enter**。

如需有關巨集和為什麼您應該而非硬式編碼路徑，請盡可能使用它們的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros)。 

如需常用巨集的清單，請參閱[建置命令和屬性的一般巨集](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties)。

您可以定義自己的巨集有兩種：
-   開發人員命令提示字元中設定環境變數。 所有環境變數會被都視為 MSBuild 屬性巨集。
-   由於.props 檔案中定義使用者巨集。 如需詳細資訊，請參閱[屬性頁面巨集](working-with-project-properties.md#bkmkPropertiesVersusMacros)。 

如需詳細資訊，請參閱部落格文章： [VC + + 目錄](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)，[繼承屬性和屬性工作表](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)，和[Visual Studio 2010 c + + 專案升級指南](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)。  
  
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

## <a name="sharing-the-settings"></a>共用設定

您可以與其他使用者或多部電腦共用專案屬性。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。
