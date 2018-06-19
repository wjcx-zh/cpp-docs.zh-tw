---
title: MSBuild （Visual c + +） 概觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae6e6d826f4bc1e8c9ab6cc28686e4ad1e6e3b02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379259"
---
# <a name="msbuild-visual-c-overview"></a>MSBuild (Visual C++) 概觀  
  
MSBuild 是標準的建置 Visual c + + 專案的系統。 當您建置 Visual Studio 整合式的開發環境 (IDE) 中的專案時，它會使用 msbuild.exe 工具、 XML 架構的專案檔，以及選擇性的設定檔。 雖然您可以使用 msbuild.exe 和命令列上的專案檔案，IDE 會提供使用者介面，讓您更輕鬆地設定和建置專案。 本概觀說明 Visual c + + 如何使用 MSBuild 系統。  
  
## <a name="prerequisites"></a>必要條件  
  
閱讀下列文件的相關 MSBuild。  
  
- [ MSBuild](/visualstudio/msbuild/msbuild)  
 MSBuild 概念的概觀。  
  
- [MSBuild 參考](/visualstudio/msbuild/msbuild-reference)  
 MSBuild 系統的相關參考資訊。  
  
- [專案檔案結構描述參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)  
 列出的 MSBuild XML 結構描述項目，和其屬性，以及父和子元素。 請特別注意[ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild)， [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild)，[目標](/visualstudio/msbuild/target-element-msbuild)，和[工作](/visualstudio/msbuild/task-element-msbuild)項目。  
  
- [命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)  
 描述的命令列引數和選項可讓您使用 msbuild.exe。  
  
- [工作參考](/visualstudio/msbuild/msbuild-task-reference)  
 描述 MSBuild 工作。 特別注意這些工作，Visual c + + 特有： [BscMake 工作](/visualstudio/msbuild/bscmake-task)， [CL 工作](/visualstudio/msbuild/cl-task)， [CPPClean 工作](/visualstudio/msbuild/cppclean-task)， [LIB 工作](/visualstudio/msbuild/lib-task)， [任務連結](/visualstudio/msbuild/link-task)， [MIDL 工作](/visualstudio/msbuild/midl-task)， [MT 工作](/visualstudio/msbuild/mt-task)， [RC 工作](/visualstudio/msbuild/rc-task)， [SetEnv 工作](/visualstudio/msbuild/setenv-task)， [VCMessage 工作](/visualstudio/msbuild/vcmessage-task)， [XDCMake 工作](/visualstudio/msbuild/xdcmake-task)， [XSD 工作](/visualstudio/msbuild/xsd-task)。  
  
## <a name="msbuild-on-the-command-line"></a>MSBuild 命令列上  
  
下列陳述式從[MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)說明 msbuild.exe 工具會隱含或明確*project_file*引數 （Visual c + + 專案.vcxproj 檔案）及零個或更多命令列*選項*引數。  
  
> **msbuild.exe** [ *project_file* ] [*選項*]  
  
使用 **/目標**(或 **/t**) 和 **/property** (或 **/p**) 命令列選項來覆寫特定的屬性和目標專案檔中指定。  
  
專案檔的必要功能是指定*目標*，這是套用至您的專案，並輸入和輸出執行這項操作所需的特定作業。 專案檔可以指定一或多個目標，可以包含預設目標。  
  
每個目標包含一或多個序列的*工作*。 每項工作會以.NET Framework 類別，其中包含一個可執行的命令。 例如， [CL 工作](/visualstudio/msbuild/cl-task)包含[cl.exe](../build/reference/compiling-a-c-cpp-program.md)命令。  
  
A*工作參數*類別 」 工作的屬性，且通常代表可執行命令的命令列選項。 例如，`FavorSizeOrSpeed`參數`CL`工作都會對應到 **/Os**和 **/Ot**編譯器選項。  
  
額外的工作參數支援 MSBuild 基礎結構。 例如，`Sources`工作參數會指定一組可供其他工作的工作。 如需 MSBuild 工作的詳細資訊，請參閱[工作參考](/visualstudio/msbuild/msbuild-task-reference)。  
  
大部分工作都需要輸入和輸出，例如檔案名稱、 路徑和字串、 數值或布林參數。 例如，常見的輸入是.cpp 來編譯原始程式檔的名稱。 重要的輸入的參數是字串，指定之組建組態與平台，例如 「 偵錯\|Win32"。 輸入和輸出由一或多個使用者定義的 XML`Item`內的項目`ItemGroup`項目。  
  
