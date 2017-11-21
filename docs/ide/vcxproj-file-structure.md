---
title: ".vcxproj 和.props 檔案結構 |Microsoft 文件"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
caps.latest.revision: "1"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bc57a69b71bd7fbdbf97d5c34e7e6ec0694bb5df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="vcxproj-and-props-file-structure"></a>.vcxproj 和.props 檔案結構
MSBuild 是預設的專案系統，在 Visual Studio;當您選擇**檔案 |新的專案**Visual c + + 中，您要建立其設定會儲存在副檔名的 XML 專案檔案的 MSBuild 專案`.vcxproj`。 .Props 檔案和設定儲存位置的.targets 檔案，也可以匯入專案檔。 在大部分情況下，您永遠不需要手動編輯專案檔，並事實上您不應該編輯它以手動方式除非您深入了解的 MSBuild。 可能的話您應該使用 Visual Studio 屬性頁來修改專案設定 (請參閱[使用專案屬性](working-with-project-properties.md)。 不過，在某些情況下，您可能需要手動修改專案檔或屬性工作表。 這些情況下，本文會包含檔案的結構的基本資訊。 

**重要事項：**如果您選擇手動編輯.vcxproj 檔案，請留意下列重點：
1. 將檔案的結構必須遵循規定的表單，這篇文章中所述。
2. Visual c + + 專案系統目前不支援萬用字元專案項目中。 例如，不支援這種：
```xml
<ClCompile Include="*.cpp"/>
```
3. Visual c + + 專案系統目前不支援的巨集的專案項目路徑中。 例如，不支援這種：
```xml
<ClCompile Include="$(IntDir)\generated.cpp"/>
```
4. 才能正確地新增、 移除或修改中編輯時，專案屬性**專案屬性** 對話方塊中，這個檔案必須包含不同的群組，每個專案組態，且條件必須在這種形式：

```xml
Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”
```
 
5. 每一個屬性必須指定正確的標籤，為指定的屬性規則檔中的群組中。 如需詳細資訊，請參閱 [屬性頁 xml 規則檔案] (https://review.docs.microsoft.com/en-us/cpp/ide/property-page-xml-files)。 


## <a name="vcxproj-file-elements"></a>.vcxproj 檔項目
您可以使用任何文字編輯器或 XML 編輯器來檢查.vcxproj 檔案的內容。 檢視 Visual Studio 中以滑鼠右鍵按一下方案總管 中的專案選擇**卸載專案**，然後選擇**編輯 Foo.vcxproj**。 

要注意的第一點是，最上層項目會出現在特定的順序。 例如: 
-  之後的匯入 Microsoft.Cpp.Default.props 發生的大部分屬性群組和項目定義群組。
-  所有目標都會匯都入的檔案結尾。
-  有多個屬性群組，每個都有唯一的標籤，並在發生特定的順序。

專案檔中項目的順序是很重要，，因為 MSBuild 會以循序求值模型為基礎。  如果您的專案檔案，包括所有匯入的.props 和.targets 檔案包含多個屬性定義，最後的定義會覆寫上述項目。 在下列範例中，值"xyz"將設定編譯期間因為 MSBUild 引擎它上次其評估期間發現。 

```xml 
 <MyProperty>abc</MyProperty>
 <MyProperty>xyz</MyProperty>
``` 
 
下列程式碼片段會顯示最少.vcxproj 檔案。 Visual Studio 所產生的任何.vcxproj 檔案會包含下列最上層的 MSBuild 項目，而且會依此順序中出現，（雖然它們可能包含多個複本的每個這類最上層項目）。 請注意，`Label`屬性僅適用於 Visual studio 突顯為編輯的任意標記; 他們沒有任何其他功能。

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
 
 下節說明每個這些元素的目的和原因，它們的順序這種方式：
  
```xml  
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```
`Project`是根節點。 它會指定要使用的 MSBuild 版本以及要執行此檔案傳遞至 MSBuild.exe 時的預設目標。

```xml  
<ItemGroup Label="ProjectConfigurations" />
```
`ProjectConfigurations`包含專案組態描述。 範例包括偵錯 |Win32，版本 |Win32，偵錯 |ARM 和等等。 許多專案設定專屬於指定的設定。 例如，您可能想設定最佳化的發行組建，但不是偵錯組建的屬性。  

下列程式碼片段顯示的專案組態。 在此範例中 ' 偵錯 | x 64' 是組態名稱。 專案組態名稱必須是格式 $(Configuration)|$(Platform). 專案組態節點可以有兩個屬性： 組態與平台。 設定作用中時此處指定的值將會自動設定這些屬性。

```xml
<ProjectConfiguration Include="Debug|x64">
    <Configuration>Debug</Configuration> 
    <Platform>x64</Platform>
</ProjectConfiguration>
```
`ProjectConfigurations`項目群組不是在建置階段。 Visual Studio IDE 會需要它才能載入專案。 此項目群組可以移至.props 檔案，並匯入.vcxproj 檔案。 不過，在此情況下，如果您需要加入或移除設定，您必須手動編輯.props 檔案中。您無法使用 IDE。

IDE，預期應找到專案組態的專案組態的所有項目中使用的組態與平台任何的值組合。 這通常表示專案可能會有意義的專案組態以滿足此需求。 比方說，如果專案具有這些設定：

- 偵錯 |Win32
- 零售 |Win32
- 特別的 32 位元最佳化 |Win32

然後它也必須擁有這些設定中，即使 「 特殊 32 位元最佳化 」 是無意義的 x64: 

- Debug|x64
- 零售 | x64
- 特別的 32 位元最佳化 | x64

您可以停用組建和部署任何設定在 方案組態管理員 」 中的命令。

```xml  
 <PropertyGroup Label="Globals" />
```
 `Globals`包含專案層級設定，例如 ProjectGuid、 RootNamespace 和 ApplicationType / a。 最後兩個通常會定義目標作業系統。 因為的參考和專案項目不能有條件目前專案可以只為目標是單一的作業系統。 這些屬性通常不覆寫其他位置之專案檔中。 這個群組不是組態相關，因此通常只有一個全域群組存在於專案檔中。

```xml
 <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Microsoft.Cpp.default.props**屬性工作表隨附於 Visual Studio，而且無法修改。 它包含專案的預設設定。 預設值是以 ApplicationType 可能有所不同。

```xml
<PropertyGroup Label="Configuration" />
```
 `Configuration`屬性群組都具有附加的設定條件 (例如`Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`) 和多個複本，其中每個組態中出現。 此屬性群組主控的特定組態設定的屬性。 組態屬性包含 PlatformToolset 和控制的系統屬性工作表中包含**Microsoft.Cpp.props**。 例如，如果您定義屬性`<CharacterSet>Unicode</CharacterSet>`，然後系統屬性工作表**microsoft。Cpp.unicodesupport.props**將會包含。 如果您檢查**Microsoft.Cpp.props**，您會看到行： `<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`。 

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```
**Microsoft.Cpp.props**屬性工作表 （直接或透過匯入） 會定義許多工具特有的屬性，例如編譯器的最佳化和警告層級屬性，MIDL 工具 TypeLibraryName 的預設值屬性，並且等等。 它也會根據哪一個組態屬性定義正上方的屬性群組中的各種系統屬性工作表匯入。 

```xml
<ImportGroup Label="ExtensionSettings" />
```
`ExtensionSettings`群組包含屬於建置自訂的屬性工作表匯入。 建置自訂由多達三個檔案所定義：.targets 檔案中，由於.props 檔案和.xml 檔案。 此匯入群組中包含.props 檔案匯的入。

```xml
<ImportGroup Label="PropertySheets" />
```
 `PropertySheets`群組包含匯入的使用者屬性工作表。 這些是您透過 Visual Studio 中的 [屬性管理員] 檢視加入屬性工作表。 這些匯入列中的順序很重要，而且會反映在 屬性管理員。 專案檔通常會包含這種匯入群組，一個用於每個專案組態的多個執行個體。  
   
```xml   
<PropertyGroup Label="UserMacros" />
```
`UserMacros`是用於自訂建置流程的變數。 例如，您可以定義使用者巨集將自訂輸出路徑定義為 $(CustomOutputPath) 並用它來定義其他變數。 此屬性群組裝載這類屬性。 請注意，在 Visual Studio 中，填入此群組是不在專案檔因為 Visual c + + 不支援設定的使用者巨集。 屬性工作表中支援使用者巨集。 

```xml
<PropertyGroup />
``` 
 此屬性群組必須有連接的所有專案組態進行設定條件。 如果遺漏任何，專案屬性 對話方塊將無法正確運作。 有多個執行個體的屬性群組，其中每個組態。 不同於上述的屬性群組，在這個沒有標籤。 此群組包含專案組態層級設定。 這些設定套用至指定的項目群組一部分的所有檔案。 建置自訂項目定義的中繼資料會初始化這裡。 之後必須放在此 PropertyGroup`<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />`必須沒有標籤之前的任何其他 PropertyGroup 和 （否則編輯專案屬性將不會正確運作）。  

```xml
 <ItemDefinitionGroup />
```
包含項目定義。 這些必須遵循標籤小於 PropertyGroup 相同條件的規則。

```xml
<ItemGroup />
```  
包含專案中的項目 （原始程式檔等）。 不支援專案項目 （也就是項目類型會被視為由規則定義的專案項目） 的條件。

中繼資料不應該有設定條件，每個組態，即使 theyare 完全相同。 例如: 

  ```xml
  <ItemGroup>
     <ClCompile Include="stdafx.cpp">
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|x64’">true</TreatWarningAsError>
     </ClCompile>
  </ItemGroup>
  ```
Visual c + + 專案系統目前不支援萬用字元專案項目中。 
```xml  
  <ItemGroup>
     <ClCompile Include="*.cpp"> <!--Error-->
  </ItemGroup>
```
Visual c + + 專案系統目前不支援的巨集專案項目中。 
```xml  
  <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
  </ItemGroup>
```
ItemGroup 中, 指定的參考，並有這些限制：
- 參考不支援條件。 
- 參考中繼資料不支援條件。

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```
定義 （直接或透過匯入） Visual c + + 為目標，例如建置、 清除等。

```xml
<ImportGroup Label="ExtensionTargets" />
```
此群組包含建置自訂的目標檔案匯入。
 
 ## <a name="impact-of-incorrect-ordering"></a>順序不正確的影響
 Visual Studio IDE，取決於專案檔，具有排序上面所述。 例如，當您定義的屬性值的屬性頁中，IDE 會通常將屬性定義空白標籤的屬性群組中。 這可確保系統屬性工作表中的預設值會覆寫由使用者定義值。 同樣地，目標檔案匯入結尾因為它們會消耗上述定義的屬性，因為它們通常不會定義屬性本身。 同樣地，使用者屬性工作表會匯入系統屬性工作表之後 (包括透過**Microsoft.Cpp.props**)。 這可確保使用者可以覆寫由系統屬性工作表的任何預設值。
  
 .Vcxproj 檔案未遵循此配置命名為，如果組建結果可能無法預期。 例如，如果您不小心之後匯入系統屬性工作表使用者所定義的屬性工作表，使用者設定將會覆寫系統屬性工作表。
  
 即使 IDE 設計階段經驗取決於在某個程度的項目正確順序。 例如，如果您.vcxproj 檔案並沒有`PropertySheets`匯入群組，IDE 可能無法判斷要在何處放置新的屬性工作表中建立使用者**屬性管理員**。 這可能導致正在覆寫由系統工作表的使用者工作表。 雖然 IDE 使用啟發學習法可以容忍.vcxproj 檔案版面配置中的不一致性，強烈建議不偏離稍早在本文中所顯示的結構。

## <a name="how-the-ide-uses-element-labels"></a>如何在 IDE 使用項目標籤
  
在 IDE 中，當您設定 UseOfAtl 屬性於一般 屬性頁面上，它會寫入專案檔案中的組態屬性群組時相同的屬性頁中的 TargetName 屬性寫入至無標籤的屬性群組。 Visual Studio 會查看屬性頁的 xml 檔案，如需有關何處寫入每一個屬性。 一般屬性頁面 （假設您有 Visual Studio Enterprise Edition 的英文版），該檔案是`%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`。 屬性頁 XML 規則檔會定義規則和其所有屬性的靜態資訊。 這類的某項資訊是規則屬性的目的地檔案 （其值將寫入其中的檔案） 中的慣用的位置。 在專案檔項目 Label 屬性指定慣用的位置。 


 ## <a name="property-sheet-layout"></a>屬性工作表版面配置
  
 下列 XML 程式碼片段為屬性工作表 (.props) 檔案的最小版面配置。 類似於.vcxproj 檔案，而且也可以推斷.props 項目的功能，從先前的討論。 

```xml
 <Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <ImportGroup Label="PropertySheets" />
   <PropertyGroup Label="UserMacros" />
   <PropertyGroup />
   <ItemDefinitionGroup />
   <ItemGroup />
 </Project>
```
若要讓屬性工作表，VCTargets 資料夾中複製其中的.props 檔案並修改您的目的。 適用於 Visual Studio 2017 Enterprise edition，預設 VCTargets 路徑是`%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets`。 

## <a name="see-also"></a>另請參閱
[使用專案屬性](working-with-project-properties.md)
[屬性頁面 XML 檔案](property-page-xml-files.md)