---
title: "常見的巨集，用於建置命令和屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f96e403516d6f85804fa798d7a0c28575482ff43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="common-macros-for-build-commands-and-properties"></a>建置命令和屬性的一般巨集
根據您的安裝選項，Visual Studio 可以提供數百個巨集給您。 這些對應 MSBuild 屬性依預設，或.props 或.targets 檔案，或您的專案設定所設定。 您可以在接受字串的專案 [屬性頁]  對話方塊的任何位置使用這些巨集。 這些巨集不區分大小寫。  
  
 若要顯示目前可用的巨集，請在屬性名稱右邊的資料行中，按一下下拉箭號。 如果 [編輯]  可以使用，請按一下它，再按一下 [編輯] 對話方塊中的 [巨集] 。 如需詳細資訊，請參閱**Specifying User-Defined 值**區段[屬性頁](../ide/property-pages-visual-cpp.md)。  
  
 標記為「已取代」的巨集無法再使用，或者已由同等 [項目中繼資料巨集](/visualstudio/msbuild/itemmetadata-element-msbuild) (**%(***名稱***)**) 取代。 標示為「已取代；已移轉」的巨集也已經被取代。 另外，如果包含巨集的專案從 Visual Studio 2008 移轉，Visual Studio 會將巨集轉換成對等的目前巨集。  
  
 下表描述可用的巨集常用的子集。 此清單未全部列出。 如需如何建立和使用為.props、.targets 和.vcxproj 檔案中的巨集 MSBuild 屬性定義的詳細資訊，請參閱[MSBuild 屬性](/visualstudio/msbuild/msbuild-properties)。  
  
