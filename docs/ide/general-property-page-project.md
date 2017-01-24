---
title: "一般屬性頁 (專案) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCConfiguration.IntermediateDirectory"
  - "VC.Project.VCConfiguration.ConfigurationType"
  - "VC.Project.VCConfiguration.ManagedExtensions"
  - "VC.Project.VCConfiguration.BuildBrowserInformation"
  - "VC.Project.VCConfiguration.BuildLogFile"
  - "VC.Project.VCConfiguration.PlatformToolset"
  - "VC.Project.VCConfiguration.TargetName"
  - "VC.Project.VCConfiguration."
  - "VC.Project.VCConfiguration.TargetExt"
  - "VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage"
  - "VC.Project.VCConfiguration.ReferencesPath"
  - "VC.Project.VCConfiguration.DeleteExtensionsOnClean"
  - "VC.Project.VCConfiguration.useOfMfc"
  - "VC.Project.VCConfiguration.CharacterSet"
  - "VC.Project.VCGeneralMakefileSettings.ConfigurationType"
  - "VC.Project.VCConfiguration.OutputDirectory"
  - "VC.Project.VCConfiguration.AppSupport"
  - "VC.Project.VCConfiguration.ToolFiles"
  - "VC.Project.VCConfiguration.useOfATL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "清除建置選項"
  - "輸出檔, 設定目錄"
  - "Unicode, 建立 C++ 組建組態"
ms.assetid: 593b383c-cd0f-4dcd-ad65-9ec9b4b19c45
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般屬性頁 (專案)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您在方案總管中以滑鼠右鍵按一下專案節點，選取 \[屬性\] 時，在左窗格的 \[組態屬性\] 節點下 \[一般\] 屬性頁顯示屬性的兩個區段：  
  
-   一般  
  
-   專案預設值  
  
