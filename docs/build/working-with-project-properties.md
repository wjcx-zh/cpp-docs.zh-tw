---
title: 在 Visual Studio 中設定 C ++ 編譯器和組建屬性
description: 使用 Visual Studio IDE 來變更 c + + 編譯器和連結器選項，以及其他組建設定。
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: 17b54311670f78cda78403c273cfbf57d43e84da
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042182"
---
# <a name="set-compiler-and-build-properties"></a>Set compiler and build properties (設定編譯器及組建屬性)

在 IDE 中，建置專案所需的所有資訊都會公開為「屬性」**。 此資訊包含應用程式名稱、副檔名 (例如 DLL、LIB、EXE)、編譯器選項、連結器選項、偵錯工具設定、自訂建置步驟，以及許多其他項目。 一般而言，您可以使用 *屬性頁* 來查看和修改這些屬性。 若要存取屬性頁，請從主功能表選擇 [**專案**  >  **_專案名稱_屬性**]，或以滑鼠右鍵按一下**方案總管**中的專案節點，然後選擇 [**屬性**]。

## <a name="default-properties"></a>預設屬性

當您建立專案時，系統會指派各種屬性值。 預設值會依據專案類型以及您在應用程式精靈中選擇的選項而稍有不同。 例如，ATL 專案具有與 MIDL 檔案相關的屬性，但這些屬性不存在於基本的主控台應用程式中。 預設屬性會顯示在 [屬性頁] 的 [一般] 窗格中：

