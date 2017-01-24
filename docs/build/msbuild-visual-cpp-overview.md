---
title: "MSBuild (Visual C++) 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MSBuild 概觀"
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MSBuild (Visual C++) 概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MSBuild 是標準建置 Visual c + + 專案系統。 當您建置 Visual Studio 整合式的開發環境 (IDE) 中的專案時，它會使用 msbuild.exe 工具、 以 XML 為基礎的專案檔，以及選擇性的設定檔。 雖然您可以使用 msbuild.exe 和命令列上的專案檔案，IDE 會提供使用者介面，以便更輕鬆地設定及建置專案。 本概觀說明 Visual c + + 如何使用 MSBuild 系統。  
  
## <a name="prerequisites"></a>必要條件  
 閱讀關於 MSBuild 下列文件。  
  
 [MSBuild](MSBuild1.md)  
 MSBuild 概念的概觀。  
  
 [MSBuild 參考](../Topic/MSBuild%20Reference.md)  
 MSBuild 系統的相關參考資訊。  
  
 [專案檔案結構描述參考](../Topic/MSBuild%20Project%20File%20Schema%20Reference.md)  
 列出 MSBuild XML 結構描述元素，和其屬性，以及父和子元素。 請特別注意 [ItemGroup](../Topic/ItemGroup%20Element%20\(MSBuild\).md), ，[PropertyGroup](../Topic/PropertyGroup%20Element%20\(MSBuild\).md), ，[目標](../Topic/Target%20Element%20\(MSBuild\).md), ，和 [工作](../Topic/Task%20Element%20\(MSBuild\).md) 項目。  
  
 [命令列參考](../Topic/MSBuild%20Command-Line%20Reference.md)  
 描述的命令列引數和選項可讓您使用 msbuild.exe。  
  
 [工作參考](../Topic/MSBuild%20Task%20Reference.md)  
 描述 MSBuild 工作。 特別注意這些工作，Visual c + + 特有︰ [BscMake 工作](../Topic/BscMake%20Task.md), ，[CL 工作](../Topic/CL%20Task.md), ，[CPPClean 工作](../Topic/CPPClean%20Task.md), ，[LIB 工作](../Topic/LIB%20Task.md), ，[連結工作](../Topic/Link%20Task.md), ，[MIDL 工作](../Topic/MIDL%20Task.md), ，[MT 工作](../Topic/MT%20Task.md), ，[RC 工作](../Topic/RC%20Task.md), ，[SetEnv 工作](../Topic/SetEnv%20Task.md), ，[VCMessage 工作](../Topic/VCMessage%20Task.md), ，[XDCMake 工作](../Topic/XDCMake%20Task.md), ，[XSD 工作](../Topic/XSD%20Task.md)。  
  
## <a name="msbuild-on-the-command-line"></a>MSBuild 命令列上  
 下列陳述式，從 [命令列參考](../Topic/MSBuild%20Command-Line%20Reference.md) 文件說明了 msbuild.exe 工具會隱含或明確 `project file` 引數 （Visual c + + 專案.vcxproj 檔案） 以及零或其他命令列 `options`。  
  
 **msbuild.exe [** `project file` **] [** `options` **]**  
  
 使用 **/目標** (或 **/t**) 和 **/property** (或 **/p**) 命令列選項來覆寫屬性和專案檔中指定的目標。  
  
 專案檔的基本功能，就是指定 *目標*, ，這是套用至您的專案，並輸入和輸出執行這項操作所需的特定作業。 專案檔可以指定一或多個目標，可以包含預設目標。  
  
 每個目標包含一個或多個序列的 *工作*。 每一項工作會以.NET Framework 類別，其中包含一個可執行的命令。 例如， [CL 工作](../Topic/CL%20Task.md) 包含 [cl.exe](../build/reference/compiling-a-c-cpp-program.md) 命令。  
  
 A *工作參數* 類別工作的屬性，而且通常代表可執行命令的命令列選項。 例如， `FavorSizeOrSpeed` 參數 `CL` 工作都會對應到 **/Os** 和 **/Ot** 編譯器選項。  
  
 額外的工作參數支援的 MSBuild 基礎結構。 例如， `Sources` 工作參數會指定一組可供其他工作的工作。 如需 MSBuild 工作的詳細資訊，請參閱 [工作參考](../Topic/MSBuild%20Task%20Reference.md)。  
  
 大部分工作都需要輸入和輸出，例如檔案名稱、 路徑和字串、 數值或布林參數。 例如，常見的輸入是.cpp 編譯原始程式檔的名稱。 重要的輸入的參數是字串，指定組建組態與平台，比方說，「 偵錯 &#124;Win32 」。 輸入和輸出由一或多個使用者定義的 XML `Item` 中所包含的項目 `ItemGroup` 項目。  
  
 專案檔也可以指定使用者定義 *屬性* 和 *項目定義群組**項目*。 屬性和項目表單可用來做為組建中的變數名稱/值組。 定義一組的名稱元件 *巨集*, ，並宣告的值元件 *巨集值*。 屬性的巨集透過使用 $(*名稱*) 表示法和項目巨集使用存取 %(*名稱*) 標記法。  
  
 在專案檔中的其他 XML 項目可以測試巨集，然後有條件地設定巨集的值或控制組建的執行。 可以串連巨集名稱和常值字串，來產生建構，例如路徑和檔案名稱。 在命令列， **/property** 選項設定，或覆寫專案屬性。 在命令列上，不能參考項目。  
  
 MSBuild 系統之前或之後另一個目標，可以有條件地執行目標。 此外，系統可以建置目標，根據是否比檔案就會發出更新的目標使用的檔案。  
  
