---
title: .vcxproj 和.props 檔案結構
ms.date: 09/18/2018
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 3b7c7bdad8848a3755db4ea565117459c72e939b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317116"
---
# <a name="vcxproj-and-props-file-structure"></a>.vcxproj 和.props 檔案結構

[MSBuild](../msbuild-visual-cpp.md) 是 Visual Studio 中的預設專案系統；當您在 Visual C++ 中選擇 [檔案] > [新增專案] 時，您會建立 MSBuild 專案，並將其設定儲存在副檔名為 `.vcxproj` 的 XML 專案檔中。 專案檔也可能會匯入可儲存設定的 .props 檔案和 .targets 檔案。 在大部分情況下，您永遠不需要手動編輯專案檔；事實上，除非您充分了解 MSBuild，否則不應該手動編輯它。 可能的話您應該使用 Visual Studio 屬性頁來修改專案設定 (請參閱[設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。 不過，在某些情況下，您可能需要手動修改專案檔或屬性工作表。 為了進行這些情況，本文包含檔案結構的基本資訊。

**重要：**

如果您選擇手動編輯 .vcxproj 檔案，請注意下列重點：

1. 檔案的結構必須遵循指定格式，如本文所述。

1. Visual C++ 專案系統目前不支援專案項目中有萬用字元。 例如，不支援：

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. Visual C++ 專案系統目前不支援專案項目路徑中有巨集。 例如，不支援：

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   「不支援」表示不保證巨集適用於 IDE 中的所有作業。 不會在不同的組態中變更其值的巨集應可運作，但若有某個項目移至不同的篩選條件或專案，則可能不會保留。 會在不同的組態中變更其值的巨集將會造成問題，因為 IDE 不預期專案項目路徑會隨著專案組態的不同而改變。

1. 為了在 [專案屬性] 對話方塊中編輯時，能夠正確地新增、移除或修改專案屬性，檔案必須針對每個專案組態包含不同的群組，而且條件的格式必須如下：

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. 您必須使用屬性規則檔中所指定的正確標籤，來指定群組中的每個屬性。 如需詳細資訊，請參閱[屬性頁 XML 規則檔](property-page-xml-files.md)。

## <a name="vcxproj-file-elements"></a>.vcxproj 檔案項目

您可以使用任何文字或 XML 編輯器來檢查 .vcxproj 檔案的內容。 若要在 Visual Studio 中檢視，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後依序選擇 [卸載專案] 和 [編輯 Foo.vcxproj]。

首先需要注意的是，最上層項目會依特定順序顯示。 例如：

- 大多數屬性群組和和項目定義群組會在匯入 Microsoft.Cpp.Default.props 之後出現。

- 所有目標都會匯入檔案結尾。

- 有多個屬性群組，各有唯一的標籤，而且會依特定順序出現。

專案檔中的項目順序很重要，因為 MSBuild 是以循序評估模型為基礎。  如果您的專案檔 (包括所有匯入的 .props 和 .targets 檔案) 是由屬性的多個定義所組成，最後一個定義會覆寫之前的定義。 在下列範例中，由於 MSBuild 引擎在其評估期間最後遇到值 "xyz"，因此會在編譯期間設定此值。

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

下列程式碼片段顯示最小 .vcxproj 檔案。 Visual Studio 所產生的任何 .vcxproj 檔案都會包含這些最上層 MSBuild 項目並依此順序顯示 (但可能包含每個這類最上層項目的多個複本)。 請注意，`Label` 屬性是僅供 Visual Studio 用作編輯指示的任意標記，沒有其他任何功能。

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
  <ItemGroup Label="ProjectConfigurations" />
  <PropertyGroup Label="Globals" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup Label="Configuration" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings" />
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets" />
</Project>
```

下列各節描述每個項目的用途，以及依此方式排序的原因：

### <a name="project-element"></a>Project 項目

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` 是根節點。 它指定要使用的 MSBuild 版本，以及此檔案傳遞至 MSBuild.exe 時要執行的預設目標。

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations ItemGroup 項目

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` 包含專案組態描述。 例如，Debug|Win32、Release|Win32、Debug|ARM 等。 許多專案設定會專屬於某個組態。 例如，您可能想要設定發行組建的最佳化屬性，而不是偵錯組建。

`ProjectConfigurations` 項目群組不會在建置時間使用。 Visual Studio IDE 需要它才能載入專案。 此項目群組可移至 .props 檔案及匯入 .vcxproj 檔案。 不過，在此情況下，如果您需要新增或移除組態，您必須手動編輯 .props 檔案；您無法使用 IDE。

### <a name="projectconfiguration-elements"></a>ProjectConfiguration 項目

下列程式碼片段顯示專案組態。 在此範例中，'Debug|x64' 是組態名稱。 專案組態名稱的格式必須是 $(Configuration)|$(Platform)。 專案組態節點可以有兩個屬性：組態與平台。 當組態為使用中時，即會自動使用此處指定的值設定這些屬性。

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

IDE 預期會針對用於所有 ProjectConfiguration 項目的任何 Configuration 和 Platform 值組合，尋找專案組態。 這通常表示專案可能會有符合此需求的無意義專案組態。 例如，如果專案具有下列組態：

- Debug|Win32

- Retail|Win32

- Special 32-bit Optimization|Win32

則必須同時具有下列組態，即使 "Special 32-bit Optimization" 對 x64 無意義也一樣：

- Debug|x64

- Retail|x64

- Special 32-bit Optimization|x64

您可以在 [方案組態管理員] 中，停用任何組態的建置和部署命令。

### <a name="globals-propertygroup-element"></a>Globals PropertyGroup 項目

```xml
<PropertyGroup Label="Globals" />
```

`Globals` 包含專案層級設定，例如 ProjectGuid、RootNamespace 和 ApplicationType/ ApplicationTypeRevision。 最後兩項通常會定義目標 OS。 一個專案只能以單一 OS 為目標，因為參考和專案項目目前不能有條件。 這些屬性通常不會在專案檔中的其他位置覆寫。 此群組與組態無關，因此專案檔中通常只有一個 Globals 群組。

### <a name="microsoftcppdefaultprops-import-element"></a>Microsoft.Cpp.default.props Import 項目

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Microsoft.Cpp.default.props** 屬性工作表隨附於 Visual Studio，而且無法修改。 它包含專案的預設設定。 視 ApplicationType 而定，預設值可能會有所不同。

### <a name="configuration-propertygroup-elements"></a>Configuration PropertyGroup 項目

```xml
<PropertyGroup Label="Configuration" />
```

`Configuration` 屬性群組具有附加的組態條件 (例如 `Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`) 和多個複本，每個組態各一個。 此屬性群組會裝載專為特定組態設定的屬性。 組態屬性包含 PlatformToolset，同時也會控制 **Microsoft.Cpp.props** 中是否包含系統屬性工作表。 例如，如果您定義屬性 `<CharacterSet>Unicode</CharacterSet>`，則會包含系統屬性工作表 **microsoft.Cpp.unicodesupport.props**。 如果您檢查 **Microsoft.Cpp.props**，您會看到此行：`<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`。

### <a name="microsoftcppprops-import-element"></a>Microsoft.Cpp.props Import 項目

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

**Microsoft.Cpp.props** 屬性工作表 (直接或透過匯入) 會定義許多工具特定屬性的預設值，例如編譯器的 Optimization 和 Warning Level 屬性、MIDL 工具的 TypeLibraryName 屬性等。 它也會根據上述屬性群組中定義的組態屬性，匯入各種系統屬性工作表。

### <a name="extensionsettings-importgroup-element"></a>ExtensionSettings ImportGroup 項目

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings` 群組包含屬於組建自訂一部分之屬性工作表的匯入。 組建自訂最多可由三個檔案定義：.targets 檔案、.props 檔案和 .xml 檔案。 此匯入群組包含 .props 檔案的匯入。

### <a name="propertysheets-importgroup-elements"></a>PropertySheets ImportGroup 項目

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets` 群組包含使用者屬性工作表的匯入。 這些是您透過 Visual Studio [屬性管理員] 檢視新增的屬性工作表。 這些匯入的列出順序很重要，而且會反映在 [屬性管理員] 中。 專案檔通常會包含這種匯入群組的多個執行個體，每個專案組態各一個。

### <a name="usermacros-propertygroup-element"></a>UserMacros PropertyGroup 項目

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` 包含您建立為變數以用來自訂建置程序的屬性。 例如，您可以定義使用者巨集，將您的自訂輸出路徑定義為 $(CustomOutputPath) 並使用它來定義其他變數。 此屬性群組會裝載這類屬性。 請注意，在 Visual Studio 中，專案檔中不會填入此群組，因為 Visual C++ 不支援組態中有使用者巨集。 屬性工作表支援使用者巨集。

### <a name="per-configuration-propertygroup-elements"></a>各個組態的 PropertyGroup 項目

```xml
<PropertyGroup />
```

此屬性群組有多個執行個體，所有專案組態的每個組態各有一個。 每個屬性群組都必須附加一個組態條件。 如有任何組態遺失，[專案屬性] 對話方塊將無法正常運作。 不同於上述屬性群組，此屬性群組沒有標籤。 此群組包含專案組態層級設定。 這些設定會套用至屬於指定項目群組一部分的所有檔案。 組建自訂項目定義中繼資料會在此初始化。

此 PropertyGroup 必須接在 `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` 後面，而且前面不得有任何其他不含 Label 的 PropertyGroup (否則 [專案屬性] 編輯將無法正常運作)。

### <a name="per-configuration-itemdefinitiongroup-elements"></a>各個組態的 ItemDefinitionGroup 項目

```xml
<ItemDefinitionGroup />
```

包含項目定義。 這些定義必須與各個組態的無標籤 PropertyGroup 項目遵循相同的條件規則。

### <a name="itemgroup-elements"></a>ItemGroup 項目

```xml
<ItemGroup />
```

包含專案中的項目 (原始程式檔等)。 專案項目 (也就是規則定義視為專案項目的項目類型) 不支援條件。

中繼資料應該包含每個組態的組態條件，即使完全相同也一樣。 例如: 

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
    <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|x64’">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Visual C++ 專案系統目前不支援專案項目中有萬用字元。

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Visual C++ 專案系統目前不支援專案項目中有巨集。

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

ItemGroup 中會指定參考，而且具有下列限制：

- 參考不支援條件。

- 參考中繼資料不支援條件。

### <a name="microsoftcpptargets-import-element"></a>Microsoft.Cpp.targets Import 項目

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

定義 (直接或透過匯入) Visual C++ 目標，例如建置、清除等。

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets ImportGroup 項目

```xml
<ImportGroup Label="ExtensionTargets" />
```

此群組包含組建自訂目標檔案的匯入。

## <a name="impact-of-incorrect-ordering"></a>順序不正確的影響

Visual Studio IDE 的專案檔必須如上所述排序。 例如，當您定義屬性頁中的屬性值時，IDE 通常會將屬性定義放在具有空白標籤的屬性群組中。 這可確保帶入系統屬性工作表的預設值會由使用者定義的值所覆寫。 同樣地，目標檔案會匯入結尾，因為它們會取用以上定義的屬性，而且通常不會自行定義屬性。 同樣地，使用者屬性工作表會在系統屬性工作表之後匯入 (透過 **Microsoft.Cpp.props** 加入)。 這可確保使用者能夠覆寫由系統屬性工作表所帶入的任何預設值。

如果 .vcxproj 檔案未遵循此配置，組建結果可能會不如預期。 例如，如果您不小心在使用者定義的屬性工作表之後匯入系統屬性工作表，使用者設定將會由系統屬性工作表所覆寫。

即使是 IDE 設計階段體驗，在某種程度上也取決於項目是否正確排序。 例如，如果您的 .vcxproj 檔案沒有 `PropertySheets` 匯入群組，IDE 可能無法判斷要在何處放置使用者在 [屬性管理員] 中建立的新屬性工作表。 這可能導致使用者工作表由系統工作表所覆寫。 雖然 IDE 所使用的啟發學習法可以容忍 .vcxproj 檔案配置中的些微不一致，但強烈建議不要偏離本文稍早所示的結構。

## <a name="how-the-ide-uses-element-labels"></a>IDE 如何使用項目標籤

在 IDE 中，當您在 [一般] 屬性頁中設定 **UseOfAtl** 屬性時，它會寫入專案檔中的組態屬性群組，而相同屬性頁中的 **TargetName** 屬性會寫入各個組態的無標籤屬性群組。 Visual Studio 會查看屬性頁的 XML 檔案，以了解每個屬性寫入位置的相關資訊。 針對 [一般] 屬性頁 (假設您有英文版的 Visual Studio Enterprise Edition)，該檔案為 `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`。 屬性頁 XML 規則檔會定義 Rule 及其所有屬性的靜態資訊。 這類資訊之一是目的檔案 (寫入其值的檔案) 中 Rule 屬性的慣用位置。 專案檔項目上的 Label 屬性會指定慣用位置。

## <a name="property-sheet-layout"></a>屬性工作表配置

下列 XML 程式碼片段是屬性工作表 (.props) 檔案的最小配置。 它類似於 .vcxproj 檔案，而且可從先前的討論推斷 .props 項目的功能。

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

若要建立您自己的屬性工作表，請複製 VCTargets 資料夾中的其中一個 .props 檔案，並配合您的目的進行修改。 若是 Visual Studio 2017 Enterprise Edition，預設 VCTargets 路徑為 `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets`。

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)<br/>
[屬性頁面 XML 檔案](property-page-xml-files.md)