專案檔也可以指定使用者定義*屬性*和`ItemDefinitionGroup`*項目*。 屬性和項目形成可用來當作在組建中變數的名稱/值組。 定義一組的名稱元件*巨集*，並宣告值元件*巨集值*。 使用 $ 來存取屬性巨集 (*名稱*) 表示法和項目巨集使用存取 %(*名稱*) 標記法。  
  
在專案檔中的其他 XML 項目可以測試巨集，然後有條件地設定的任何巨集中的值或控制執行的組建。 若要產生的建構，例如路徑和檔案名稱可以串連巨集名稱和常值字串。 在命令列， **/property**選項設定，或覆寫專案屬性。 在命令列上，不能參考項目。  
  
MSBuild 系統之前，或另一個目標之後，可以有條件地執行目標。 此外，系統可以建置目標會耗用檔案是否比更新的檔案，它會發出為基礎的目標。  
  
## <a name="msbuild-in-the-ide"></a>在 IDE 的 MSBuild  
  
當您在 IDE 中設定專案屬性，並儲存專案，Visual c + + 專案將設定寫入專案檔。 專案檔包含對您的專案，都是唯一的設定，但它不包含建置您的專案所需的所有設定。 專案檔包含`Import`項目包含的其他網路*支援檔案。* 支援檔案包含其餘的屬性、 目標和建置專案所需的設定。  
  
大部分的目標和支援檔案中的屬性存在單獨來實作組建系統。 下列章節會討論一些有用的目標和您可以指定在 MSBuild 命令列的屬性。 若要探索更多的目標和內容，瀏覽的支援檔案的目錄中的檔案。  
  
### <a name="support-file-directories"></a>支援的檔案目錄  
  
根據預設，主要的 Visual c + + 支援檔案位於下列目錄中。 Microsoft Visual Studio 下的目錄會使用 Visual Studio 2017 和更新版本中，而 Visual Studio 2015 和較早版本所使用 MSBuild 下的目錄。  
  
|Directory|描述|  
|---------------|-----------------|  
|*磁碟機*: \Program Files *(x86)* \Microsoft Visual Studio\\*年*\\*edition*\Common7\IDE\VC\VCTargets\ <br /><br />*磁碟機*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp (x86) \v4.0\\*版本*\ |包含主要的目標檔案 (.targets) 和屬性檔案 (.props) 所使用的目標。 根據預設，$(VCTargetsPath) 巨集，請參考此目錄。|  
|*磁碟機*: \Program Files *(x86)* \Microsoft Visual Studio\\*年*\\*edition*\Common7\IDE\VC\VCTargets\平台\\*平台*\ <br /><br />*磁碟機*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*版本*\Platforms\\*平台*\ |包含目標和它的上層目錄中的屬性會覆寫特定平台目標和屬性檔案。 這個目錄也會包含 DLL 可定義此目錄中的目標所使用的工作。<br /><br /> *平台*預留位置代表 ARM、 Win32、 或 x64 子目錄。|  
|*磁碟機*: \Program Files *(x86)* \Microsoft Visual Studio\\*年*\\*edition*\Common7\IDE\VC\VCTargets\平台\\*平台*\PlatformToolsets\\*工具組*\ <br /><br />*磁碟機*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*版本*\Platforms\\*平台*\PlatformToolsets\\*工具組*\ <br /><br />*磁碟機*: \Program Files *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*平台*\PlatformToolsets\\*工具組*\ |包含啟用產生 Visual c + + 應用程式，使用指定的組建目錄*工具組*。<br /><br /> *年*和*edition* Visual Studio 2017 和更新版本中所使用的預留位置。 *版本*預留位置為 V110 for Visual Studio 2012、 V120 Visual Studio 2013 或 Visual Studio 2015 的 V140。 *平台*預留位置代表 ARM、 Win32、 或 x64 子目錄。 *工具組*預留位置代表工具組子目錄，例如，以建置 Windows 應用程式使用的 Visual Studio 2015 工具組，建置 Windows xp 使用 Visual Studio 2013 的工具組或以 v110_wp80 v120_xp v140使用 Visual Studio 2012 的工具組，建置 Windows Phone 8.0 應用程式。<br /><br />包含啟用的組建，以產生 Visual c + + 2008年或 Visual c + + 2010年應用程式的目錄路徑不包含*版本*，而*平台*預留位置代表Itanium、 Win32、 或 x64 子目錄。 *工具組*預留位置代表 v90 或 v100 工具組子目錄。|  
  
### <a name="support-files"></a>支援檔案  
  
支援檔案目錄包含這些副檔名的檔案：  
  
