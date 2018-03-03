---
title: "屬性頁 XML 規則檔 |Microsoft 文件"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b81e8965773c64144059fa433b54484c786159a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="property-page-xml-rule-files"></a>屬性頁 XML 規則檔
在 IDE 中的專案屬性頁會設定 VCTargets 資料夾中的 XML 檔案。 確切的路徑取決於 Visual Studio 的哪些 edition(s) 已安裝，並且產品語言。 適用於 Visual Studio 2017 Enterprise Edition，在英文中，路徑是`%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`。 XML 檔案會描述規則、 類別和個別的屬性、 其資料類型、 預設值的名稱以及其所要顯示的方式。 當您在 IDE 中設定屬性時，新的值會儲存在專案檔中。

唯一的情況下，需要了解這些檔案，並在 Visual Studio IDE 的內部工作 （a） 您想要建立自訂屬性頁，或者 （b） 您想要透過 Visual Studio IDE 以外方式來自訂您的專案屬性。 

首先，我們來開啟 [專案屬性頁 (中的專案節點上按一下滑鼠右鍵**方案總管] 中**，然後選擇屬性):
   
![Visual c + + 專案屬性](media/cpp-property-page-2017.png)

每個節點下的**組態屬性**稱為規則。 規則有時表示單一編譯器等工具，但一般而言一詞是指執行和，可能會產生一些輸出屬性的項目。 每個規則會填入 VCTargets 資料夾中的 xml 檔案。 例如，如上述的 C/c + + 規則會填入 'cl.xml'。

如上所示，每個規則有一組會組織成類別目錄的屬性。 每個規則底下的子節點代表目錄。 例如下的 最佳化節點 C/c + + 包含最佳化相關的所有屬性編譯器工具。 屬性和其本身的值會在右窗格的方格格式轉譯。

您可以開啟 cl.xml 在記事本或任何 XML 編輯器 （請參閱下方的快照集）。 您會看到根節點，稱為規則具有相同定義其下，顯示在 UI 中，以及其他中繼資料屬性的清單。

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

沒有對應至每個節點在 組態屬性的屬性頁 UI 中的一個 XML 檔案。 您可以新增或移除在 UI 中的規則，包括，或在專案中移除對應的 XML 檔案的位置。 比方說，這是如何 Microsoft.CppBuild.targets （向上一層從 1033年資料夾） 包括 cl.xml:

```xml  
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>

``` 
帶狀 cl.xml 的所有資料時，如果您將會得到下列基本架構：
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

下列章節說明每個主要元素以及某些可以附加至它們的中繼資料。

1. **規則：**規則通常是 xml 檔案中的根節點; 它可以有多個屬性：

```xml    
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```  

   a. **名稱：** Name 屬性是此規則的識別碼。 它需要所有的屬性頁面 xml 檔案的專案之間是唯一的。

   b. **PageTemplate:**這個屬性的值可由 UI 來選擇 UI 範本集合。 [工具] 範本會呈現標準的方格格式中的屬性。 其他內建的值，這個屬性為"偵錯工具 」 和 「 泛型 」。 請參閱的偵錯 節點和 一般 節點，分別指定這些值所產生的 UI 格式。 「 偵錯工具 」 頁範本的 UI 使用下拉式方塊切換不同的偵錯工具的內容，而 「 泛型 」 的範本在一頁，而不需要多個分類規則底下的子節點中顯示不同的屬性類別節點。 這個屬性是只對 UI; 建議xml 檔案被設計為獨立的 UI。 針對不同目的，不同的 UI 可能會使用這個屬性。

  c.  **SwitchPrefix:**這是參數的命令列中使用的前置詞。 值為"/"會產生看起來像 /ZI、 /nologo、 /W3 等等的參數。

  d. **順序：**這是建議的潛在的 UI 用戶端上的這項規則相較於所有其他規則，在系統中的相對位置。

  e. **xmlns:**這是標準的 XAML 項目。 您可以看到所列的三個命名空間。 這些會對應至 XAML 還原序列化的命名空間的類別，XAML 結構描述和系統命名空間，分別。

  f. **DisplayName:**這是規則節點的屬性頁 UI 上所顯示的名稱。 這個值會進行當地語系化。 我們建立 DisplayName 為規則的子元素，而不是屬性 （例如名稱或 SwitchPrefix） 因為內部當地語系化工具的需求。 從 XAML 的觀點來看，兩者都是相等的。 因此，您可以只會使其屬性，以減少雜亂，或讓它保持原狀。

  g. **資料來源：**這是非常重要的屬性，會告知專案系統的位置屬性值應該從中讀取和寫入，以及其分組 （如下所述）。 Cl.xml，這些值如下：

