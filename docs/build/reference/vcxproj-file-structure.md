---
title: .vcxproj 和.props 檔案結構
description: C + + 原生 MSBuild 專案 .vcxproj 和. .props 檔案如何儲存專案資訊。
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 562ef0c1b371d7212f31da1917d19c012e4cbb24
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662278"
---
# <a name="vcxproj-and-props-file-structure"></a>`.vcxproj` 和 `.props` 檔結構

[MSBuild](../msbuild-visual-cpp.md)是 Visual Studio 中的預設專案系統;當您在 Visual C++ 中**選擇 [** 檔案  >  **新專案**] 時，會建立 MSBuild 專案，其設定會儲存在副檔名為的 XML 專案檔中 *`.vcxproj`* 。 專案檔也可以匯入 *`.props`* *`.targets`* 可儲存設定的檔案和檔案。

建議您只 *`.vcxproj`* 在 IDE 中建立和修改專案，並盡可能避免手動編輯。 在大多數情況下，您永遠不需要手動編輯專案檔。 可能的話，您應該使用 Visual Studio 屬性頁來修改專案設定。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

如果您需要在 IDE 中無法進行的自訂，建議您新增自訂 .props 或目標。 插入自訂的方便位置是 *`Directory.Build.props`* 和檔案 *`Directory.Build.targets`* ，這些檔案會自動匯入至所有 MSBuild 型專案。

在某些情況下，您可能仍然需要手動修改 *`.vcxproj`* 專案檔或屬性工作表。 除非您對 MSBuild 有充分的瞭解，並遵循本文中的指導方針，否則不建議您手動進行編輯。 為了讓 IDE 自動載入和更新檔案 *`.vcxproj`* ，這些檔案有幾項限制不適用於其他 MSBuild 專案檔。 它們並不是針對手動編輯所設計。 錯誤可能會導致 IDE 損毀或以非預期的方式運作。

針對手動編輯案例，此文章包含的結構和相關檔案的基本資訊 *`.vcxproj`* 。

**重要：**

如果您選擇手動編輯檔案 *`.vcxproj`* ，請注意下列事實：

- 檔案的結構必須遵循指定格式，如本文所述。

- Visual Studio c + + 專案系統目前不支援直接在專案專案中的萬用字元或清單。 例如，不支援下列表單：

   ```xml
   <ItemGroup>
     <None Include="*.txt"/>
     <ClCompile Include="a.cpp;b.cpp"/>
   </ItemGroup>
   ```

   如需專案中的萬用字元支援和可能的因應措施的詳細資訊，請參閱檔案[ `.vcxproj` 和萬用字元](vcxproj-files-and-wildcards.md)。

- Visual Studio c + + 專案系統目前不支援專案專案路徑中的宏。 例如，不支援這個表單：

   ```xml
   <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"/>
   </ItemGroup>
   ```

   「不支援」表示不保證宏適用于 IDE 中的所有作業。 未在不同設定中變更其值的宏應該可以運作，但如果專案移至不同的篩選或專案，則可能不會保留。 針對不同設定變更其值的宏將會造成問題。 這是因為 IDE 不會預期不同專案設定的專案專案路徑不同。

- 若要在 [ **專案屬性** ] 對話方塊中編輯專案時，正確地加入、移除或修改專案屬性，檔案必須包含每個專案設定的個別群組。 條件的格式必須如下：

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

- 每個屬性都必須在具有正確標籤的群組中指定，如屬性規則檔中所指定。 如需詳細資訊，請參閱[屬性頁 XML 規則檔](property-page-xml-files.md)。

## <a name="vcxproj-file-elements"></a>`.vcxproj` file 元素

您可以 *`.vcxproj`* 使用任何文字或 XML 編輯器來檢查檔案的內容。 若要在 Visual Studio 中檢視，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後依序選擇 [卸載專案]**** 和 [編輯 Foo.vcxproj]****。

首先需要注意的是，最上層項目會依特定順序顯示。 例如：

- 大多數屬性群組和和項目定義群組會在匯入 Microsoft.Cpp.Default.props 之後出現。

- 所有目標都會匯入檔案結尾。

- 有多個屬性群組，各有唯一的標籤，而且會依特定順序出現。

專案檔中的專案順序極為重要，因為 MSBuild 是以連續的評估模型為基礎。  如果您的專案檔（包括所有匯入的和檔案） *`.props`* *`.targets`* 包含屬性的多個定義，則最後一個定義會覆寫先前的定義。 在下列範例中，將會在編譯期間設定值 "xyz"，因為 MSBUild 引擎會在其評估期間最後遇到它。

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

下列程式碼片段顯示最小的檔案 *`.vcxproj`* 。 *`.vcxproj`* Visual Studio 產生的任何檔案都會包含這些最上層 MSBuild 元素。 而且它們會依此順序出現，雖然它們可能包含每個最上層元素的多個複本。 任何 `Label` 屬性都是僅供 Visual Studio 用來編輯 signposts 的任意標記; 它們沒有其他函式。

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

下列各節將說明每個專案的用途，以及如何以這種方式排序這些元素：

