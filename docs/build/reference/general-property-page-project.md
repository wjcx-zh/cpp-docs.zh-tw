---
title: 一般屬性頁 (專案)
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
ms.openlocfilehash: eb172e7bd76816458a0efff7b053d136f52076ab
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166754"
---
# <a name="general-property-page-project"></a>一般屬性頁 (專案)

::: moniker range=">=vs-2019"

本主題適用于 Windows 的 Visual Studio 專案。 針對 Linux 專案，請[參閱C++ Linux 屬性頁參考](../../linux/prop-pages-linux.md)。 如需 CMake 專案，請參閱[在 Visual Studio 中 CMake 專案](../cmake-projects-in-visual-studio.md)。 若為 Android 專案，請參閱[一般專案屬性C++（Android）](/cpp/cross-platform/general-android-prop-page)。 針對 Android Makefile 專案，請參閱[一般專案屬性（ C++ Android makefile）](/cpp/cross-platform/general-makefile-android-prop-page)

當您以滑鼠右鍵按一下方案總管中的專案節點，然後選取 [**屬性**] 時，左窗格中 [設定**屬性**] 節點底下的 [**一般**] 屬性頁會顯示這些屬性：

- **輸出目錄**

   指定連結器等工具將放置在建置程序期間建立之所有最終輸出檔案的目錄。 這通常包括連結器、管理員或 BSCMake 之類的工具的輸出。 根據預設，此屬性是巨集 $(SolutionDir)$(Configuration)\ 所指定的目錄。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>。

- **中繼目錄**

   指定編譯器等工具將放置在建置程序期間建立之所有中繼檔案的目錄。 這通常包括 C/C++ 編譯器、MIDL 及資源編譯器等工具的輸出。 根據預設，此屬性是巨集 $(Configuration)\ 所指定的目錄。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>。

- **目標名稱**

   指定此專案會產生的檔案名稱。 根據預設，此屬性是巨集 $(ProjectName) 所指定的檔名。

- **組態類型**

  有數個組態類型可供選擇：

  - **應用程式 (.exe)**

     會顯示連結器工具組 (C/C++ 編譯器、MIDL、資源編譯器、連結器、BSCMake、XML Web Service Proxy 產生器、自訂建置、建置前、連結前、建置後事件)。

  - **動態程式庫 (.dll)**

     會顯示連結器工具組、指定 /DLL 連結器選項，並將 _WINDLL define 新增至 CL。

  - **Makefile**

     會顯示 Makefile 工具組 (NMake)。

  - **靜態程式庫 (.lib)**

     會顯示管理員工具組 (與連結器工具組相同，除了用管理員取代連結器，並省略 XML Web Service Proxy 產生器)。

  - **公用程式**

     會顯示公用程式工具組 (MIDL、自訂建置、建置前、建置後事件)。

  若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>。

- **Windows SDK 版本**

   對於 Windows 目標平台，這會指定您的專案所需的 Windows SDK 版本。 當您使用 Visual Studio 安裝程式安裝 C++ 工作負載時，也會安裝 Windows SDK 的必要組件。 如果您的電腦上有其他 Windows SDK 版本，您已安裝的每個 SDK 工具版本都會出現在下拉式清單中。

   若要以 Windows 7 或 Windows Vista 為目標，請使用值 **8.1**，因為 Windows SDK 8.1 具有這些平台的回溯相容性。 此外，您應該在 targetver.h 定義 **_WIN32_WINNT** 的適當值。 對於 Windows 7，這是 0x0601。 請參閱[修改 WINVER 和 _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md)。

   您可以安裝 Visual Studio 隨附的 Windows XP 平台工具組，以便使用目前的程式庫版本來建置 Windows XP 和 Windows 2003 Server 專案。 如需如何取得及使用此平台工具組的資訊，請參閱[為 Windows XP 設定程式](../configuring-programs-for-windows-xp.md)。 如需變更平台工具組的其他資訊，請參閱[如何：修改目標 Framework 和平台工具組](../how-to-modify-the-target-framework-and-platform-toolset.md)。