|巨集|描述|  
|-----------|-----------------|  
|**$ （remotemachine)**|設定為偵錯屬性頁的 **Remote Machine** 屬性值。 如需詳細資訊，請參閱 [變更 C/C++ 偵錯組態的專案設定](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) 。|  
|**$(Configuration)**|目前的專案設定名稱，例如 "Debug"。|  
|**$(Platform)**|目前專案的平台，例如"Win32"的名稱。|  
|**$ （parentname)**|(已取代。)包含這個專案項目的項目名稱。 這會是父資料夾名稱或專案名稱。|  
|**$ （rootnamespace)**|包含應用程式的命名空間 (如果有的話)。|  
|**$(IntDir)**|為中繼檔案指定的目錄路徑。 如果這是相對路徑時，中繼檔案會移至這個附加至專案目錄的路徑。 這個路徑應該有尾端斜線。 這可以解析 **Intermediate Directory** 屬性的值。 請勿使用 **$(OutDir)** 定義這個屬性。|  
|**$(OutDir)**|輸出檔案目錄的路徑。 如果這是相對路徑，前往這個路徑的輸出檔案會附加在專案目錄的後面。 這個路徑應該有尾端斜線。 這可以解析 **Output Directory** 屬性的值。 請勿使用 **$(IntDir)** 定義這個屬性。|  
|**$ （devenvdir)**|安裝 Visual Studio 的目錄 （定義為磁碟機 + 路徑），包含尾端有反斜線 '\\'。|  
|**$ （inputdir)**|(已被取代；已移轉。)（定義為磁碟機 + 路徑），輸入檔案的目錄包含尾端有反斜線 '\\'。 如果專案是輸入，這個巨集就相當於 **$(ProjectDir)**。|  
|**$ （inputpath)**|(已被取代；已移轉。)輸入檔的絕對路徑名稱 (定義為磁碟機 + 路徑 + 主檔名 + 副檔名)。 如果專案是輸入，這個巨集就相當於 **$(ProjectPath)**。|  
|**$ （inputname)**|(已被取代；已移轉。)輸入檔的主檔名。 如果專案是輸入，這個巨集就相當於 **$(ProjectName)**。|  
|**$ （inputfilename)**|(已被取代；已移轉。)輸入檔的檔案名稱 (定義為主檔名 + 副檔名)。 如果專案是輸入，這個巨集就相當於 **$(ProjectFileName)**。|  
|**$ （inputext)**|(已被取代；已移轉。)輸入檔的副檔名。 副檔名前面有 '.'。 如果專案是輸入，這個巨集就相當於 **$(ProjectExt)**。|  
|**$(ProjectDir)**|（定義為磁碟機 + 路徑），專案的目錄包含尾端有反斜線 '\\'。|  
|**$(ProjectPath)**|專案的絕對路徑名稱 (定義為磁碟機 + 路徑 + 主檔名 + 副檔名)。|  
|**$(ProjectName)**|專案的主檔名。|  
|**$(ProjectFileName)**|專案的檔案名稱 (定義為名稱 + 副檔名)。|  
|**$(ProjectExt)**|專案的副檔名。 副檔名前面有 '.'。|  
|**$ （solutiondir)**|（定義為磁碟機 + 路徑），方案的目錄包含尾端有反斜線 '\\'。 建置在 IDE 中的方案時，只定義。|  
|**$ （solutionpath)**|解決方案的絕對路徑名稱 (定義為磁碟機 + 路徑 + 主檔名 + 副檔名)。 建置在 IDE 中的方案時，只定義。|  
|**$ （solutionname)**|解決方案的主檔名。 建置在 IDE 中的方案時，只定義。|  
|**$ （solutionfilename)**|解決方案的檔案名稱 (定義為主檔名 + 副檔名)。 建置在 IDE 中的方案時，只定義。|  
|**$ （solutionext)**|解決方案的副檔名。 副檔名前面有 '.'。 建置在 IDE 中的方案時，只定義。|  
|**$ （targetdir)**|組建 （定義為磁碟機 + 路徑），主要輸出檔的目錄包含尾端有反斜線 '\\'。|  
|**$ （targetpath)**|建置的主要輸出檔絕對路徑名稱 (定義為磁碟機 + 路徑 + 主檔名 + 副檔名)。|  
|**$ （targetname)**|建置的主要輸出檔主檔名。|  
|**$ （targetfilename)**|建置的主要輸出檔檔案名稱 (定義為主檔名 + 副檔名)。|  
|**$ （targetext)**|建置的主要輸出檔副檔名。 副檔名前面有 '.'。|  
|**$(VSInstallDir)**|Visual Studio 安裝所在目錄。<br /><br /> 這個屬性包含的目標 Visual Studio 版本，可能和主機 Visual Studio 不一樣。 例如，使用 `$(PlatformToolset) = v110`建置時， **$(VSInstallDir)** 會包含 Visual Studio 2012 安裝的路徑。|  
|**$(VCInstallDir)**|Visual C++ 安裝所在目錄。<br /><br /> 這個屬性包含的目標 Visual C++ 版本，可能和主機 Visual Studio 不一樣。 例如，當使用建置`$(PlatformToolset) = v140`， **$ （vcinstalldir)**包含 Visual c + + 2015年的安裝路徑。|  
|**$(FrameworkDir)**|.NET Framework 安裝所在目錄。|  
|**$ （frameworkversion)**|Visual Studio 使用的 .NET framework 版本。 結合了 **$(FrameworkDir)**，Visual Studio 使用的 .NET Framework 版本完整路徑。|  
|**$ （frameworksdkdir)**|.NET Framework 安裝所在目錄。 .NET Framework 可能已安裝為 Visual Studio 的一部分或另行安裝。|  
|**$ （webdeploypath)**|從 Web 部署根目錄到專案輸出所屬根目錄的相對路徑。 傳回 <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A>的相同值。|  
|**$ （webdeployroot)**|位置的絕對路徑 **\<localhost >**。 例如，c:\inetpub\wwwroot。|  
|**$(SafeParentName)**|(已取代。)有效名稱格式的直接父代名稱。 例如，表單是 .resx 檔案的父代。|  
|**$(SafeInputName)**|(已取代。)做為有效類別名稱、不包含副檔名的檔案名稱。|  
|**$ （saferootnamespace)**|(已取代。)專案精靈會加入程式碼的命名空間名稱。 這個命名空間名稱只會包含有效 C++ 識別項允許的字元。|  
|**$ （fxcopdir)**|fxcop.cmd 檔案的路徑。 不是所有 Visual C++ 版本都安裝 fxcop.cmd 檔案。|  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中建置 C++ 專案](../ide/building-cpp-projects-in-visual-studio.md)