### <a name="project-element"></a>Project 項目

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` 是根節點。 它會指定要使用的 MSBuild 版本，以及此檔案傳遞至 MSBuild.exe 時要執行的預設目標。

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations ItemGroup 項目

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` 包含專案組態描述。 例如，Debug|Win32、Release|Win32、Debug|ARM 等。 許多專案設定會專屬於某個組態。 例如，您可能會想要為發行組建設定優化屬性，而不是設定 debug build。

`ProjectConfigurations`專案群組不會在組建階段使用。 Visual Studio IDE 會要求它載入專案。 您可以將這個專案群組移至檔案 *`.props`* ，並匯入檔案中 *`.vcxproj`* 。 不過，在這種情況下，如果您需要新增或移除設定，則必須手動編輯檔案 *`.props`* ; 您無法使用 IDE。

### <a name="projectconfiguration-elements"></a>ProjectConfiguration 項目

下列程式碼片段顯示專案組態。 在此範例中，' Debug | x64 ' 是設定名稱。 專案設定名稱的格式必須是 `$(Configuration)|$(Platform)` 。 `ProjectConfiguration`節點可以有兩個屬性： `Configuration` 和 `Platform` 。 當設定為使用中時，會自動以此處指定的值來設定這些屬性。

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

IDE 預期會針對 `Configuration` `Platform` 所有專案中使用的任何組合和值尋找專案設定 `ProjectConfiguration` 。 通常，這表示專案可能有無意義的專案設定來滿足這項需求。 例如，如果專案具有下列組態：

- Debug|Win32

- Retail|Win32

- Special 32-bit Optimization|Win32

則必須同時具有下列組態，即使 "Special 32-bit Optimization" 對 x64 無意義也一樣：

- Debug|x64

- Retail|x64

- Special 32-bit Optimization|x64

您可以在 [方案組態管理員]**** 中，停用任何組態的建置和部署命令。

### <a name="globals-propertygroup-element"></a>Globals PropertyGroup 項目

```xml
<PropertyGroup Label="Globals" />
```

`Globals` 包含專案層級設定 `ProjectGuid` ，例如、 `RootNamespace` 和 `ApplicationType` `ApplicationTypeRevision` 。 最後兩項通常會定義目標 OS。 專案只能以單一 OS 為目標，因為參考和專案專案目前不能有條件。 這些屬性通常不會在專案檔中的其他位置覆寫。 此群組並非與設定相依，而且專案檔中通常只會 `Globals` 有一個群組。

### <a name="microsoftcppdefaultprops-import-element"></a>Microsoft.Cpp.default.props Import 項目

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**.Props**屬性工作表隨附 Visual Studio，且無法修改。 它包含專案的預設設定。 視 ApplicationType 而定，預設值可能會有所不同。

### <a name="configuration-propertygroup-elements"></a>Configuration PropertyGroup 項目

```xml
<PropertyGroup Label="Configuration" />
```

`Configuration` 屬性群組具有附加的組態條件 (例如 `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"`) 和多個複本，每個組態各一個。 此屬性群組會裝載專為特定組態設定的屬性。 組態屬性包含 PlatformToolset，同時也會控制 **Microsoft.Cpp.props** 中是否包含系統屬性工作表。 例如，如果您定義屬性 `<CharacterSet>Unicode</CharacterSet>`，則會包含系統屬性工作表 **microsoft.Cpp.unicodesupport.props**。 如果您檢查 **.props**，您會看到以下這 `<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />` 一行：

### <a name="microsoftcppprops-import-element"></a>Microsoft.Cpp.props Import 項目

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

**.Props**屬性工作表 (直接或透過匯入) 定義許多工具特定屬性的預設值。 範例包括編譯器的優化和警告層級屬性、MIDL 工具的 TypeLibraryName 屬性等等。 它也會根據在屬性群組中定義的設定屬性，匯入各種系統屬性表。

### <a name="extensionsettings-importgroup-element"></a>ExtensionSettings ImportGroup 項目

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings` 群組包含屬於組建自訂一部分之屬性工作表的匯入。 組建自訂最多可由三個檔案定義：檔案 *`.targets`* 、檔案 *`.props`* 和檔案 *`.xml`* 。 此匯入群組包含檔案的匯入 *`.props`* 。

### <a name="propertysheets-importgroup-elements"></a>PropertySheets ImportGroup 項目

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets` 群組包含使用者屬性工作表的匯入。 這些匯入是您透過 Visual Studio 的屬性管理員視圖新增的屬性工作表。 這些匯入的列出順序很重要，而且會反映在 [屬性管理員] 中。 專案檔通常會包含這種匯入群組的多個執行個體，每個專案組態各一個。