## <a name="msbuild-in-the-ide"></a>在 IDE 中的 MSBuild  
 當您在 IDE 中設定專案屬性，然後儲存專案時，Visual c + + 會寫入您的專案檔的專案設定。 專案檔包含對您的專案，都是唯一的設定，但不包含建置您的專案所需的所有設定。 專案檔內含 `Import` 項目包含的其他網路 *支援檔案。* 支援檔案包含其餘的屬性、 目標和建置專案所需的設定。  
  
 大部分的目標和支援檔案中的屬性存在只是要實作的建置系統。 以下章節會討論一些有用的目標和您可以在 MSBuild 命令列指定的屬性。 若要探索更多的目標和屬性，探索支援檔案目錄中的檔案。  
  
### <a name="support-file-directories"></a>支援檔案目錄  
 根據預設，主要的 Visual c + + 支援檔案位於下列目錄中。  
  
|Directory|說明|  
|---------------|-----------------|  
|*磁碟機*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*版本*\|包含主要的目標檔案 (.targets) 和屬性檔案 (.props) 所使用的目標。 根據預設，$(VCTargetsPath) 巨集，請參考此目錄。|  
|*磁碟機*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*版本*\Platforms\\*平台*\|包含平台目標與屬性之特定檔案覆寫目標和它的上層目錄中的屬性。 這個目錄也包含定義工作所使用的目標，此目錄中的.dll 檔案。<br /><br />  *平台* 預留位置代表 `ARM`, ，`Win32`, ，或 `x64` 子目錄。|  
|*磁碟機*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*版本*\Platforms\\*平台*\PlatformToolsets\\*工具組*\|包含讓建置產生 Visual c + + 應用程式，使用指定的目錄 *版本* 的工具組。<br /><br />  *平台* 預留位置代表 `ARM`, ，`Win32`, ，或 `x64` 子目錄。  *工具組* 預留位置代表建置 Windows、 Windows XP 或 Windows Phone 應用程式的工具組子目錄。|  
|*磁碟機*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\Platforms\\*平台*\PlatformToolsets\\*工具組*\|包含讓建置產生 9.0 或 Visual c + + 10.0 的應用程式的目錄。<br /><br />  *平台* 預留位置代表 `Itanium`, ，`Win32`, ，或 `x64` 子目錄。  *工具組* 預留位置代表 `v90` 或 `v100` 工具組子目錄。|  
  
### <a name="support-files"></a>支援檔案  
 支援檔案目錄包含具有下列副檔名的檔案。  
  
