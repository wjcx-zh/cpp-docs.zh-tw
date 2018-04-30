---
title: VC + + 目錄屬性頁 |Microsoft 文件
ms.custom: ''
ms.date: 04/26/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.tgt_pltfrm: ''
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
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8931ecd34acfa1aba0287274acb45d362bdec2cf
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="vc-directories-property-page-windows"></a>VC + + 目錄屬性頁 (Windows)

使用此屬性頁面來告知 Visual Studio 建置目前選取的專案時使用的目錄。 若要在方案中設定多個專案的目錄，請使用自訂的屬性工作表中所述[建立可重複使用的屬性設定](working-with-project-properties.md#bkmkPropertySheets)。

此頁面的 Linux 版本，請參閱[VC + + 目錄 （Linux c + +）](../linux/prop-pages/directories-linux.md)。   

若要存取**VC + + 目錄**屬性頁：

1. 如果**方案總管 中**看不到視窗，然後在主功能表上選擇 **檢視** > **方案總管 中**。
1. 以滑鼠右鍵按一下專案節點 （而不是最上層方案），然後選擇 **屬性**。
1. 在左窗格中**屬性頁**對話方塊中，選取**組態屬性** > **VC + + 目錄**。  

VC + + 目錄屬性會套用至專案，而不是最上層方案節點。 如果您沒有看到**VC + + 目錄**下**組態屬性**，c + + 中選取專案節點**方案總管 中**視窗： 

![選取專案節點](media/vcppdir.png "選取專案節點，請參閱 VC + + 目錄屬性")

請注意， **VC + + 目錄**跨平台專案屬性頁看起來不同。 Linux c + + 專案的特定資訊，請參閱[VC + + 目錄 （Linux c + +）](../linux/prop-pages/directories-linux.md)。 
 
如果您不熟悉*專案屬性*在 Visual Studio 中，您也許會很有幫助第一次讀取[使用專案屬性](working-with-project-properties.md)。 
 
預設設定**VC + + 目錄**屬性取決於專案類型。 對於傳統型專案它們包含 c + + 工具的位置特定的平台工具組和 Windows SDK 的位置。 您可以變更**平台工具組**和**Windows SDK 版本**上**組態屬性** > **一般**頁面。 

若要檢視的任何目錄的值：

1. 選取其中一個屬性中**VC + + 目錄**頁面。 例如，選擇**程式庫目錄**。
1. 選擇向下鍵按鈕，屬性值欄位的結尾。
1. 在下拉式功能表中，選擇 **編輯**。

![編輯程式庫目錄](media/vcppdir_libdir_edit.png "對話方塊，以編輯的程式庫路徑")

現在，您會看到一個對話方塊，像這樣： 

![顯示程式庫目錄](media/vcppdir_libdir.png "對話方塊來新增或移除程式庫路徑")

您可以使用此對話方塊來檢視目前的目錄。 不過，如果您想要變更或新增一個目錄，最好是使用**屬性管理員**建立屬性工作表，或修改預設使用者屬性工作表。 如需詳細資訊，請參閱[建立可重複使用的屬性設定](working-with-project-properties.md#bkmkPropertySheets)。

如上所示，許多的繼承路徑會提供為巨集。  若要檢查巨集的目前值，請選擇**巨集**對話方塊右下角中的按鈕。 請注意，許多巨集就會取決於組態類型。 偵錯組建中的巨集可能會評估為相同的巨集的發行組建中不同的路徑。 

您可以搜尋部分或完整比對，在編輯方塊中。 下圖顯示包含字串"WindowsSDK"的所有巨集，它也會顯示目前的路徑巨集判斷值為：

![請參閱巨集值](media/vcppdir_libdir_macros.png "對話方塊，以編輯巨集")

注意： 當您輸入時，會填入此清單。 請勿按**Enter**。

如需有關巨集和為什麼您應該而非硬式編碼路徑，請盡可能使用它們的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros)。 

如需常用巨集的清單，請參閱[建置命令和屬性的一般巨集](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties)。

您可以定義自己的巨集有兩種：
-   開發人員命令提示字元中設定環境變數。 所有環境變數會被都視為 MSBuild 屬性巨集。
-   由於.props 檔案中定義使用者巨集。 如需詳細資訊，請參閱[屬性頁面巨集](working-with-project-properties.md#bkmkPropertiesVersusMacros)。 

如需詳細資訊，請參閱部落格文章： [VC + + 目錄](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)，[繼承屬性和屬性工作表](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)，和[Visual Studio 2010 c + + 專案升級指南](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)。  
  
## <a name="directory-types"></a>目錄類型

您也可以指定其他目錄，如下所示。  
  
**可執行檔目錄**<br/>
要在其中搜尋可執行檔的目錄。 對應至**路徑**環境變數。

**Include 目錄**<br/>
要在其中搜尋原始程式碼中所參考之 Include 檔案的目錄。 對應至**INCLUDE**環境變數。

**參考目錄**<br/>
 要在其中搜尋組件和模組 （中繼資料） 檔案的原始程式碼中所參考目錄[#using](../preprocessor/hash-using-directive-cpp.md)指示詞。 對應至**LIBPATH**環境變數。

**程式庫目錄**<br/>
要在其中搜尋程式庫 (.lib) 檔案的目錄；包括執行階段程式庫。 對應至**LIB**環境變數。 此設定不適用於.obj 檔案，若要連結.obj 檔案，在**組態屬性** > **連結器** > **一般**屬性頁上，選取**其他程式庫相依性**，然後指定檔案的相對路徑。 如需詳細資訊，請參閱[連結器屬性頁](../ide/linker-property-pages.md)。

**程式庫 WinRT 目錄**<br/>
要搜尋的 WinRT 程式庫檔案的目錄用於通用 Windows 平台 (UWP) 應用程式。 

**來源目錄**<br/>
要在其中搜尋用於 IntelliSense 之來源檔的目錄。

**排除目錄**<br/>
之前每次編譯，Visual Studio 會查詢上所有檔案，以判斷是否任何已修改先前編譯後的時間戳記。 如果您的專案具有大型穩定的程式庫，您可以潛在加快建置時間的時間戳記檢查從排除這些目錄。

## <a name="sharing-the-settings"></a>共用設定

您可以與其他使用者或多部電腦共用專案屬性。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。
