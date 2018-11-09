---
title: 建置命令和屬性的一般巨集
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- $(FrameworkSDKDir) macro
- ProjectName macro $(ProjectName)
- DevEnvDir macro $(DevEnvDir)
- $(DevEnvDir) macro
- TargetPath macro $(TargetPath)
- VSInstallDir macro $(VSInstallDir)
- $(InputFileName) macro
- $(SolutionFileName) macro
- macros [C++], build macros
- InputFileName macro $(InputFileName)
- $(VCInstallDir) macro
- $(IntDir) macro
- $(ConfigurationName) macro
- SolutionDir macro $(SolutionDir)
- $(TargetPath) macro
- $(Inherit) macro
- $(SolutionPath) macro
- WebDeployRoot macro $(WebDeployRoot)
- WebDeployPath macro $(WebDeployPath)
- StopEvaluating macro $(StopEvaluating)
- $(RootNamespace) macro
- $(WebDeployRoot) macro
- ProjectPath macro $(ProjectPath)
- $(ProjectPath) macro
- $(InputDir) macro
- SolutionName macro $(SolutionName)
- ProjectExt macro $(ProjectExt)
- $(TargetExt) macro
- $(ProjectFileName) macro
- TargetName macro $(TargetName)
- $(References) macro
- References macro $(References)
- TargetExt macro $(TargetExt)
- ProjectDir macro $(ProjectDir)
- $(TargetDir) macro
- SolutionExt macro $(SolutionExt)
- $(SolutionDir) macro
- ProjectFileName macro $(ProjectFileName)
- VCInstallDir macro $(VCInstallDir)
- $(InputExt) macro
- $(TargetFileName) macro
- $(SolutionExt) macro
- PlatformName macro $(PlatformName)
- IntDir macro $(IntDir)
- $(FrameworkVersion) macro
- $(ProjectDir) macro
- build macros [C++]
- InputPath macro $(InputPath)
- $(VSInstallDir) macro
- $(WebDeployPath) macro
- TargetFileName macro $(TargetFileName)
- NoInherit macro $(NoInherit)
- ConfigurationName macro $(ConfigurationName)
- $(ProjectExt) macro
- TargetDir macro $(TargetDir)
- InputName macro $(InputName)
- $(ProjectName) macro
- FrameworkSDKDir macro $(FrameworkSDKDir)
- $(ParentName) macro
- InputExt macro $(InputExt)
- $(SafeRootNamespace) macro
- InputDir macro $(InputDir)
- $(FxCopDir) macro
- $(RemoteMachine) macro
- Inherit macro $(Inherit)
- FrameworkVersion macro $(FrameworkVersion)
- $(StopEvaluating) macro
- $(OutDir) macro
- FrameworkDir macro $(FrameworkDir)
- SolutionFileName macro $(SolutionFileName)
- $(NoInherit) macro
- RemoteMachine macro $(RemoteMachine)
- properties [C++], build property macros
- $(TargetName) macro
- $(SolutionName) macro
- $(InputPath) macro
- ParentName macro $(ParentName)
- OutDir macro $(OutDir)
- SafeRootNamespace macro $(SafeRootNamespace)
- FxCopDir macro $(FxCopDir)
- $(InputName) macro
- RootNamespace macro $(RootNamespace)
- builds [C++], macros
- $(FrameworkDir) macro
- $(PlatformName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: 3ccd5b7a8fe8a04b69a963e8edc3811cc3fd2772
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628575"
---
# <a name="common-macros-for-build-commands-and-properties"></a>建置命令和屬性的一般巨集

根據您的安裝選項，Visual Studio 可以提供數百個巨集給您。 這些巨集會對應至 .props 或 .targets 檔案或是您專案設定中預設設定的 MSBuild 屬性。 您可以在接受字串的專案 [屬性頁]  對話方塊的任何位置使用這些巨集。 這些巨集不區分大小寫。

## <a name="view-the-current-properties-and-macros"></a>檢視目前的屬性和巨集

若要顯示目前可用的巨集，請在 [屬性頁] 對話方塊的任何屬性頁上，選擇屬性資料列結尾的下拉式箭頭。 如果 [編輯] 可用，請選擇它，然後選擇 [編輯] 對話方塊中的 [巨集] 按鈕。 會列出 Visual Studio 目前可見料集的屬性和巨集，以及其每一個的目前值。 如需詳細資訊，請參閱[屬性頁](../ide/property-pages-visual-cpp.md)的**指定使用者定義值**一節。

## <a name="list-of-common-macros"></a>常見巨集的清單

下表描述常用的可用巨集子集。 此清單並不完整。 如需如何建立 MSBuild 屬性定義並作為 .props、.targets 和 .vcxproj 檔案中巨集的詳細資訊，請參閱 [MSBuild 屬性](/visualstudio/msbuild/msbuild-properties)。

|巨集|描述|
|-----------|-----------------|
|**$(Configuration)**|目前的專案設定名稱，例如 "Debug"。|
|**$(DevEnvDir)**|Visual Studio 的安裝目錄 (定義為磁碟機 + 路徑)，尾端有反斜線 '\\'。|
|**$(FrameworkDir)**|.NET Framework 安裝所在目錄。|
|**$(FrameworkSDKDir)**|.NET Framework 安裝所在目錄。 .NET Framework 可能已安裝為 Visual Studio 的一部分或另行安裝。|
|**$(FrameworkVersion)**|Visual Studio 使用的 .NET framework 版本。 結合了 **$(FrameworkDir)**，Visual Studio 使用的 .NET Framework 版本完整路徑。|
|**$(FxCopDir)**|fxcop.cmd 檔案的路徑。 不是所有 Visual C++ 版本都安裝 fxcop.cmd 檔案。|
|**$(IntDir)**|為中繼檔案指定的目錄路徑。 如果這是相對路徑，前往這個路徑的中繼檔案會附加在專案目錄的後面。 這個路徑應該有尾端斜線。 這可以解析 **Intermediate Directory** 屬性的值。 請勿使用 **$(OutDir)** 定義這個屬性。|
|**$(OutDir)**|輸出檔案目錄的路徑。 如果這是相對路徑，前往這個路徑的輸出檔案會附加在專案目錄的後面。 這個路徑應該有尾端斜線。 這可以解析 **Output Directory** 屬性的值。 請勿使用 **$(IntDir)** 定義這個屬性。|
|**$(Platform)**|目前的專案平台名稱，例如 "Win32"。|
|**$(ProjectDir)**|專案的目錄 (定義為磁碟機 + 路徑)，尾端有反斜線 '\\'。|
|**$(ProjectExt)**|專案的副檔名。 副檔名前面有 '.'。|
|**$(ProjectFileName)**|專案的檔案名稱 (定義為名稱 + 副檔名)。|
|**$(ProjectName)**|專案的主檔名。|
|**$(ProjectPath)**|專案的絕對路徑名稱 (定義為磁碟機 + 路徑 + 主檔名 + 副檔名)。|
|**$(RemoteMachine)**|設定為偵錯屬性頁的 **Remote Machine** 屬性值。 如需詳細資訊，請參閱 [變更 C/C++ 偵錯組態的專案設定](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) 。|
|**$(RootNameSpace)**|包含應用程式的命名空間 (如果有的話)。|
|**$(SolutionDir)**|方案的目錄 (定義為磁碟機 + 路徑)，尾端有反斜線 '\\'。 只有在 IDE 中建置方案時才會定義。|
|**$(SolutionExt)**|解決方案的副檔名。 副檔名前面有 '.'。 只有在 IDE 中建置方案時才會定義。|
|**$(SolutionFileName)**|解決方案的檔案名稱 (定義為主檔名 + 副檔名)。 只有在 IDE 中建置方案時才會定義。|
|**$(SolutionName)**|解決方案的主檔名。 只有在 IDE 中建置方案時才會定義。|
|**$(SolutionPath)**|解決方案的絕對路徑名稱 (定義為磁碟機 + 路徑 + 主檔名 + 副檔名)。 只有在 IDE 中建置方案時才會定義。|
|**$(TargetDir)**|建置的主要輸出檔目錄 (定義為磁碟機 + 路徑)，尾端有反斜線 '\\'。|
|**$(TargetExt)**|建置的主要輸出檔副檔名。 副檔名前面有 '.'。|
|**$(TargetFileName)**|建置的主要輸出檔檔案名稱 (定義為主檔名 + 副檔名)。|
|**$(TargetName)**|建置的主要輸出檔主檔名。|
|**$(TargetPath)**|建置的主要輸出檔絕對路徑名稱 (定義為磁碟機 + 路徑 + 主檔名 + 副檔名)。|
|**$(VCInstallDir)**|包含您 Visual Studio 安裝之 C++ 內容的目錄。 這個屬性包含的目標 Visual C++ 工具集版本，可能和主機 Visual Studio 不一樣。 例如，使用 `$(PlatformToolset) = v140` 建置時，**$(VCInstallDir)** 會包含 Visual C++ 2015 安裝的路徑。|
|**$(VSInstallDir)**|Visual Studio 安裝所在目錄。 這個屬性包含的目標 Visual Studio 工具集版本，可能和主機 Visual Studio 不一樣。 例如，使用 `$(PlatformToolset) = v110`建置時， **$(VSInstallDir)** 會包含 Visual Studio 2012 安裝的路徑。|
|**$(WebDeployPath)**|從 Web 部署根目錄到專案輸出所屬根目錄的相對路徑。 傳回 <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>的相同值。|
|**$(WebDeployRoot)**|**\<localhost>** 位置的絕對路徑。 例如，c:\inetpub\wwwroot。|

## <a name="obsolete-macros"></a>已淘汰的巨集

在 Visual Studio 2008 與 Visual Studio 2010 之間，C++ 的建置系統已大幅變更。 在舊版專案類型中使用的許多巨集已經變更為新的巨集。 這些巨集不再使用，或是已取代為一或多個對等的屬性或[項目中繼資料巨集](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(**_name_**)**) 值。 標示為「已移轉」的巨集可以由專案移轉工具更新。 如果包含巨集的專案從 Visual Studio 2008 或更早版本移轉到 Visual Studio 2010，Visual Studio 會將巨集轉換成對等的目前巨集。 較新版本的 Visual Studio 無法將專案從 Visual Studio 2008 和更早版本轉換為新的專案類型。 您必須用兩個步驟來轉換這些專案；首先，將它們轉換成 Visual Studio 2010，然後將結果轉換成您的 Visual Studio 較新版本。 如需詳細資訊，請參閱[潛在升級問題概觀](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)。

|巨集|描述|
|-----------|-----------------|
|**$(InputDir)**|(已移轉。)輸入檔的目錄 (定義為磁碟機 + 路徑)，尾端有反斜線 '\\'。 如果專案是輸入，這個巨集就相當於 **$(ProjectDir)**。|
|**$(InputExt)**|(已移轉。)輸入檔的副檔名。 副檔名前面有 '.'。 如果專案是輸入，這個巨集就相當於 **$(ProjectExt)**。 對於原始程式檔 ，這是 **%(Extension)**。|
|**$(InputFileName)**|(已移轉。)輸入檔的檔案名稱 (定義為主檔名 + 副檔名)。 如果專案是輸入，這個巨集就相當於 **$(ProjectFileName)**。 對於原始程式檔 ，這是 **%(Identity)**。|
|**$(InputName)**|(已移轉。)輸入檔的主檔名。 如果專案是輸入，這個巨集就相當於 **$(ProjectName)**。 對於原始程式檔 ，這是 **%(Filename)**。|
|**$(InputPath)**|(已移轉。)輸入檔的絕對路徑名稱 (定義為磁碟機 + 路徑 + 主檔名 + 副檔名)。 如果專案是輸入，這個巨集就相當於 **$(ProjectPath)**。 對於原始程式檔 ，這是 **%(FullPath)**。|
|**$(ParentName)**|包含這個專案項目的項目名稱。 這會是父資料夾名稱或專案名稱。|
|**$(SafeInputName)**|做為有效類別名稱、不包含副檔名的檔案名稱。 這個屬性並沒有對等項目。|
|**$(SafeParentName)**|有效名稱格式的直接父代名稱。 例如，表單是 .resx 檔案的父代。 這個屬性並沒有對等項目。|
|**$(SafeRootNamespace)**|專案精靈會加入程式碼的命名空間名稱。 這個命名空間名稱只會包含有效 C++ 識別項允許的字元。 這個屬性並沒有對等項目。|

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建置 C++ 專案](../ide/building-cpp-projects-in-visual-studio.md)
- [Visual C++ 移植和升級指南](../porting/visual-cpp-porting-and-upgrading-guide.md)
- [潛在升級問題概觀](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
