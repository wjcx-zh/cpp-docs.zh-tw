---
title: MSBuild (Visual C++) 概觀
ms.date: 11/04/2016
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: 072bc15cc931c2fd50cf8a2a1ff0c9145da8b7be
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414690"
---
# <a name="msbuild-visual-c-overview"></a>MSBuild (Visual C++) 概觀

MSBuild 是標準建置 Visual c + + 專案系統。 當您建置 Visual Studio 整合式的開發環境 (IDE) 中的專案時，它會使用 msbuild.exe 工具、 XML 專案檔，以及選擇性的設定檔。 雖然您可以使用執行 msbuild.exe 加專案檔，在命令列上的，IDE 會提供使用者介面，讓您更輕鬆地設定和建置專案。 本概觀會說明 Visual c + + 如何使用 MSBuild 系統。

## <a name="prerequisites"></a>必要條件

閱讀下列 MSBuild 相關文件。

- [MSBuild](/visualstudio/msbuild/msbuild)概觀的 MSBuild 概念。

- [MSBuild 參考](/visualstudio/msbuild/msbuild-reference)參考 MSBuild 系統的相關資訊。

- [專案檔案結構描述參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)列出 MSBuild XML 結構描述的項目，以及其屬性和父系和子系的項目。 請特別注意[ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild)， [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild)，[目標](/visualstudio/msbuild/target-element-msbuild)，以及[工作](/visualstudio/msbuild/task-element-msbuild)項目。

- [命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)說明的命令列引數和選項可供您使用 msbuild.exe。

- [工作參考](/visualstudio/msbuild/msbuild-task-reference)描述 MSBuild 工作。 特別注意這些工作，也就是特定 Visual c + +:[BscMake 工作](/visualstudio/msbuild/bscmake-task)， [CL 工作](/visualstudio/msbuild/cl-task)， [CPPClean 工作](/visualstudio/msbuild/cppclean-task)， [LIB 工作](/visualstudio/msbuild/lib-task)，[連結工作](/visualstudio/msbuild/link-task)， [MIDL 工作](/visualstudio/msbuild/midl-task)， [MT 工作](/visualstudio/msbuild/mt-task)， [RC 工作](/visualstudio/msbuild/rc-task)， [SetEnv 工作](/visualstudio/msbuild/setenv-task)， [VCMessage 工作](/visualstudio/msbuild/vcmessage-task)， [XDCMake 工作](/visualstudio/msbuild/xdcmake-task)， [XSD 工作](/visualstudio/msbuild/xsd-task)。

## <a name="msbuild-on-the-command-line"></a>在命令列上的 MSBuild

下列陳述式，從[MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)說明 msbuild.exe 工具使用隱含或明確*project_file*引數 （Visual c + + 專案的.vcxproj 檔案）以及零或多個命令列*選項*引數。

> **msbuild.exe** [ *project_file* ] [ *options* ]

使用 **/target** (或 **/t**) 和 **/property** (或 **/p**) 命令列選項來覆寫特定的屬性和目標在專案檔中指定。

專案檔有一個重要功能是指定*目標*，這是套用至您的專案，並輸入和輸出執行該作業所需的特定作業。 專案檔可以指定一或多個目標，其中可以包括預設目標。

每個目標是由一或多個序列所組成*任務*。 每個工作被以.NET Framework 類別，其中包含一個可執行命令。 例如， [CL 工作](/visualstudio/msbuild/cl-task)包含[cl.exe](../build/reference/compiling-a-c-cpp-program.md)命令。

A*工作參數*是類別工作的屬性，通常代表可執行命令的命令列選項。 例如，`FavorSizeOrSpeed`的參數`CL`工作會對應至 **/Os**並 **/Ot**編譯器選項。

其他工作參數都支援 MSBuild 基礎結構。 比方說，`Sources`工作參數指定一組可供其他工作的工作。 如需有關 MSBuild 工作的詳細資訊，請參閱[工作參考](/visualstudio/msbuild/msbuild-task-reference)。

大部分工作都需要輸入和輸出，例如檔案名稱、 路徑和字串、 數值或布林參數。 比方說，一般輸入是編譯的.cpp 原始程式檔的名稱。 重要的輸入的參數是一個字串，指定建置組態與平台，例如 「 偵錯\|Win32"。 輸入和輸出由一或多個使用者定義的 XML`Item`中所包含的項目`ItemGroup`項目。