### <a name="usermacros-propertygroup-element"></a>UserMacros PropertyGroup 項目

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` 包含您建立為變數以用來自訂建置程序的屬性。 例如，您可以定義使用者巨集，將您的自訂輸出路徑定義為 $(CustomOutputPath) 並使用它來定義其他變數。 此屬性群組會裝載這類屬性。 在 Visual Studio 中，因為 Visual C++ 不支援設定的使用者宏，所以不會在專案檔中填入此群組。 屬性工作表支援使用者巨集。

### <a name="per-configuration-propertygroup-elements"></a>各個組態的 PropertyGroup 項目

```xml
<PropertyGroup />
```

此屬性群組有多個執行個體，所有專案組態的每個組態各有一個。 每個屬性群組都必須附加一個組態條件。 如有任何組態遺失，[專案屬性]**** 對話方塊將無法正常運作。 與之前列出的屬性群組不同的是，此屬性群組沒有標籤。 此群組包含專案組態層級設定。 這些設定會套用至屬於指定項目群組一部分的所有檔案。 組建自訂項目定義中繼資料會在此初始化。

此 PropertyGroup 必須在之後 `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` ，且沒有標籤的其他 PropertyGroup 必須在 (，否則專案屬性編輯將無法正確運作) 。

### <a name="per-configuration-itemdefinitiongroup-elements"></a>各個組態的 ItemDefinitionGroup 項目

```xml
<ItemDefinitionGroup />
```

包含項目定義。 這些定義必須遵循相同的條件規則，作為每個標籤的個別設定 `PropertyGroup` 元素。

### <a name="itemgroup-elements"></a>ItemGroup 項目

```xml
<ItemGroup />
```

`ItemGroup` 專案包含 (原始檔的專案，以及專案中) 的專案。 專案專案不支援條件 (也就是依規則定義視為專案專案的專案類型) 。

中繼資料應該要有每個設定的設定條件，即使它們都相同也一樣。 例如：

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Visual Studio c + + 專案系統目前不支援專案專案中有萬用字元。

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Visual Studio c + + 專案系統目前不支援專案專案中的宏。

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

直接定義 (或透過匯入) c + + 目標，例如組建、清除等等。

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets ImportGroup 項目

```xml
<ImportGroup Label="ExtensionTargets" />
```

此群組包含組建自訂目標檔案的匯入。

## <a name="impact-of-incorrect-ordering"></a>順序不正確的影響

Visual Studio IDE 相依于先前所述排序的專案檔。 例如，當您定義屬性頁中的屬性值時，IDE 通常會將屬性定義放在具有空白標籤的屬性群組中。 這種排序可確保系統屬性表中引入的預設值會由使用者定義值覆寫。 同樣地，目標檔案會在結束時匯入，因為它們會取用之前定義的屬性，而且通常不會自行定義屬性。 同樣地，使用者屬性工作表會在系統屬性表 (包含) 之後匯入 *`Microsoft.Cpp.props`* 。 此順序可確保使用者可以覆寫系統屬性表所導入的任何預設值。

如果檔案 *`.vcxproj`* 未遵循此配置，則組建結果可能不是您預期的結果。 例如，如果您在使用者定義的屬性工作表之後誤匯入系統屬性表，系統屬性表就會覆寫使用者設定。

即使是 IDE 設計階段的經驗，也取決於專案的正確排序範圍。 例如，如果您的檔案 *`.vcxproj`* 沒有匯 `PropertySheets` 入群組，IDE 可能無法判斷要在哪裡放置使用者在 **屬性管理員**中建立的新屬性工作表。 這可能會導致系統工作表覆寫使用者工作表。 雖然 IDE 所使用的啟發學習法可容忍檔案配置中的 *`.vcxproj`* 不一致，但強烈建議您不要偏離本文稍早所示的結構。

## <a name="how-the-ide-uses-element-labels"></a>IDE 如何使用項目標籤

在 IDE 中，當您在 [一般] 屬性頁中設定 **UseOfAtl** 屬性時，它會寫入至專案檔中的設定屬性群組。 相同屬性頁中的 [ **TargetName** ] 屬性會寫入 [每個標籤-less] 屬性群組。 Visual Studio 會查看屬性頁的 XML 檔案，以了解每個屬性寫入位置的相關資訊。 在 [ **一般** ] 屬性頁中，假設您有英文版的 Visual Studio 2019 Enterprise Edition，則該檔案為 `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml` 。 屬性頁 XML 規則檔會定義 Rule 及其所有屬性的靜態資訊。 這類資訊之一是目的檔案 (寫入其值的檔案) 中 Rule 屬性的慣用位置。 專案檔項目上的 Label 屬性會指定慣用位置。

## <a name="property-sheet-layout"></a>屬性工作表配置

下列 XML 程式碼片段是屬性工作表 (.props) 檔案的最小配置。 它類似于檔案 *`.vcxproj`* ，而且 *`.props`* 可以從先前的討論推斷專案的功能。

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

若要建立您自己的屬性工作表，請複製資料夾中的其中一個檔案， *`.props`* *`VCTargets`* 並針對您的目的進行修改。 針對 Visual Studio 2019 Enterprise edition，預設 *`VCTargets`* 路徑是 `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets` 。

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)\
[屬性頁面 XML 檔案](property-page-xml-files.md)\
[`.vcxproj` 檔案和萬用字元](vcxproj-files-and-wildcards.md)
