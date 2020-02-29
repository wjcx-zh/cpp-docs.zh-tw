---
title: Visual Studio 中的 C++ 專案的 MSBuild 內部項目
ms.date: 02/26/2020
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: 010fa244ed77ea782fa76be959c58ff1e1b254a9
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166715"
---
# <a name="msbuild-internals-for-c-projects"></a>C++ 專案的 MSBuild 內部項目

當您在 IDE 中設定專案屬性，然後儲存專案時，Visual Studio 會將專案設定寫入至您的專案檔。 專案檔包含專案特有的設定。 不過，它不包含建立您的專案所需的所有設定。 專案檔含有 `Import` 元素，其中包含其他*支援檔案*的網路。 支援檔案包含建立專案所需的其餘屬性、目標和設定。

支援檔案中大部分的目標和屬性的唯一用途皆為實作建置系統。 本文討論您可以在 MSBuild 命令列上指定的有用目標和屬性。 若要探索更多目標和屬性，請瀏覽支援檔案目錄中的檔案。

## <a name="support-file-directories"></a>支援檔案目錄

根據預設，主要的 Visual Studio 支援檔案會位於下列目錄中。 這是特定版本的資訊。

### <a name="visual-studio-2019"></a>Visual Studio 2019

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*版本*\\VCTargets\\

  包含目標所使用的主要目標檔案 (.targets) 和屬性檔案 (.props)。 根據預設，$(VCTargetsPath) 巨集會參考這個目錄。 *版本*預留位置會參考 Visual Studio 版本：適用于 Visual Studio 2019、v150 （適用于 Visual Studio 2017）的 v160。

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*版本*\\VCTargets\\平臺\\*platform*\\

  包含平台特定的目標和屬性檔案，會覆寫其上層目錄中的目標和屬性。 此目錄也包含一個 DLL，會定義此目錄中的目標所使用的工作。 *platform* 預留位置代表 ARM、Win32 或 x64 子目錄。

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*版本*\\VCTargets\\平臺\\*平臺*\\PlatformToolsets\\*工具*組\\

  包含可讓組建使用指定的 *toolset* 產生 C++ 應用程式的目錄。 *platform* 預留位置代表 ARM、Win32 或 x64 子目錄。 *工具*組預留位置代表工具組子目錄。

### <a name="visual-studio-2017"></a>Visual Studio 2017

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\

  包含目標所使用的主要目標檔案 (.targets) 和屬性檔案 (.props)。 根據預設，$(VCTargetsPath) 巨集會參考這個目錄。

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\平臺\\*平臺*\\

  包含平台特定的目標和屬性檔案，會覆寫其上層目錄中的目標和屬性。 此目錄也包含一個 DLL，會定義此目錄中的目標所使用的工作。 *platform* 預留位置代表 ARM、Win32 或 x64 子目錄。

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\平臺\\*平臺*\\PlatformToolsets\\*工具*組\\

  包含可讓組建使用指定的 *toolset* 產生 C++ 應用程式的目錄。 *platform* 預留位置代表 ARM、Win32 或 x64 子目錄。 *工具*組預留位置代表工具組子目錄。

### <a name="visual-studio-2015-and-earlier"></a>Visual Studio 2015 和更早版本

- *磁片磁碟機*：\\Program Files *（X86）* \\MSBuild\\Microsoft .cpp （x86）\\v4.0\\*版本*\\

  包含目標所使用的主要目標檔案 (.targets) 和屬性檔案 (.props)。 根據預設，$(VCTargetsPath) 巨集會參考這個目錄。

- *磁片磁碟機*：\\Program Files *（X86）* \\MSBuild\\Microsoft .cpp\\v4.0\\*版本*\\平臺\\*platform*\\

  包含平台特定的目標和屬性檔案，會覆寫其上層目錄中的目標和屬性。 此目錄也包含一個 DLL，會定義此目錄中的目標所使用的工作。 *platform* 預留位置代表 ARM、Win32 或 x64 子目錄。

- *磁片磁碟機*：\\Program Files *（X86）* \\MSBuild\\Microsoft .cpp\\v4.0\\*版本*\\平臺\\*平臺*\\PlatformToolsets\\*工具*組\\

  包含可讓組建使用指定的 *toolset* 產生 C++ 應用程式的目錄。 *版本*預留位置為 Visual Studio 2012、V120 （Visual Studio 2013）和 V140 （適用于 Visual Studio 2015）的 V110。 *platform* 預留位置代表 ARM、Win32 或 x64 子目錄。 *工具*組預留位置代表工具組子目錄。 例如，它是使用 Visual Studio 2015 工具組來建立 Windows 應用程式的 v140。 或者，v120_xp 使用 Visual Studio 2013 工具組來建立 Windows XP。

- *磁片磁碟機*：\\Program Files *（X86）* \\MSBuild\\Microsoft .cpp\\v4.0\\平臺\\*平臺*\\PlatformToolsets\\*工具*組\\

  讓組建產生 Visual Studio 2008 或 Visual Studio 2010 應用程式的路徑不包含*版本*。 在這些版本中，*平臺*預留位置代表 Itanium、Win32 或 x64 子目錄。 *toolset* 預留位置代表 v90 或 v100 工具組子目錄。

## <a name="support-files"></a>支援檔案

支援檔案目錄包含具有下列副檔名的檔案：