專案檔也可以指定使用者定義*屬性*並`ItemDefinitionGroup`*項目*。 屬性和項目會形成名稱/值組，可用來當做組建中的變數。 定義一組的名稱元件*巨集*，和值的部分宣告*巨集值*。 屬性巨集可使用 $(*名稱*) 表示法和項目巨集使用存取 %(*名稱*) 標記法。

在專案檔中的其他 XML 項目可以測試巨集，然後有條件地設定任何巨集的值或控制組建的執行。 巨集名稱和常值字串可以串連來產生建構，例如路徑和檔案名稱。 在命令列 **/property**選項可以設定或覆寫專案屬性。 在命令列上，不能參考項目。

MSBuild 系統可以有條件地目標之前或之後執行另一個目標。 此外，系統可以建置目標，根據目標所取用的檔案是否比更新的檔案就會發出。

## <a name="msbuild-in-the-ide"></a>在 IDE 中的 MSBuild

當您在 IDE 中設定專案屬性，然後儲存專案時，Visual c + + 會將專案設定寫入專案檔中。 專案檔包含您專案中，唯一的設定，但它不包含建置您的專案所需的所有設定。 專案檔內含`Import`項目包含的其他網路*支援檔案。* 支援檔案中包含其餘的屬性、 目標和建置專案所需的設定。

大部分的目標和支援檔案中的屬性存在只是為了實作建置系統。 下列章節會討論一些有用的目標和您可以指定在 MSBuild 命令列的屬性。 若要探索更多目標和屬性，瀏覽支援檔案目錄中的檔案。

### <a name="support-file-directories"></a>支援檔案目錄

根據預設，主要的 Visual c + + 支援檔案位於下列目錄中。 Microsoft Visual Studio 下的目錄會使用 Visual Studio 2017 和更新版本中，位於 MSBuild 底下的目錄會使用 Visual Studio 2015 和更早版本。

|Directory|描述|
|---------------|-----------------|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86)\v4.0\\*version*\ |包含主要的目標檔案 (.targets) 和屬性檔案 (.props) 所使用的目標。 根據預設，$ （vctargetspath） 巨集，請參考這個目錄。|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\Platforms\\*platform*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*platform*\ |包含目標和其父目錄中的屬性會覆寫的平台特定目標和屬性檔案。 這個目錄也包含定義工作所使用的目標，此目錄中的 DLL。<br /><br /> *平台*預留位置代表 ARM，Win32 或 x64 子目錄。|
|*drive*:\Program Files *(x86)* \Microsoft Visual Studio\\*year*\\*edition*\Common7\IDE\VC\VCTargets\Platforms\\*platform*\PlatformToolsets\\*toolset*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*version*\Platforms\\*platform*\PlatformToolsets\\*toolset*\ <br /><br />*drive*:\Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*platform*\PlatformToolsets\\*toolset*\ |包含可讓組件產生 Visual c + + 應用程式，使用指定的目錄*工具組*。<br /><br /> *年份*並*edition* Visual Studio 2017 和更新版本中所使用的預留位置。 *版本*預留位置是 V110 適用於 Visual Studio 2012、 V120 適用於 Visual Studio 2013 或適用於 Visual Studio 2015 的 V140。 *平台*預留位置代表 ARM，Win32 或 x64 子目錄。 *工具組*預留位置代表的 toolset 子目錄，例如，用於建置 Windows 應用程式，使用 Visual Studio 2015 工具組，建置適用於 Windows XP 使用 Visual Studio 2013 的工具組或以 v110_wp80 v120_xp v140使用 Visual Studio 2012 的工具組，以建置 Windows Phone 8.0 的應用程式。<br /><br />包含可讓組件產生 Visual c + + 2008年或 Visual c + + 2010年的應用程式的目錄的路徑不包含*版本*，而*平台*預留位置代表在 Itanium、 Win32、 或 x64 子目錄。 *工具組*預留位置代表 v90 或 v100 的 toolset 子目錄。|

### <a name="support-files"></a>支援檔案

支援檔案目錄包含具有這些副檔名的檔案：