## 一般  
 \[一般\] 區段中的屬性會影響在建置程序中建立的檔案位置，以及在選取 \[清除\] 選項 \(\[建置\] 功能表\) 時要刪除的檔案。  
  
 **目標平台**  
 指定專案將執行所在的平台。 例如，Windows、Android 或 iOS。 值 **Windows 10** 表示專案以通用 Windows 平台為目標。 如果您以舊版的 Windows 版本為目標，則版本不會列出，此欄位中的值只會顯示為 **Windows**。 這是當您建立專案時設定的唯讀欄位。  
  
 **目標平台版本**  
 對於 Windows 平台，這會指定您的專案建置使用的 Windows SDK 版本。 對於 Windows，這是 Windows SDK 版本。[!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 隨附於 Windows SDK 8.1。 如果您已安裝 [Tools for Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=617631)，則您已安裝的工具每個版本會出現在下拉式清單中。  
  
 若要以 Windows 7 或 Windows Vista 為目標，請使用值 **8.1**，因為 Windows SDK 8.1 具有這些平台的回溯相容性。 此外，您應該在 targetver.h 定義 \_WIN32\_WINNT 的適當值。 對於 Windows 7，這是 0x0601。 請參閱 [修改 WINVER 和 \_WIN32\_WINNT](../porting/modifying-winver-and-win32-winnt.md)。  
  
 您可以安裝 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 隨附的 v110\_xp 平台工具組，以便使用目前的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本來建置 Windows XP 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 專案。 如需如何取得及使用這個平台工具組的相關資訊，請參閱 [為 Windows XP 設定 C\+\+ 11 程式](../build/configuring-programs-for-windows-xp.md)。 如需變更平台工具組的其他資訊，請參閱 [如何：修改目標 Framework 和平台工具組](../build/how-to-modify-the-target-framework-and-platform-toolset.md)。  
  
 **目標平台最小值。 版本**  
 指定專案可以在其上執行的平台最低版本。 只有當專案類型支援此功能，例如在通用 Windows 專案中，才會顯示這個屬性。 如果您的應用程式可以利用較新版 Windows SDK 中的功能，但仍然可以在沒有這些功能的較早版本上執行，可能遺失某些功能，則這兩個屬性的值可能會不同。 若是這樣，您的程式碼應該在執行階段檢查它執行的平台版本，而不要試著使用舊版平台中未提供的功能。  
  
 請注意，Visual C\+\+ 不會強制此選項。 它是為了與其他程式設計語言的一致性，例如 C\# 和 JavaScript，以及做為使用您專案的任何人的指南。 如果您使用最小版本中沒有的功能，Visual C\+\+ 不會產生錯誤。  
  
 **輸出目錄**  
 指定連結器等工具將放置在建置程序期間建立之所有最終輸出檔案的目錄。 這通常包括連結器、管理員或 BSCMake 之類的工具的輸出。  
  
 若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>。  
  
 **中繼目錄**  
 指定編譯器等工具將放置在建置程序期間建立之所有中繼檔案的目錄。 這通常包括 C\/C\+\+ 編譯器、MIDL 及資源編譯器等工具的輸出。  
  
 若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>。  
  
 **目標名稱**  
 指定此專案會產生的檔案名稱。  
  
 **目標副檔名**  
 指定此專案會產生的副檔名，例如 .exe 或 .dll。  
  
 **清除時要刪除的副檔名**  
 \[清除\] 選項 \(\[建置\] 功能表\) 會從建置專案組態的中繼目錄刪除檔案。 具有此屬性所指定副檔名的檔案，將會在執行 \[清除\] 時或您執行重建時刪除。 除了中繼目錄裡這些副檔名的檔案，建置系統也會刪除任何已知的建置輸出，而不論其所在位置 \(包括像是 .obj 檔的中繼輸出\)。 請注意，您可以指定萬用字元。  
  
 若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。  
  
 **建置記錄檔**  
 可讓您指定每當建置專案時建立記錄檔的非預設位置。  
  
 若要變更目錄位置，您可以使用專案巨集。 請參閱 [建置命令和屬性的巨集](../ide/common-macros-for-build-commands-and-properties.md)。  
  
 **平台工具組**  
 可讓專案以不同版本的 Visual C\+\+ 程式庫和編譯器為目標。[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 專案可以 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] \(**v100**\) 的預設工具組或建立可在 Windows XP 上執行之可執行檔的工具組做為目標。  
  
## 專案預設值  
 專案預設值區段中的屬性代表您可以修改的預設屬性。 這些屬性的定義可在 *安裝目錄*\\VC\\VCProjectDefaults 中的 .props 檔案中找到。  
  
 **組態類型**  
 有數個組態類型可供選擇：  
  
-   **應用程式 \(.exe\)**，這會顯示連結器工具組 \(C\/C\+\+ 編譯器、MIDL、資源編譯器、連結器、BSCMake、XML Web 服務 Proxy 產生器、自訂建置、建置前、連結前、建置後事件\)。  
  
-   **動態程式庫 \(.dll\)**，這會顯示連結器工具組、指定 \/DLL 連結器選項，並將 \_WINDLL define 加入 CL。  
  
-   **Makefile**，這會顯示 makefile 工具組 \(NMake\)。  
  
-   **靜態程式庫 \(.lib\)**，這會顯示管理員工具組 \(與連結器工具組相同，除了用管理員取代連結器，並省略 XML Web 服務 Proxy 產生器\)。  
  
-   **公用程式**，這會顯示公用程式工具組 \(MIDL、自訂建置、建置前、建置後事件\)。  
  
 若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>。  
  
 **MFC 用途**  
 指定 MFC 專案將會靜態還是動態連結至 MFC DLL。 非 MFC 專案可選取 \[使用標準的視窗程式庫\] 連結至使用 MFC 時包含的各種 Win32 程式庫。  
  
 若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。  
  
 **ATL 用途**  
 指定 ATL 專案將會靜態還是動態連結至 ATL DLL。 如果指定 \[未使用 ATL\] 以外的任何項目，define 將會加入編譯器 \[命令列\] 屬性頁。  
  
 若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>。  
  
 **字元集**  
 定義是否應該設定 \_UNICODE 或 \_MBCS。 在適當的地方，也會影響連結器進入點。  
  
 若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。  
  
 **Common Language Runtime 支援**  
 導致使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項。  
  
 若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。  
  
 **整個程式最佳化**  
 指定 [\/GL](../build/reference/gl-whole-program-optimization.md) 編譯器選項和 [\/LTCG](../build/reference/ltcg-link-time-code-generation.md) 連結器選項。  
  
 **Windows 市集應用程式支援**  
 指定此專案是否支援 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式。 如需詳細資訊，請參閱 [\/ZW \(Windows 執行階段編譯\)](../build/reference/zw-windows-runtime-compilation.md) 及 Windows 開發人員中心。  
  
## 請參閱  
 [屬性頁](../ide/property-pages-visual-cpp.md)