|副檔名|描述|  
|---------------|-----------------|  
|.targets|包含 `Target` 指定目標所執行的工作的 XML 項目。 也可能包含 `Property Group`, ，`Item Group`, ，`Item Definition Group`, ，和使用者定義 `Item` 用來將檔案和命令列選項指派給工作參數的項目。<br /><br /> 如需詳細資訊，請參閱 [目標項目 (MSBuild)](../Topic/Target%20Element%20\(MSBuild\).md)。|  
|.props|包含 `Property Group` 和使用者定義 `Property` 指定在建置期間所使用的檔案和參數設定的 XML 項目。<br /><br /> 也可能包含 `Item Definition Group` 和使用者定義 `Item` 指定其他設定的 XML 項目。 定義項目定義群組中的項目類似屬性，但不能從命令列存取。 Visual c + + 專案檔通常會使用而不是屬性的項目來代表設定。<br /><br /> 如需詳細資訊，請參閱 [ItemGroup 項目 (MSBuild)](../Topic/ItemGroup%20Element%20\(MSBuild\).md), ，[ItemDefinitionGroup 項目 (MSBuild)](../Topic/ItemDefinitionGroup%20Element%20\(MSBuild\).md), ，和 [項目 (MSBuild)](../Topic/Item%20Element%20\(MSBuild\).md)。|  
|.xml|包含 XML 宣告及初始化 IDE 使用者介面項目，如屬性工作表和屬性頁中的文字] 方塊和清單方塊控制項的項目。<br /><br /> IDE、 不 MSBuild，直接支援的.xml 檔案。 不過，IDE 屬性的值會指派給組建屬性和項目。<br /><br /> 大部分的.xml 檔案都是地區設定特定子目錄中。 例如，英文-美國地區的檔案位於 $(VCTargetsPath) \1033\\。|  
  
## <a name="user-targets-and-properties"></a>使用者目標和屬性  
 若要最有效地使用 MSBuild 命令列上，這有助於明白了哪些屬性和目標很有用而且相關。 大部分的屬性和目標協助 Visual c + + 組建系統的實作，因此並非與使用者相關。 本節說明一些值得使用者導向的屬性和目標。  
  
### <a name="platformtoolset-property"></a>PlatformToolset 屬性  
  `PlatformToolset` 屬性會判斷在組建中使用的 Visual c + + 工具組。 屬性的值會與以建置專案，以取得特定的平台所需的屬性和目標檔案所在的目錄路徑的常值字串串連。  
  
 設定 `PlatformToolset` 屬性 `v110` 使用 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] 工具和程式庫來建置應用程式。  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v110`  
  
 設定 `PlatformToolset` 屬性 `v100` 使用 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] 工具和程式庫來建置應用程式。  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v100`  
  
 設定 `PlatformToolset` 屬性 `v90` 使用 Visual c + + 2008年工具與程式庫來建置應用程式。 此屬性設為有效的電腦上必須已安裝的 Visual c + + 2008年工具組。  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v90`  
  
### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture 屬性  
  `PreferredToolArchitecture` 屬性會決定是否使用 32 位元或 64 位元編譯器和工具組建中。 這個屬性不會影響輸出平台架構或組態。 根據預設，MSBuild 會使用 x86 版本的編譯器和工具，如果這個屬性未設定，或設為任何值以外的其他 `x64`。  
  
 設定 `PreferredToolArchitecture` 屬性 `x64` 使用 64 位元編譯器和工具來建置應用程式。  
  
 `msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>UseEnv 屬性  
 根據預設，目前專案的平台特定設定覆寫路徑、 INCLUDE、 LIB、 LIBPATH、 組態和平台的環境變數。 設定 `UseEnv` 屬性 `true` 保證環境變數不會被覆寫。  
  
 `msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>目標  
 有數百個 Visual c + + 支援檔案中的目標。 不過，大部分都是可以忽略使用者的系統導向目標。 大部分的系統目標會加上底線 (_)，或開頭為"PrepareFor 」，「 運算 」、 「 之前 」，「 之後 」，「 之前 」，或"Post"的名稱。  
  
 下表列出數個值得使用者導向目標。  
  
|目標|描述|  
|------------|-----------------|  
|BscMake|執行 Microsoft 瀏覽資訊維護公用程式的工具，bscmake.exe。|  
|組建|建置專案。<br /><br /> 這是預設的目標專案。|  
|ClCompile|執行 Visual c + + 編譯器工具 cl.exe。|  
|清除|刪除暫存檔和中繼組建檔案。|  
|Lib|執行 Microsoft 32 位元程式庫管理員工具 lib.exe。|  
|連結|執行 Visual c + + 連結器工具 link.exe。|  
|ManifestResourceCompile|擷取資訊清單資源的清單，然後執行 [Microsoft Windows 資源編譯器工具 rc.exe。|  
|Midl|執行 Microsoft 介面定義語言 (MIDL) 編譯器工具 midl.exe。|  
|重建|會清除，然後建置您的專案。|  
|ResourceCompile|Microsoft Windows 資源編譯器工具會執行 rc.exe。|  
|XdcMake|執行 XML 文件工具 xdcmake.exe。|  
|Xsd|執行 XML 結構描述定義工具，xsd.exe。|  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild （Visual c + +）](../build/msbuild-visual-cpp.md)