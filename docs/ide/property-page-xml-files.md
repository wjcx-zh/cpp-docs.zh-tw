---
title: 屬性頁 XML 規則檔 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcee2c416fba6a959785826781aefd96b0d06d75
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339640"
---
# <a name="property-page-xml-rule-files"></a>屬性頁 XML 規則檔
IDE 中的專案屬性頁是由 VCTargets 資料夾中的 XML 檔案設定。 實際路徑取決於所安裝的 Visual Studio 版本，以及產品語言。 若是英文版的 Visual Studio 2017 Enterprise Edition，其路徑會是 `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`。 XML 檔案描述規則、分類和個別屬性的名稱，以及其資料類型、預設值與要顯示的方式。 當您在 IDE 中設定屬性時，新的值會儲存在專案檔中。

只有在下列情況下，您才需要了解這些檔案和 Visual Studio IDE 的內部運作：(a) 您想要建立自訂屬性頁，或 (b) 您想要透過 Visual Studio IDE 以外方式來自訂您的專案屬性。 

首先，讓我們開啟專案的屬性頁 (以滑鼠右鍵按一下 [方案總管] 中的專案節點，然後選擇 [屬性])：
   
![Visual C++ 專案屬性](media/cpp-property-page-2017.png)

[組態屬性] 下的每個節點稱為「規則」。 規則有時代表單一工具 (例如編譯器)，但一般而言，該字詞是指具有屬性、會執行且可能產生一些輸出的某種項目。 每項規則都是從 VCTargets 資料夾中的 XML 檔案填入。 例如，上述 C/C++ 規則是由 `cl.xml' 填入。

如上所示，每項規則會有組織成分類的一組屬性。 規則下的每個子節點各代表一個分類。 例如，C/C++ 下的 [最佳化] 節點包含編譯器工具的所有最佳化相關屬性。 屬性及其值本身是以右窗格的方格格式呈現。

您可以在 [記事本] 或任何 XML 編輯器中開啟 cl.xml (請參閱下面的快照集)。 您會看到一個稱為 Rule 的根節點，其下方定義了與 UI 中所顯示相同的屬性清單，以及其他中繼資料。

```xml  
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
...
``` 

屬性頁 UI 中 [組態屬性] 下的每個節點各有一個對應的 XML 檔案。 您可以透過包含或移除專案中對應 XML 檔案的位置，來新增或移除 UI 中的規則。 例如，以下示範 Microsoft.CppBuild.targets (從 1033 資料夾往上一個層級) 如何包含 cl.xml：

```xml  
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>

``` 
如果您移除 cl.xml 中的所有資料，您會得到下列基本架構：
```xml  
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
        ...
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
``` 

下一節描述每個主要項目，以及可對其附加的一些中繼資料。

1. **Rule：** Rule 通常是 XML 檔案中的根節點，可以有多個屬性：

```xml    
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```  

   a. **Name：** Name 屬性是 Rule 的識別碼。 它必須在專案的所有屬性頁 XML 檔案之間是唯一的。

   b. **PageTemplate：** UI 使用此屬性值從 UI 範本集合進行選擇。 "tool" 範本會以標準方格格式呈現屬性。 此屬性的其他內建值還包括 "debugger" 和 "generic"。 請分別參閱 [偵錯] 節點和 [一般] 節點，以了解透過指定這些值所產生的 UI 格式。 "debugger" 頁面範本的 UI 使用下拉式方塊在不同偵錯工具的屬性之間進行切換，而 "generic" 範本將不同的屬性分類全部顯示在一個頁面上，有別於在規則節點下有多個分類子節點。 此屬性只是對 UI 的建議，XML 檔案設計成獨立於 UI。 不同 UI 可能會基於不同目的使用此屬性。

  c.  **SwitchPrefix：** 這是參數的命令列中所使用的前置詞。 值 "/" 會產生看起來像 /ZI、/nologo、/W3 等的參數。

  d. **Order：** 這是對潛在 UI 用戶端提出之有關此 Rule 相較於系統中所有其他 Rule 之相對位置的建議。

  e. **xmlns：** 這是標準 XAML 項目。 您可以看到列出三個命名空間。 這些會分別對應至 XAML 還原序列化類別、XAML 結構描述和系統命名空間的命名空間。

  f. **DisplayName：** 這是屬性頁 UI 上針對 Rule 節點所顯示的名稱。 此值會當地語系化。 由於內部當地語系化工具需求，我們將 DisplayName 建立為 Rule 的子項目，而不是屬性 (例如 Name 或 SwitchPrefix)。 從 XAML 的觀點來看，兩者是相等的。 因此，您可以直接將它設為屬性來減少雜亂，或讓它保持原狀。

  g. **DataSource：** 這是非常重要的屬性，它會告知專案系統屬性值應該從中讀取及寫入的位置，以及其群組方式 (以下將進行說明)。 針對 cl.xml，這些值包括：

```xml  
       <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
```  
   - `Persistence="ProjectFile`，告知專案系統 Rule 的所有屬性都應該寫入專案檔或屬性工作表檔 (視用來繁衍屬性頁的節點而定)。 其他可能的值為 "UserFile"，這會將值寫入 .user 檔案。

   - `ItemType="ClCompile"`，指出屬性將儲存為此項目類型的 ItemDefinition 中繼資料或項目中繼資料 (後者僅限於從 [方案總管] 中的檔案節點繁衍屬性頁時)。 若未設定此欄位，屬性會寫入作為 PropertyGroup 中的通用屬性。

   - `Label=""`，表示當屬性會寫入作為 `ItemDefinition` 中繼資料時，父 ItemDefinitionGroup 的標籤會是空白 (每個 MSBuild 項目可以有一個 Label)。 Visual Studio 2017 使用已標記的群組來巡覽 .vcxproj 專案檔。 請注意，包含大部分 Rule 屬性的群組是以空字串為標籤。

   - `HasConfigurationCondition="true"`，告知專案系統將組態條件附加至值，只有目前的專案組態才會生效 (條件可附加至父群組或值本身)。 例如，開啟專案節點的屬性頁，然後將 [組態屬性] > [C/C++] > [一般] 下的 [將警告視為錯誤] 屬性值設定為 [是]。 下列值會寫入專案檔。 注意附加至父 ItemDefinitionGroup 的組態條件。