|副檔名|描述|
|---------------|-----------------|
|.targets|包含`Target`指定目標所執行的工作的 XML 項目。 也可能會包含`PropertyGroup`， `ItemGroup`， `ItemDefinitionGroup`，和使用者定義`Item`用來指派給工作參數的檔案和命令列選項的項目。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 目標項目 (MSBuild)](/visualstudio/msbuild/target-element-msbuild)。|
|.props|包含`Property Group`和使用者定義`Property`指定在建置期間所使用的檔案和參數設定的 XML 項目。<br /><br /> 也可能會包含`ItemDefinitionGroup`和使用者定義`Item`指定其他設定的 XML 項目。 定義項目定義群組中的項目類似於屬性，但不能從命令列存取。 Visual c + + 專案檔經常會使用而不是屬性的項目來代表設定。<br /><br /> 如需詳細資訊，請參閱 < [ItemGroup 項目 (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild)， [ItemDefinitionGroup 項目 (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)，並[item 項目 (MSBuild)](/visualstudio/msbuild/item-element-msbuild)。|
|.xml|包含宣告和初始化 IDE 使用者介面項目，例如屬性工作表和屬性頁，以及文字方塊和清單方塊控制項的 XML 項目。<br /><br /> .Xml 檔案直接支援 IDE，而非 MSBuild。 不過，指派 IDE 屬性的值來建置屬性和項目。<br /><br /> 大部分.xml 檔案是在地區設定特定子目錄。 例如，英文-美國 」 地區的檔案位於 $(VCTargetsPath) \1033\\。|

## <a name="user-targets-and-properties"></a>使用者目標和屬性

若要最有效地使用 MSBuild 命令列上，最好先知道哪些屬性和目標有用且相關。 大部分屬性和目標協助實作 Visual c + + 建置系統，也因此無法與使用者相關。 本節說明一些值得使用者導向屬性和目標。

### <a name="platformtoolset-property"></a>PlatformToolset 屬性

`PlatformToolset`屬性會判斷在組建中使用的 Visual c + + 工具組。 根據預設，會使用目前的工具組。 當設定這個屬性時，屬性的值被串連來形成包含建置專案，以供特定平台所需的屬性和目標檔案的目錄路徑的常值字串。 必須安裝平台工具組，使用該平台工具組版本來建置。

例如，設定`PlatformToolset`屬性設`v140`使用 Visual c + + 2015年工具和程式庫來建置您的應用程式：

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture 屬性

`PreferredToolArchitecture`屬性決定組建中會使用 32 位元或 64 位元編譯器和工具。 這個屬性不會影響輸出平台架構或組態。 根據預設，MSBuild 會使用 x86 版本的編譯器和工具，如果沒有設定這個屬性。

例如，設定`PreferredToolArchitecture`屬性設`x64`使用 64 位元編譯器和工具來建置您的應用程式：

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>UseEnv 屬性

根據預設，目前專案的平台特定設定覆寫的路徑、 INCLUDE、 LIB、 LIBPATH、 組態及平台的環境變數。 設定`UseEnv`屬性，以 **，則為 true**保證不會覆寫環境變數。

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>目標

有數百個 Visual c + + 支援檔案中的目標。 不過，大部分都是系統導向的目標，使用者可以忽略。 大部分系統目標都會加上底線 (_)，或有名稱開頭為"PrepareFor"、"Compute"、"Before"、"After"、"Pre"或"Post"。

下表列出數個實用的使用者導向目標。

|目標|描述|
|------------|-----------------|
|BscMake|執行 Microsoft Browse Information Maintenance Utility 工具 bscmake.exe。|
|組建|建置專案。<br /><br /> 這是專案的預設目標。|
|ClCompile|執行 Visual c + + 編譯器工具 cl.exe。|
|清除|刪除暫存檔和中繼組建檔案。|
|Lib|執行 Microsoft 32 位元 Library Manager 工具 lib.exe。|
|連結|執行 Visual c + + 連結器工具 link.exe。|
|ManifestResourceCompile|從資訊清單擷取資源清單，然後執行 Microsoft Windows 資源編譯器工具 rc.exe。|
|Midl|執行 Microsoft 介面定義語言 (MIDL) 編譯器工具 midl.exe。|
|重建|清除，並建立您的專案。|
|ResourceCompile|執行 Microsoft Windows 資源編譯器工具 rc.exe。|
|XdcMake|執行 XML 文件工具 xdcmake.exe。|
|Xsd|執行 XML 結構描述定義工具 xsd.exe。 請參閱下列注意事項。|

> [!NOTE]
> 在 Visual Studio 2017 中，c + + 專案的支援**xsd**檔案已被取代。 您仍然可以使用**Microsoft.VisualC.CppCodeProvider**加上**CppCodeProvider.dll**手動加入 GAC。

## <a name="see-also"></a>另請參閱

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