```xml  
       <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
```  
   - `Persistence="ProjectFile`告訴專案系統規則的所有內容應該寫入至專案檔或屬性工作表檔 （依據節點用於繁衍 （spawn） 的屬性頁）。 其他可能的值為"UserFile"，這會將值寫入.user 檔案。

   - `ItemType="ClCompile"`指出屬性，將儲存為 ItemDefinition 中繼資料或項目中繼資料 （後者屬性頁已繁衍從方案總管 中的檔案節點時，才） 的這個項目類型。 如果未設定此欄位，做為一般屬性 PropertyGroup 中寫入屬性。

   - `Label=""`指示當屬性都會寫入為`ItemDefinition`中繼資料的父 ItemDefinitionGroup 標籤將會是空白 （每個 MSBuild 項目可以有標籤）。 Visual Studio 2017 使用加上標籤的群組，以瀏覽.vcxproj 專案檔。 請注意，包含大部分的規則內容的群組是空字串做為標籤。

   - `HasConfigurationCondition="true"`告訴專案系統，使其接受目前的專案組態 （條件無法附加至父群組或值本身） 的效果附加設定條件和值。 例如，開啟關閉的專案節點的屬性頁，並設定屬性的值**警告與錯誤**下**組態屬性 > C/c + + 一般**為"Yes"。 下列的值會寫入至專案檔。 請注意，設定條件附加至父代 ItemDefinitionGroup。

```xml  
     <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
           <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
     </ItemDefinitionGroup>
 ```
   若此值已設為特定的檔案，例如 stdafx.cpp，屬性頁中的屬性值會被寫入專案檔，如下所示的 stdafx.cpp 項目底下。 請注意如何設定條件直接連接至本身的中繼資料。

 ```xml  
<ItemGroup>
   <ClCompile Include="stdafx.cpp">
      <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
   </ClCompile>
</ItemGroup>
 ```
   另一個屬性的**DataSource**以上未列出為**PersistedName**。 您可以使用這個屬性來表示使用不同名稱的專案檔中的屬性。 根據預設，此屬性設為屬性的**名稱**。 

   個別的屬性可以覆寫其父代規則的資料來源。 在此情況下，該屬性的值的位置會從規則中的其他屬性不同。

   h. 有其他屬性的規則，例如描述、 SupportsFileBatching 等等，這裡不顯示。 瀏覽這些類型的文件可以取得完整的規則或其他項目上適用於屬性集。 或者，您可以檢查中的型別上的公用屬性`Microsoft.Build.Framework.XamlTypes`命名空間中的`Microsoft.Build.Framework .dll`組件。

   i. **DisplayName**， **PageTemplate**，和**順序**會出現在此 UI 相關屬性否則 UI 無關資料模型。 這些屬性是幾乎一定可供任何用來顯示屬性頁的 UI。 **DisplayName**和**描述**xml 檔案中的幾乎所有項目上有兩個屬性。 這些是只有兩種當地語系化的屬性和 （當地語系化這些字串會說明在更新後）。

2.  **類別：**規則可以具有多個分類。 Xml 檔案中列出的分類的順序是以相同順序顯示類別目錄的 ui 建議。 例如，在 UI 中所見的 C/c + + 節點下類別的次序 – 一般、 最佳化、 前置處理器，...  – 與該在 cl.xml 相同。 範例類別看起來像這樣：

```xml  
 <Category Name="Optimization">
    <Category.DisplayName>
        <sys:String>Optimization</sys:String>
    </Category.DisplayName>
 </Category>
```
上述程式碼片段說明**名稱**和**DisplayName**前所說明的屬性。 同樣地，有其他屬性**類別**可以有不會使用上方。 您可以知道資訊，請閱讀的文件，或檢查使用 ildasm.exe 的組件。

3. **屬性：**這是中的 xml 檔案，包含這個規則中的所有屬性的清單。 每個屬性可以是其中一種 XAML 基本架構上面所示的五個可能類型。 當然，您可以在檔案中有只有少數這些型別。 屬性具有允許使用它來描述豐富的屬性數目。 將只說明**StringProperty**這裡。 其餘部分都很相似。

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
大部分的程式碼片段中的屬性之前介紹。 新的子類型、 分類和參數。

   a. **子型別**是屬性僅適用於**StringProperty**和**StringListProperty**; 它提供內容資訊。 例如，"file"的值表示此屬性代表檔案路徑。 這類內容資訊用來增強藉由提供做為屬性的編輯器，可讓使用者以視覺化方式選擇檔案的 Windows 檔案總管的編輯體驗。

   b. **類別：**這宣告這個屬性就會在其下的類別目錄。 嘗試尋找此內容**輸出檔**UI 中的類別。

   c.  **參數：**當規則表示工具 – 例如編譯器工具在此情況下 – 規則的大部分屬性期間不會傳遞為參數工具可執行檔建置時間。 這個屬性的值會指出要使用常值的參數。 上述的屬性會指定其參數應該是**Fo**。 結合**SwitchPrefix**父系規則，此屬性的屬性會被傳遞做為可執行檔**/Fo"偵錯\"** （會顯示在屬性頁 UI C/c + + 命令列中）。

   其他屬性的屬性包括：

   d. **Visible:**如果基於某些原因，您不希望屬性若要顯示在 屬性頁 （但可能仍可在建置階段期間），請將這個屬性設定為 false。

   e. **ReadOnly:**如果您想要提供的屬性頁中的這個屬性的值的唯讀檢視，此屬性設定為 true。

   f. **IncludeInCommandLine:**部分屬性可能不需要在建置階段期間傳遞至工具。 將此屬性設定為 false，會造成它無法傳遞。


