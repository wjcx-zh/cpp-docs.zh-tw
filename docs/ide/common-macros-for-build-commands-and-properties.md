---
title: "建置命令和屬性的巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles"
  - "VC.Project.VCCLCompilerTool.XMLDocumentationFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "$(ConfigurationName) 巨集"
  - "$(DevEnvDir) 巨集"
  - "$(FrameworkDir) 巨集"
  - "$(FrameworkSDKDir) 巨集"
  - "$(FrameworkVersion) 巨集"
  - "$(FxCopDir) 巨集"
  - "$(Inherit) 巨集"
  - "$(InputDir) 巨集"
  - "$(InputExt) 巨集"
  - "$(InputFileName) 巨集"
  - "$(InputName) 巨集"
  - "$(InputPath) 巨集"
  - "$(IntDir) 巨集"
  - "$(NoInherit) 巨集"
  - "$(OutDir) 巨集"
  - "$(ParentName) 巨集"
  - "$(PlatformName) 巨集"
  - "$(ProjectDir) 巨集"
  - "$(ProjectExt) 巨集"
  - "$(ProjectFileName) 巨集"
  - "$(ProjectName) 巨集"
  - "$(ProjectPath) 巨集"
  - "$(References) 巨集"
  - "$(RemoteMachine) 巨集"
  - "$(RootNamespace) 巨集"
  - "$(SafeRootNamespace) 巨集"
  - "$(SolutionDir) 巨集"
  - "$(SolutionExt) 巨集"
  - "$(SolutionFileName) 巨集"
  - "$(SolutionName) 巨集"
  - "$(SolutionPath) 巨集"
  - "$(StopEvaluating) 巨集"
  - "$(TargetDir) 巨集"
  - "$(TargetExt) 巨集"
  - "$(TargetFileName) 巨集"
  - "$(TargetName) 巨集"
  - "$(TargetPath) 巨集"
  - "$(VCInstallDir) 巨集"
  - "$(VSInstallDir) 巨集"
  - "$(WebDeployPath) 巨集"
  - "$(WebDeployRoot) 巨集"
  - "建置巨集 [C++]"
  - "組建 [C++], 巨集"
  - "ConfigurationName 巨集 $(ConfigurationName)"
  - "DevEnvDir 巨集 $(DevEnvDir)"
  - "FrameworkDir 巨集 $(FrameworkDir)"
  - "FrameworkSDKDir 巨集 $(FrameworkSDKDir)"
  - "FrameworkVersion 巨集 $(FrameworkVersion)"
  - "FxCopDir 巨集 $(FxCopDir)"
  - "Inherit 巨集 $(Inherit)"
  - "InputDir 巨集 $(InputDir)"
  - "InputExt 巨集 $(InputExt)"
  - "InputFileName 巨集 $(InputFileName)"
  - "InputName 巨集 $(InputName)"
  - "InputPath 巨集 $(InputPath)"
  - "IntDir 巨集 $(IntDir)"
  - "巨集 [C++], 建置巨集"
  - "NoInherit 巨集 $(NoInherit)"
  - "OutDir 巨集 $(OutDir)"
  - "ParentName 巨集 $(ParentName)"
  - "PlatformName 巨集 $(PlatformName)"
  - "ProjectDir 巨集 $(ProjectDir)"
  - "ProjectExt 巨集 $(ProjectExt)"
  - "ProjectFileName 巨集 $(ProjectFileName)"
  - "ProjectName 巨集 $(ProjectName)"
  - "ProjectPath 巨集 $(ProjectPath)"
  - "屬性 [C++], 建置屬性巨集"
  - "References 巨集 $(References)"
  - "RemoteMachine 巨集 $(RemoteMachine)"
  - "RootNamespace 巨集 $(RootNamespace)"
  - "SafeRootNamespace 巨集 $(SafeRootNamespace)"
  - "SolutionDir 巨集 $(SolutionDir)"
  - "SolutionExt 巨集 $(SolutionExt)"
  - "SolutionFileName 巨集 $(SolutionFileName)"
  - "SolutionName 巨集 $(SolutionName)"
  - "SolutionPath 巨集 $(SolutionPath)"
  - "StopEvaluating 巨集 $(StopEvaluating)"
  - "TargetDir 巨集 $(TargetDir)"
  - "TargetExt 巨集 $(TargetExt)"
  - "TargetFileName 巨集 $(TargetFileName)"
  - "TargetName 巨集 $(TargetName)"
  - "TargetPath 巨集 $(TargetPath)"
  - "VCInstallDir 巨集 $(VCInstallDir)"
  - "VSInstallDir 巨集 $(VSInstallDir)"
  - "WebDeployPath 巨集 $(WebDeployPath)"
  - "WebDeployRoot 巨集 $(WebDeployRoot)"
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# 建置命令和屬性的巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在接受字串的專案 \[屬性頁\] 對話方塊的任何位置使用這些巨集。 這些巨集不區分大小寫。  
  
 若要顯示目前可用的巨集，請在屬性名稱右邊的資料行中，按一下下拉箭號。 如果 \[編輯\] 可以使用，請按一下它，再按一下 \[編輯\] 對話方塊中的 \[巨集\]。 如需詳細資訊，請參閱 [屬性頁](../ide/property-pages-visual-cpp.md) 的 **Specifying User\-Defined Values** 一節。  
  
 標記為「已取代」的巨集無法再使用，或者已由同等[項目中繼資料巨集](../Topic/ItemMetadata%20Element%20\(MSBuild\).md) \(**%\(***名稱***\)**\) 取代。 標示為「已取代；已移轉」的巨集也已經被取代。 另外，如果包含巨集的專案從 Visual Studio 2008 移轉，Visual Studio 會將巨集轉換成對等的目前巨集。  
  