|副檔名|描述|  
|---------------|-----------------|  
|.targets|包含`Target`指定目標所執行的工作的 XML 項目。 也可能包含`PropertyGroup`， `ItemGroup`， `ItemDefinitionGroup`，和使用者定義`Item`項目，可用來將檔案和命令列選項指派給工作參數。<br /><br /> 如需詳細資訊，請參閱[目標項目 (MSBuild)](/visualstudio/msbuild/target-element-msbuild)。|  
|.props|包含`Property Group`和使用者定義`Property`指定在建置期間所使用的檔案和參數設定的 XML 項目。<br /><br /> 也可能包含`ItemDefinitionGroup`和使用者定義`Item`指定其他設定的 XML 項目。 定義項目定義群組中的項目類似內容，但不能從命令列存取。 Visual c + + 專案檔通常會使用而非屬性項目來代表設定。<br /><br /> 如需詳細資訊，請參閱[ItemGroup 項目 (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild)， [ItemDefinitionGroup 項目 (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)，和[item 項目 (MSBuild)](/visualstudio/msbuild/item-element-msbuild)。|  
|.xml|包含宣告和初始化 IDE 使用者介面項目，例如屬性工作表和屬性頁，以及文字方塊和清單方塊控制項的 XML 項目。<br /><br /> IDE、 不 MSBuild，直接支援的.xml 檔案。 不過，IDE 屬性的值會指派給組建屬性和項目。<br /><br /> 大部分的.xml 檔案是地區設定特定子目錄中。 例如，英文-美國地區的檔案位於 $(VCTargetsPath) \1033\\。|  
  
## <a name="user-targets-and-properties"></a>使用者目標和內容  
  
若要最有效地使用 MSBuild 命令列上，這有助於了哪些內容和目標很有用而且相關。 大部分的內容和目標協助實作 Visual c + + 建置系統，並因此不相關的使用者。 本章節描述一些值得使用者導向的內容和目標。  

### <a name="platformtoolset-property"></a>PlatformToolset 屬性  
  
`PlatformToolset`屬性會判斷組建中使用的 Visual c + + 工具組。 根據預設，會使用目前的工具組。 當設定這個屬性時，以形成包含建置在特定平台的專案所需的屬性和目標檔案的目錄路徑的常值字串串連屬性的值。 必須安裝平台工具組，使用該平台工具組版本來建立。  
  
例如，設定`PlatformToolset`屬性`v140`建置應用程式中使用 Visual c + + 2015年工具和程式庫：  
  
`msbuild myProject.vcxproj /p:PlatformToolset=v140`  
  
### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture 屬性  
  
`PreferredToolArchitecture`屬性會決定是否使用 32 位元或 64 位元編譯器和工具在組建中。 這個屬性不會影響輸出平台架構或組態。 根據預設，MSBuild 會使用 x86 版本的編譯器和工具，如果沒有設定這個屬性。  
  
例如，設定`PreferredToolArchitecture`屬性`x64`使用 64 位元編譯器和工具來建置應用程式：  
  
`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>UseEnv 屬性  
  
根據預設，目前專案的平台專屬設定會覆寫的路徑、 INCLUDE、 LIB、 LIBPATH、 設定及平台的環境變數。 設定`UseEnv`屬性`true`保證不會覆寫環境變數。  
  
`msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>目標  
  
有數百個中的 Visual c + + 支援檔案的目標。 不過，大部分都是可以忽略使用者的系統導向目標。 大部分的系統目標都會加上底線 (_)，或開頭為"PrepareFor 」、 「 計算 」、 「 之前 」，「 之後 」，「 之前 」，或"Post"的名稱。  
  
下表列出數個實用的使用者導向目標。  
  
|目標|描述|  
|------------|-----------------|  
|BscMake|執行 Microsoft Browse Information Maintenance Utility 工具 bscmake.exe。|  
|組建|建置專案。<br /><br /> 這是預設的目標專案。|  
|ClCompile|Visual c + + 編譯器工具會執行 cl.exe。|  
|清除|刪除暫存檔和中繼組建檔案。|  
|Lib|執行 Microsoft 32 位元程式庫管理員工具 lib.exe。|  
|連結|執行 Visual c + + 連結器工具 link.exe。|  
|ManifestResourceCompile|擷取從資訊清單資源的清單，然後執行 Microsoft Windows 資源編譯器工具 rc.exe。|  
|Midl|執行 Microsoft 介面定義語言 (MIDL) 編譯器工具 midl.exe。|  
|重建|會清除，然後建置您的專案。|  
|ResourceCompile|執行 Microsoft Windows 資源編譯器工具 rc.exe。|  
|XdcMake|執行 XML 文件工具 xdcmake.exe。|  
|Xsd|執行 XML 結構描述定義工具 xsd.exe。|  
  
## <a name="see-also"></a>另請參閱  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