![Visual C&#43;&#43; 專案預設值](media/visual-c---project-defaults.png "Visual C++ 專案預設值")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>將屬性套用至組建設定和目標平臺

某些屬性 (例如應用程式名稱) 適用於所有組建變異，而不論目標平台為何或它是偵錯組建還是發行組建。 但大部分的屬性都與組態相關。 這是因為，編譯器必須知道將在哪個特定平台上執行程式，以及要使用哪些特定的編譯器選項以產生正確的程式碼。 因此，當您設定屬性時，請務必注意新值應該套用到哪個組態與平台。 它應該只套用到偵錯 Win32 組建，還是也應該套用到偵錯 ARM 和偵錯 x64？ 例如，根據預設，[最佳化]**** 屬性在發行組態中設定為 [最快速度 (/O2)]****，但在偵錯組態中已停用。

屬性頁的設計可讓您隨時查看，以及在需要時修改應該會套用屬性值的組態與平台。 下圖顯示在頂端的清單方塊中包含組態與平台資訊的屬性頁。 如果在此處設定 [最佳化]**** 屬性，它只會套用到偵錯 Win32 組建，這正好是使用中的組態，如紅色箭頭所示。

![顯示現用設定的 Visual C&#43;&#43; 屬性頁面](media/visual-c---property-pages-showing-active-configuration.png "顯示作用中設定的 Visual C++ 屬性頁面")

下圖顯示相同的專案屬性頁，但組態已變更為 [發行]。 請注意 [最佳化] 屬性的不同值。 另外請注意，使用中的組態仍然是 [偵錯]。 您可以在此處設定任何組態的屬性；它不一定是使用中的組態。

![顯示發行設定的 Visual C&#43;&#43; 屬性頁面](media/visual-c---property-pages-showing-release-config.png "顯示發行設定的 Visual C++ 屬性頁面")

## <a name="target-platforms"></a>目標平台

「目標平台」** 指的是可執行檔將在其上執行之裝置及/或作業系統的類型。 您可以為多個平台建置專案。 C++ 專案可用的目標平台取決於專案類型；它們包括但不限於 Win32、x64、ARM、Android 和 iOS。     您可能會在 [組態管理員]**** 中看到的 **X86** 目標平台，等同於原生 C++ 專案中的 **Win32**。 Win32 表示 32 位元 Windows，而 **x64** 表示 64 位元 Windows。 如需這兩個平台的詳細資訊，請參閱[執行 32 位元應用程式](/windows/win32/WinProg64/running-32-bit-applications)。

您可能會在 [組態管理員]**** 中看到的 [任何 CPU]**** 目標平台值，對原生 C++ 專案沒有任何影響；它與 C++/CLI 和其他 .NET 專案類型有關。 如需詳細資訊，請參閱 [/CLRIMAGETYPE (指定 CLR 映像類型)](reference/clrimagetype-specify-type-of-clr-image.md)。

如需設定 Debug 組建屬性的詳細資訊，請參閱：

- [C + + 偵錯工具設定的專案設定](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [偵錯設定及準備](/visualstudio/debugger/debugger-settings-and-preparation)
- [調試準備： Visual C++ 專案類型](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [在 Visual Studio 偵錯工具中指定符號 (.pdb) 和原始程式檔](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>C + + 編譯器和連結器選項

C + + 編譯器和連結器選項位於左窗格中的 [ **c/c + +** ] 和 [ **連結器** ] 節點底下的 [設定 **屬性**] 下 這些會直接轉譯為將傳遞給編譯器的命令列選項。 若要閱讀特定選項的相關檔，請選取中央窗格中的選項，然後按 **F1**。 或者，您可以在 [MSVC 編譯器選項](reference/compiler-options.md) 和 [MSVC 連結器選項](reference/linker-options.md)流覽所有選項的檔。

[ **屬性頁** ] 對話方塊只會顯示與目前專案相關的屬性頁。 例如，如果專案沒有 .idl 檔案，就不會顯示 MIDL 屬性頁。 如需有關每個屬性頁設定的詳細資訊，請參閱 [ (c + +) 的屬性頁 ](reference/property-pages-visual-cpp.md)。

## <a name="directory-and-path-values"></a>目錄和路徑值

MSBuild 支援針對某些字串值使用稱為「宏」的編譯時期常數，包括目錄和路徑。 這些會在屬性頁中公開，您可以在其中使用 [屬性編輯器](#property_editor)來參考和修改它們。

下圖顯示 Visual Studio c + + 專案的屬性頁。 在左窗格中，已選取 [ **VC + + 目錄**] *規則* ，右窗格會列出與該規則相關聯的屬性。 這些 `$(...)` 值稱為「 *宏*」。 「巨集」** 是一個編譯時間常數，可以參考由 Visual Studio 或 MSBuild 系統所定義的值或使用者定義的值。 藉由使用宏而不是硬式編碼的值（例如目錄路徑），您可以更輕鬆地在電腦之間和 Visual Studio 的版本之間共用屬性設定，並且可以更妥善地確保專案設定在 [屬性繼承](project-property-inheritance.md)中正確地參與。

![專案屬性頁](media/project_property_pages_vc.png "Project_Property_Pages_VC")

您可以使用屬性編輯器來檢視所有可用巨集的值。

### <a name="predefined-macros"></a>預先定義巨集

*全域巨集*<br/>
套用至專案組態中的所有項目。 具有語法 `$(name)`。 例如，`$(VCInstallDir)` 即是全域巨集，這會儲存 Visual Studio 安裝根目錄。 全域巨集對應於 MSBuild 中的 `PropertyGroup`。

項目巨集**<br/>
具有語法 `%(name)`。 對於檔案，項目巨集只套用至該檔案。例如，您可以使用 `%(AdditionalIncludeDirectories)` 來指定只套用至特定檔案的 Include 目錄。 這類型的項目巨集對應於 MSBuild 中的 `ItemGroup` 中繼資料。 在專案組態的內容中使用時，項目巨集會套用至特定類型的所有檔案。 例如，C/c + + **預處理器定義** 設定屬性可以採用 `%(PreprocessorDefinitions)` 套用至專案中所有 .cpp 檔案的專案宏。 這類型的項目巨集對應於 MSBuild 中的 `ItemDefinitionGroup` 中繼資料。 如需詳細資訊，請參閱 [專案定義](/visualstudio/msbuild/item-definitions)。

### <a name="user-defined-macros"></a>使用者定義巨集

您可以建立 *使用者定義的宏* ，以做為專案組建中的變數使用。 例如，您可以建立使用者定義巨集，提供自訂建置步驟或自訂建置工具的值。 使用者定義巨集是名稱/值組。 在專案檔中，使用 **$(**<em>name</em>**)** 標記法來存取值。

使用者定義巨集會儲存在屬性工作表中。 如果您的專案還沒有包含屬性工作表，您可以遵循 [ [共用或重複使用 Visual Studio 專案設定](create-reusable-property-configurations.md)] 下的步驟來建立一個屬性工作表。

#### <a name="to-create-a-user-defined-macro"></a>建立使用者定義巨集

1. 開啟 **屬性管理員** 視窗。  (在功能表列上，選擇 [ **view**  >  **屬性管理員**] 或 [ **view**  >  **Other Windows**  >  **屬性管理員**]。 ) 開啟內容工作表的快捷方式功能表， (其名稱結尾為 [使用者) ]，然後選擇 [**屬性**]。 該屬性工作表的 [ **屬性頁** ] 對話方塊隨即開啟。

1. 在對話方塊的左窗格中，選取 [ **使用者宏**]。 在右窗格中，選擇 [ **加入宏** ] 按鈕以開啟 [ **加入使用者宏** ] 對話方塊。

1. 在對話方塊中，指定巨集的名稱和值。 （選擇性）選取 [ **將這個宏設定為組建環境中的環境變數** ] 核取方塊。

## <a name=""></a><a name="property_editor">屬性編輯器</a>

您可以使用屬性編輯器，修改特定字串屬性和選擇巨集做為值。 若要存取屬性編輯器，請選取屬性頁上的屬性，然後選擇右邊的向下箭號按鈕。 如果下拉式清單包含 **\<Edit>** ，您可以選擇它來顯示該屬性的屬性編輯器。

![屬性下拉式控制項可用來存取屬性編輯器](media/property_editor_dropdown.png "屬性編輯器下拉式清單")

在屬性編輯器中，您可以選擇 [ **宏** ] 按鈕來查看可用的宏與其目前的值。 下圖顯示選擇 [**宏**] 按鈕之後，[**其他 Include 目錄**] 屬性的屬性編輯器。 當您選取 [ **從父代或專案預設值繼承** ] 核取方塊，並加入新值時，它會附加至目前繼承的任何值。 如果您清除此核取方塊，則新值會取代繼承的值。 在大部分情況下，讓核取方塊保持已選取狀態。

![[Include 目錄] 屬性的 [屬性編輯器] 對話方塊](media/propertyeditorvc.png "PropertyEditorVC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>將 include 目錄新增至一組預設目錄

當您將 Include 目錄加入至專案時，注意不要覆寫所有的預設目錄。 新增目錄的正確方式是附加新路徑（例如 "C:\MyNewIncludeDir"），然後將 \" **$ (IncludePath) ** 宏附加至屬性值。

## <a name="quickly-browse-and-search-all-properties"></a>快速流覽和搜尋所有屬性

[所有選項]**** 屬性頁 (在 [屬性頁]**** 對話方塊中的 [組態屬性] &#124; [C/C++]**** 節點底下) 提供快速的方式，讓您瀏覽和搜尋目前內容中可用的屬性。 其中有特別的搜尋方塊和協助篩選結果的簡單語法：

沒有前置詞：<br/>
只在屬性名稱中搜尋 (不區分大小寫的子字串)。

'/' 或 '-'：<br/>
只在編譯器參數中搜尋 (不區分大小寫的前置詞)

v:<br/>
只在值中搜尋 (不區分大小寫的子字串)。

## <a name="set-environment-variables-for-a-build"></a>設定組建的環境變數

MSVC 編譯器 ( # A0) 會辨識特定的環境變數，特別是 LIB、LIBPATH、PATH 和 INCLUDE。 當您使用 IDE 建立時，[ [VC + + 目錄](reference/vcpp-directories-property-page.md) ] 屬性頁中設定的屬性會用來設定這些環境變數。 如果已經設定 LIB、LIBPATH 和 INCLUDE 值 (例如，透過開發人員命令提示字元)，這些值會取代為對應 MSBuild 屬性的值。 組建接著會在 PATH 之前加上 [VC++ 目錄] 可執行檔目錄屬性的值。 您可以設定使用者定義的環境變數，方法是建立使用者定義宏，然後核取 [ **將這個宏設定為組建環境中的環境變數**] 方塊。

## <a name="set-environment-variables-for-a-debugging-session"></a>設定偵錯工具會話的環境變數

在專案 [ **屬性頁** ] 對話方塊的左窗格中，展開 [設定 **屬性** ]，然後選取 [ **調試**程式]。

在右窗格中，修改 [ **環境** ] 或 [ **合併環境** ] 專案設定，然後選擇 [ **確定]** 按鈕。

## <a name="in-this-section"></a>本節內容

[共用或重複使用 Visual Studio 專案設定](create-reusable-property-configurations.md)<br/>
如何使用可共用或重複使用的自訂群組建設定來建立 .props 檔。

[專案屬性繼承](project-property-inheritance.md)<br/>
描述組建進程中 .props、.targets、.vcxproj 檔案和環境變數的評估順序。

[修改屬性和目標而不變更專案檔](modify-project-properties-without-changing-project-file.md)<br/>
如何建立暫存組建設定，而不需要修改專案檔。

## <a name="see-also"></a>另請參閱

[Visual Studio 專案-c + +](creating-and-managing-visual-cpp-projects.md)<br/>
[.vcxproj 和.props 檔案結構](reference/vcxproj-file-structure.md)<br/>
[屬性頁面 XML 檔案](reference/property-page-xml-files.md)<br/>