|巨集|描述|  
|--------|--------|  
|**$\(RemoteMachine\)**|設定為偵錯屬性頁的 **Remote Machine**  屬性值。 如需詳細資訊，請參閱[變更 C\/C\+\+ 偵錯組態的專案設定](../Topic/Project%20Settings%20for%20a%20C++%20Debug%20Configuration.md)。|  
|**$\(Configuration\)**|目前的專案組態名稱 \(例如 "Debug"\)。|  
|**$\(Platform\)**|目前的專案平台名稱 \(例如 "Win32"\)。|  
|**$\(ParentName\)**|\(已取代。\) 包含這個專案項目的項目名稱。 這會是父資料夾名稱或專案名稱。|  
|**$\(RootNameSpace\)**|包含應用程式的命名空間 \(如果有的話\)。|  
|**$\(IntDir\)**|為中繼檔案指定的目錄路徑。 如果這是相對路徑，前往這個路徑的中繼檔案會附加在專案目錄的後面。 這個路徑應該有尾端斜線。 這可以解析 **Intermediate Directory** 屬性的值。 請勿使用 **$\(OutDir\)** 定義這個屬性。|  
|**$\(OutDir\)**|輸出檔案目錄的路徑。 如果這是相對路徑，前往這個路徑的輸出檔案會附加在專案目錄的後面。 這個路徑應該有尾端斜線。 這可以解析 **Output Directory** 屬性的值。 請勿使用 **$\(IntDir\)** 定義這個屬性。|  
|**$\(DevEnvDir\)**|Visual Studio 的安裝目錄 \(定義為磁碟機 \+ 路徑\)，尾端有反斜線 '\\'。|  
|**$\(InputDir\)**|\(已被取代；已移轉。\) 輸入檔的目錄 \(定義為磁碟機 \+ 路徑\)，尾端有反斜線 '\\'。 如果專案是輸入，這個巨集就相當於 **$\(ProjectDir\)**。|  
|**$\(InputPath\)**|\(已被取代；已移轉。\) 輸入檔的絕對路徑名稱 \(定義為磁碟機 \+ 路徑 \+ 主檔名 \+ 副檔名\)。 如果專案是輸入，這個巨集就相當於 **$\(ProjectPath\)**。|  
|**$\(InputName\)**|\(已被取代；已移轉。\) 輸入檔的主檔名。 如果專案是輸入，這個巨集就相當於 **$\(ProjectName\)**。|  
|**$\(InputFileName\)**|\(已被取代；已移轉。\) 輸入檔的檔案名稱 \(定義為主檔名 \+ 副檔名\)。 如果專案是輸入，這個巨集就相當於 **$\(ProjectFileName\)**。|  
|**$\(InputExt\)**|\(已被取代；已移轉。\) 輸入檔的副檔名。 副檔名前面有 '.'。 如果專案是輸入，這個巨集就相當於 **$\(ProjectExt\)**。|  
|**$\(ProjectDir\)**|專案的目錄 \(定義為磁碟機 \+ 路徑\)，尾端有反斜線 '\\'。|  
|**$\(ProjectPath\)**|專案的絕對路徑名稱 \(定義為磁碟機 \+ 路徑 \+ 主檔名 \+ 副檔名\)。|  
|**$\(ProjectName\)**|專案的主檔名。|  
|**$\(ProjectFileName\)**|專案的檔案名稱 \(定義為名稱 \+ 副檔名\)。|  
|**$\(ProjectExt\)**|專案的副檔名。 副檔名前面有 '.'。|  
|**$\(SolutionDir\)**|解決方案的目錄 \(定義為磁碟機 \+ 路徑\)，尾端有反斜線 '\\'。|  
|**$\(SolutionPath\)**|解決方案的絕對路徑名稱 \(定義為磁碟機 \+ 路徑 \+ 主檔名 \+ 副檔名\)。|  
|**$\(SolutionName\)**|解決方案的主檔名。|  
|**$\(SolutionFileName\)**|解決方案的檔案名稱 \(定義為主檔名 \+ 副檔名\)。|  
|**$\(SolutionExt\)**|解決方案的副檔名。 副檔名前面有 '.'。|  
|**$\(TargetDir\)**|建置的主要輸出檔目錄 \(定義為磁碟機 \+ 路徑\)，尾端有反斜線 '\\'。|  
|**$\(TargetPath\)**|建置的主要輸出檔絕對路徑名稱 \(定義為磁碟機 \+ 路徑 \+ 主檔名 \+ 副檔名\)。|  
|**$\(TargetName\)**|建置的主要輸出檔主檔名。|  
|**$\(TargetFileName\)**|建置的主要輸出檔檔案名稱 \(定義為主檔名 \+ 副檔名\)。|  
|**$\(TargetExt\)**|建置的主要輸出檔副檔名。 副檔名前面有 '.'。|  
|**$\(VSInstallDir\)**|Visual Studio 安裝所在目錄。<br /><br /> 這個屬性包含的目標 Visual Studio 版本，可能和主機 Visual Studio 不一樣。 例如，使用 `$(PlatformToolset) = v110` 建置時，**$\(VSInstallDir\)** 會包含 Visual Studio 2012 安裝的路徑。|  
|**$\(VCInstallDir\)**|Visual C\+\+ 安裝所在目錄。<br /><br /> 這個屬性包含的目標 Visual C\+\+ 版本，可能和主機 Visual Studio 不一樣。 例如，使用 `$(PlatformToolset) = v90` 建置時，**$\(VCInstallDir\)** 會包含 Visual C\+\+ 2008 安裝的路徑。|  
|**$\(FrameworkDir\)**|.NET Framework 安裝所在目錄。|  
|**$\(FrameworkVersion\)**|Visual Studio 使用的 .NET framework 版本。 結合了 **$\(FrameworkDir\)**，Visual Studio 使用的 .NET Framework 版本完整路徑。|  
|**$\(FrameworkSDKDir\)**|.NET Framework 安裝所在目錄。 .NET Framework 可能已安裝為 Visual Studio 的一部分或另行安裝。|  
|**$\(WebDeployPath\)**|從 Web 部署根目錄到專案輸出所屬根目錄的相對路徑。 傳回 <xref:Microsoft.VisualStudio.VCProjectEngine.VCWebDeploymentTool.RelativePath%2A> 的相同值。|  
|**$\(WebDeployRoot\)**|**\<localhost\>** 位置的絕對路徑。 例如，c:\\inetpub\\wwwroot。|  
|**$\(SafeParentName\)**|\(已取代。\) 有效名稱格式的直接父代名稱。 例如，表單是 .resx 檔案的父代。|  
|**$\(SafeInputName\)**|\(已取代。\) 做為有效類別名稱、不包含副檔名的檔案名稱。|  
|**$\(SafeRootNamespace\)**|\(已取代。\) 專案精靈會加入程式碼的命名空間名稱。 這個命名空間名稱只會包含有效 C\+\+ 識別項允許的字元。|  
|**$\(FxCopDir\)**|fxcop.cmd 檔案的路徑。 不是所有 Visual C\+\+ 版本都安裝 fxcop.cmd 檔案。|  
  
## 請參閱  
 [在 Visual Studio 中建置 C\+\+ 專案](../ide/building-cpp-projects-in-visual-studio.md)