- **平台工具組**

   可讓專案以不同版本的 Visual C++ 程式庫和編譯器為目標。 Visual Studio C++專案可以針對 Visual Studio 所安裝的預設工具組，或是數個舊版 Visual Studio 所安裝的其中一個工具組，包括建立可在 Windows XP 上執行之可執行檔的工具組。 如需變更平台工具組的資訊，請參閱[如何：修改目標 Framework 和平台工具組](../how-to-modify-the-target-framework-and-platform-toolset.md)。

- **C++語言標準**

   指定要使用的語言標準。 預設值為/std： c + + 14。 指定/std： c + + 17 以使用 c + + 17 功能，或/std： c + + + 最新版本以使用 c + + 20 或其他實驗性功能。 如需詳細資訊，請參閱[/std （指定語言標準版本）](std-specify-language-standard-version.md)

::: moniker-end

::: moniker range="<=vs-2017"

在 Visual Studio 2015 和 Visual Studio 2017 中，當您以滑鼠右鍵按一下**方案總管**中的專案節點，然後選取 [**屬性**] 時，左窗格中 [設定**屬性**] 節點底下的 [**一般**] 屬性頁會顯示內容的兩個區段：

- 一般

- 專案預設值

## <a name="general"></a>一般

- **目標平台**

   指定專案將執行所在的平台。 例如，Windows、Android 或 iOS。 值 **Windows 10** 表示專案以通用 Windows 平台為目標。 如果您以舊版 Windows 為目標，則不會列出版本，此欄位中的值只會顯示為 **Windows**。 這是當您建立專案時設定的唯讀欄位。

- **目標平臺版本（Visual Studio 2015）**

   指定專案可以在其上執行的平台最低版本。 這個屬性只有在專案類型支援時才會出現。 如果您的應用程式可以利用較新版 Windows SDK 中的功能，但仍然可以在沒有這些功能的較早版本上執行，可能遺失某些功能，則這兩個屬性的值可能會不同。 若是這樣，您的程式碼應該在執行階段檢查它執行的平台版本，而不要試著使用舊版平台中未提供的功能。

   C++專案系統不會強制執行此選項。 它是為了與其他程式設計語言的一致性，例如 C# 和 JavaScript，以及做為使用您專案的任何人的指南。 如果您使用最小版本中沒有的功能，Visual C++ 不會產生錯誤。

- **Windows SDK 版本（Visual Studio 2017）**

   對於 Windows 目標平台，這會指定您的專案所需的 Windows SDK 版本。 當您使用 Visual Studio 安裝程式安裝 C++ 工作負載時，也會安裝 Windows SDK 的必要組件。 如果您的電腦上有其他 Windows SDK 版本，您已安裝的每個 SDK 工具版本都會出現在下拉式清單中。

   若要以 Windows 7 或 Windows Vista 為目標，請使用值 **8.1**，因為 Windows SDK 8.1 具有這些平台的回溯相容性。 此外，您應該在 targetver.h 定義 **_WIN32_WINNT** 的適當值。 對於 Windows 7，這是 0x0601。 請參閱[修改 WINVER 和 _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md)。

   您可以安裝 Visual Studio 隨附的 Windows XP 平台工具組，以便使用目前的程式庫版本來建置 Windows XP 和 Windows 2003 Server 專案。 如需如何取得及使用此平台工具組的資訊，請參閱[為 Windows XP 設定程式](../configuring-programs-for-windows-xp.md)。 如需變更平台工具組的其他資訊，請參閱[如何：修改目標 Framework 和平台工具組](../how-to-modify-the-target-framework-and-platform-toolset.md)。

- **輸出目錄**

   指定連結器等工具將放置在建置程序期間建立之所有最終輸出檔案的目錄。 這通常包括連結器、管理員或 BSCMake 之類的工具的輸出。 根據預設，此屬性是巨集 $(SolutionDir)$(Configuration)\ 所指定的目錄。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>。

- **中繼目錄**

   指定編譯器等工具將放置在建置程序期間建立之所有中繼檔案的目錄。 這通常包括 C/C++ 編譯器、MIDL 及資源編譯器等工具的輸出。 根據預設，此屬性是巨集 $(Configuration)\ 所指定的目錄。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>。