| 分機 | 描述 |
| --------- | ----------- |
| .targets | 包含 `Target` XML 元素，會指定目標所執行的工作。 也可能包含 `PropertyGroup`、`ItemGroup`、`ItemDefinitionGroup` 和使用者定義的 `Item` 元素，用來檔案和命令列選項指派給工作參數。<br /><br /> 如需詳細資訊，請參閱 [Target 元素 (MSBuild)](/visualstudio/msbuild/target-element-msbuild)。 |
| .props | 包含 `Property Group` 和使用者定義的 `Property` XML 元素，會指定在建置期間使用的檔案和參數設定。<br /><br /> 也可能包含指定其他設定的 `ItemDefinitionGroup` 和使用者定義 `Item` XML 元素。 專案定義群組中所定義的專案與屬性類似，但無法從命令列存取。 Visual Studio 專案檔通常會使用項目來代表設定，而不是使用屬性。<br /><br /> 如需詳細資訊，請參閱[ItemGroup 元素（msbuild）](/visualstudio/msbuild/itemgroup-element-msbuild)、 [ItemDefinitionGroup 元素（Msbuild）](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)和[Item 元素（msbuild）](/visualstudio/msbuild/item-element-msbuild)。 |
| .xml | 包含宣告和初始化 IDE 使用者介面專案的 XML 元素。 例如，屬性工作表、屬性頁、textbox 控制項和 listbox 控制項。<br /><br /> .xml 檔案可直接支援 IDE，而非 MSBuild。 不過，IDE 屬性的值會指派給組建屬性和項目。<br /><br /> 大部分的 .xml 檔案會位於地區設定特定子目錄中。 例如，美國英文地區的檔案是 $ （VCTargetsPath）\\1033\\。 |

## <a name="user-targets-and-properties"></a>使用者目標和屬性

若要有效地使用 MSBuild，它有助於瞭解哪些屬性和目標是有用且相關的。 大部分的屬性和目標都有助於執行 Visual Studio 組建系統，因此不會與使用者相關。 本節說明使用者導向的屬性和目標，瞭解您的相關資訊。

### <a name="platformtoolset-property"></a>PlatformToolset 屬性

`PlatformToolset` 屬性會決定要在組建中使用的 MSVC 工具組。 依預設會使用目前的工具組。 設定此屬性時，會與常值字串串連以形成路徑。 它是一個目錄，其中包含為特定平臺建立專案時所需的屬性和目標檔案。 必須安裝平台工具組，才能使用該平台工具組版本來建置。

例如，將 `PlatformToolset` 屬性設為 `v140`，會使用 Visual Studio 2015 工具和程式庫來建置您的應用程式：

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture 屬性

`PreferredToolArchitecture` 屬性會決定要在組建中使用 32 位元還是 64 位元編譯器和工具。 此屬性不會影響輸出平臺架構或設定。 根據預設，如果未設定此屬性，MSBuild 會使用 x86 版的編譯器和工具。

例如，將 `PreferredToolArchitecture` 屬性設為 `x64`，會使用 64 位元編譯器和工具來建置您的應用程式：

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>UseEnv 屬性

根據預設，目前專案的平台特定設定會覆寫 PATH、INCLUDE、LIB、LIBPATH、CONFIGURATION 和 PLATFORM 等環境變數。 將 [`UseEnv`] 屬性設為 [ **true** ]，以確保不會覆寫環境變數。

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>目標

Visual Studio 支援檔案中有數百個目標。 不過，大部分都是使用者可忽略的系統導向目標。 大部分系統目標的前面都會加上底線（`_`），或名稱開頭為 "PrepareFor"、"Compute"、"Before"、"After"、"Pre" 或 "Post"。

下表列出數個有用的使用者導向目標。

| 目標 | 描述 |
| ------ | ----------- |
| BscMake | 執行 Microsoft Browse Information Maintenance Utility 工具 (bscmake.exe)。 |
| 組建 | 建置專案。<br /><br /> 此目標是專案的預設值。 |
| ClCompile | 執行 MSVC 編譯器工具 (cl.exe)。 |
| 清除 | 刪除暫存檔和中繼組建檔案。 |
| Lib | 執行 Microsoft 32 位元程式庫管理員工具 (lib.exe)。 |
| 連結 | 執行 MSVC 連結器工具 (link.exe)。 |
| ManifestResourceCompile | 從資訊清單中擷取資源清單，然後執行 Microsoft Windows 資源編譯器工具 (rc.exe)。 |
| Midl | 執行 Microsoft 介面定義語言 (MIDL) 編譯器工具 (midl.exe)。 |
| 重建 | 清除並建置您的專案。 |
| ResourceCompile | 執行 Microsoft Windows 資源編譯器工具 (rc.exe)。 |
| XdcMake | 執行 XML 文件工具 (xdcmake.exe)。 |
| Xsd | 執行 XML 結構描述定義工具 (xsd.exe)。 請參閱下列注意事項。 |

> [!NOTE]
> 在 Visual Studio 2017 和更新版本中，**xsd** 檔案的 C++ 專案支援已過時。 您仍然可以將 **CppCodeProvider.dll** 手動新增至 GAC 來使用 **Microsoft.VisualC.CppCodeProvider**。

## <a name="see-also"></a>另請參閱

[MSBuild 工作參考](/visualstudio/msbuild/msbuild-task-reference)\
[BscMake](/visualstudio/msbuild/bscmake-task)工作\
[CL](/visualstudio/msbuild/cl-task)工作\
[CPPClean](/visualstudio/msbuild/cppclean-task)工作\
[LIB](/visualstudio/msbuild/lib-task)工作\
[連結](/visualstudio/msbuild/link-task)工作\
[MIDL](/visualstudio/msbuild/midl-task)工作\
[MT](/visualstudio/msbuild/mt-task)工作\
[RC](/visualstudio/msbuild/rc-task)工作\
[SetEnv](/visualstudio/msbuild/setenv-task)工作\
[VCMessage](/visualstudio/msbuild/vcmessage-task)工作\
[XDCMake 工作](/visualstudio/msbuild/xdcmake-task)