```xml  
     <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
           <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
     </ItemDefinitionGroup>
 ```
   如果已在屬性頁中針對特定檔案 (例如 stdafx.cpp) 設定此值，則屬性值會寫入專案檔中的 stdafx.cpp 項目下，如下所示。 注意如何將組態條件直接附加至中繼資料本身。

 ```xml  
<ItemGroup>
   <ClCompile Include="stdafx.cpp">
      <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
   </ClCompile>
</ItemGroup>
 ```
   **DataSource** 還有以上未列出的另一個屬性，那就是 **PersistedName**。 您可以使用此屬性 (Attribute) 代表專案檔中使用不同名稱的屬性 (Property)。 根據預設，此屬性 (Attribute) 會設定為屬性 (Property) 的 **Name**。 

   個別屬性可以覆寫其父 Rule 的 DataSource。 在此情況下，該屬性值的位置會與 Rule 中的其他屬性不同。

   h. Rule 還有此處未顯示的其他屬性，例如 Description、SupportsFileBatching 等。 藉由瀏覽這些類型的文件，即可取得適用於 Rule 或任何其他項目的完整屬性集。 或者，您可以在 `Microsoft.Build.Framework .dll` 組件的 `Microsoft.Build.Framework.XamlTypes` 命名空間中，查看這些類型的公用屬性。

   i. **DisplayName**、**PageTemplate** 和 **Order** 是位於此 UI 獨立資料模型中的 UI 相關屬性。 這些屬性幾乎一定可供用來顯示屬性頁的 UI 使用。 **DisplayName** 和 **Description** 是 XML 檔案中幾乎所有項目上都有的兩個屬性。 而且只有這兩個屬性會當地語系化 (本文稍後將說明這些字串的當地語系化)。

2.  **Category：** 一個 Rule 可以有多個 Category。 XML 檔案中列出的分類順序是對 UI 的建議，以依照相同順序顯示分類。 例如，[C/C++] 節點下的分類順序在 UI 中顯示為：[一般]、[最佳化]、[前置處理器]...  – 與 cl.xml 中相同。 範例分類看起來如下：

```xml  
 <Category Name="Optimization">
    <Category.DisplayName>
        <sys:String>Optimization</sys:String>
    </Category.DisplayName>
 </Category>
```
上述程式碼片段顯示先前描述的 **Name** 和 **DisplayName** 屬性。 同樣地，**Category** 可能會有以上未使用的其他屬性。 您可以藉由閱讀文件或使用 ildasm.exe 查看組件，來了解這些屬性。

3. **Property：** 這是 XML 檔案的主要部分，包含此 Rule 中的所有屬性清單。 每個屬性可以是上面 XAML 基本架構中所示的五種可能類型之一。 當然，您的檔案中可以只有其中一些類型。 一個屬性 (Property) 包含可讓其描述更豐富的數個屬性 (Attribute)。 此處只會說明 **StringProperty**。 其餘屬性則大同小異。

```xml  
<StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
  <StringProperty.DisplayName>
    <sys:String>Object File Name</sys:String>
  </StringProperty.DisplayName>
  <StringProperty.Description>
    <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
  </StringProperty.Description>
</StringProperty>
```
程式碼片段中的大部分屬性先前都已描述。 Subtype、Category 和 Switch 是新的屬性。

   a. **Subtype** 是僅適用於 **StringProperty** 和 **StringListProperty** 的屬性，其提供內容資訊。 例如，值 "file" 指出屬性代表檔案路徑。 這類內容資訊藉由提供 Windows 檔案總管作為屬性的編輯器，讓使用者以視覺化方式選擇檔案，因此可增強編輯體驗。

   b. **Category：** 這會宣告此屬性所屬分類。 請嘗試在 UI 中的 [輸出檔案] 分類下找到此屬性。

   c.  **Switch：** 當 Rule 代表一項工具時 (例如本例中的編譯器工具)，Rule 的大部分屬性會在建置時作為參數傳遞至工具可執行檔。 此屬性的值會指出要使用的參數常值。 上述屬性指定其參數應該是 **Fo**。 此屬性 (Property) 會與父 Rule 的 **SwitchPrefix** 屬性 (Attribute) 結合，然後傳遞至可執行檔作為 **/Fo"Debug\"** (顯示在屬性頁 UI 的 C/C++ 命令列中)。

   其他屬性 (Property) 的屬性 (Attribute) 包括：

   d. **Visible：** 如果基於某些原因，您不想要在屬性 (Property) 頁中顯示您的屬性 (Property) (但仍可能在建置期間提供)，請將此屬性 (Attribute) 設定為 false。

   e. **ReadOnly：** 如果您想要在屬性 (Property) 頁中提供此屬性 (Property) 值的唯讀檢視，請將此屬性 (Attribute) 設定為 true。

   f. **IncludeInCommandLine：** 某些屬性可能不需要在建置期間傳遞至工具。 將此屬性設定為 false 可防止傳遞它。