- **目標名稱**

   指定此專案會產生的檔案名稱。 根據預設，此屬性是巨集 $(ProjectName) 所指定的檔名。

- **目標副檔名**

   指定此專案會產生的副檔名，例如 .exe 或 .dll。

- **清除時要刪除的副檔名**

   [清除] 選項 ([建置] 功能表) 會從建置專案組態的中繼目錄刪除檔案。 具有此屬性所指定副檔名的檔案，將會在執行 [清除] 時或您執行重建時刪除。 除了中繼目錄裡這些副檔名的檔案，建置系統也會刪除任何已知的建置輸出，而不論其所在位置 (包括像是 .obj 檔的中繼輸出)。 請注意，您可以指定萬用字元。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。

- **建置記錄檔**

   可讓您指定每當建置專案時建立記錄檔的非預設位置。 預設位置是由巨集 $(IntDir)$(MSBuildProjectName).log 所指定。

   若要變更目錄位置，您可以使用專案巨集。 請參閱[組建命令和屬性的一般宏](common-macros-for-build-commands-and-properties.md)。

- **平台工具組**

   可讓專案以不同版本的 Visual C++ 程式庫和編譯器為目標。 Visual Studio C++專案可以針對 Visual Studio 所安裝的預設工具組，或是數個舊版 Visual Studio 所安裝的其中一個工具組，包括建立可在 Windows XP 上執行之可執行檔的工具組。 如需變更平台工具組的資訊，請參閱[如何：修改目標 Framework 和平台工具組](../how-to-modify-the-target-framework-and-platform-toolset.md)。

- **啟用受控累加建置**

   對於受控專案，這會在您產生組件時啟用外部可見度的偵測。 如果其他專案看不到受控專案的變更，則不會重建相依專案。 如此可大幅改善方案 (包括受控專案) 的建置時間。

## <a name="project-defaults"></a>專案預設值

專案預設值區段中的屬性代表您可以修改的預設屬性。 這些屬性的定義可在 <安裝目錄>\VC\VCProjectDefaults 的 .props 檔案中找到。

- **組態類型**

  有數個組態類型可供選擇：

  - **應用程式 (.exe)**

     會顯示連結器工具組 (C/C++ 編譯器、MIDL、資源編譯器、連結器、BSCMake、XML Web Service Proxy 產生器、自訂建置、建置前、連結前、建置後事件)。

  - **動態程式庫 (.dll)**

     會顯示連結器工具組、指定 /DLL 連結器選項，並將 _WINDLL define 新增至 CL。

  - **Makefile**

     會顯示 Makefile 工具組 (NMake)。

  - **靜態程式庫 (.lib)**

     會顯示管理員工具組 (與連結器工具組相同，除了用管理員取代連結器，並省略 XML Web Service Proxy 產生器)。

  - **公用程式**

     會顯示公用程式工具組 (MIDL、自訂建置、建置前、建置後事件)。

  若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>。

- **MFC 用途**

   指定 MFC 專案將會靜態還是動態連結至 MFC DLL。 非 MFC 專案可選取 [使用標準的視窗程式庫] 連結至使用 MFC 時包含的各種 Win32 程式庫。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。

- **字元集**

   定義是否應該設定 _UNICODE 或 _MBCS。 在適當的地方，也會影響連結器進入點。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。

- **Common Language Runtime 支援**

   導致使用 [/clr](clr-common-language-runtime-compilation.md) 編譯器選項。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。

- **目標 .NET Framework 版本**

   在受控專案中，指定目標 .NET Framework 版本。

- **整個程式最佳化**

   指定 [/GL](gl-whole-program-optimization.md) 編譯器選項和 [/LTCG](ltcg-link-time-code-generation.md) 連結器選項。 根據預設，偵錯組態會停用此選項，而零售組態會啟用此選項。

- **Windows 市集應用程式支援**

   指定此專案是否支援 Windows 執行階段 (通用 Windows 平台) 應用程式。 如需詳細資訊，請參閱 [/ZW (Windows 執行階段編譯)](zw-windows-runtime-compilation.md) 及 Windows 開發人員中心。

::: moniker-end

## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](property-pages-visual-cpp.md)
