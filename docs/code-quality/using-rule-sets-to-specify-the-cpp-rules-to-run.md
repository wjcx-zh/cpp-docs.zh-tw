---
title: 使用規則集指定要執行的 C++ 規則
ms.date: 07/27/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
ms.openlocfilehash: f9876a2ce164d0a129ba21405ec61fdcbbd8de91
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507479"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>使用規則集來指定要執行的 C++ 規則

在 Visual Studio 中，您可以建立和修改自訂 *規則集* ，以符合與程式碼分析相關聯的特定專案需求。 預設規則集會儲存在中 *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* 。

**Visual Studio 2017 15.7 版和更新版本：** 您可以使用任何文字編輯器來建立自訂規則集，並在命令列組建中套用它們，無論您使用的是哪一個組建系統都一樣。 如需詳細資訊，請參閱 [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md)。

若要在 Visual Studio 中建立自訂 c + + 規則集，必須在 Visual Studio IDE 中開啟 C/c + + 專案。 然後，您可以在規則集編輯器中開啟標準規則集，然後新增或移除特定規則，並選擇性地變更程式碼分析判斷違反規則時所發生的動作。

若要建立新的自訂規則集，請使用新的檔案名進行儲存。 自訂規則集會自動指派給專案。

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>從單一現有的規則集建立自訂規則

::: moniker range="<=vs-2017"

1. 在方案總管中，開啟專案的快捷方式功能表，然後選擇 [ **屬性**]。

1. 在 [ **屬性頁** ] 對話方塊中，選取 [設定 **屬性**程式 > **代碼分析** > **一般** ] 屬性頁。

1. 在 [ **規則集** ] 下拉式清單中，執行下列其中一項：

   - 選擇您要自訂的規則集。

     \- 或 -

   - 選擇 **\<Browse...>** 指定不在清單中的現有規則集。

1. 選擇 [ **開啟** ]，在規則集編輯器中顯示規則。

::: moniker-end
::: moniker range=">=vs-2019"

1. 在方案總管中，開啟專案的快捷方式功能表，然後選擇 [ **屬性**]。

1. 在 [ **屬性頁** ] 對話方塊中，選取 [設定 **屬性**程式 > **代碼分析** > **Microsoft** ] 屬性頁。

1. 在 [作用中 **規則** ] 下拉式清單中，執行下列其中一項：

   - 選擇您要自訂的規則集。

     \- 或 -

   - 選擇 **\<Browse...>** 指定不在清單中的現有規則集。

1. 選擇 [ **開啟** ]，在規則集編輯器中顯示規則。

::: moniker-end

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>若要在規則集編輯器中修改規則集

- 若要變更規則集的顯示名稱，請在 [ **View** ] 功能表上選擇 [ **屬性視窗]**。 在 [ **名稱** ] 方塊中輸入顯示名稱。 請注意，顯示名稱可能與檔案名不同。

- 若要將群組的所有規則新增至自訂規則集，請選取群組的核取方塊。 若要移除群組的所有規則，請清除該核取方塊。

- 若要將特定規則新增至自訂規則集，請選取規則的核取方塊。 若要從規則集中移除規則，請清除該核取方塊。

- 若要變更程式碼分析違反規則時所採取的動作，請選擇規則的 [ **動作** ] 欄位，然後選擇下列其中一個值：

     **警告** -會產生警告。

     **錯誤** -產生錯誤。

     **Info** -產生訊息。

     **無** -停用規則。 此動作與從規則集移除規則相同。

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>使用規則集編輯器工具列來群組、篩選或變更規則集編輯器中的欄位

- 若要展開所有群組中的規則，請選擇 [ **全部展開**]。

- 若要折迭所有群組中的規則，請選擇 [ **全部**折迭]。

- 若要變更規則分組依據的欄位，請從 [ **群組依據** ] 清單中選擇欄位。 若要顯示已取消分組的規則，請選擇 **\<None>** 。

- 若要在規則資料行中新增或移除欄位，請選擇 [ **資料行選項**]。

- 若要隱藏未套用至目前方案的規則，請選擇 [ **隱藏未套用至目前解決方案的規則**]。

- 若要在顯示和隱藏指派錯誤動作的規則之間切換，請選擇 [ **顯示可產生程式碼分析錯誤的規則**]。

- 若要在顯示和隱藏指派警告動作的規則之間切換，請選擇 [ **顯示可產生程式碼分析警告的規則**]。

- 若要在顯示和隱藏指派 [ **無** ] 動作的規則之間切換，請選擇 [ **顯示未啟用的規則**]。

- 若要新增或移除目前規則集的 Microsoft 預設規則集，請選擇 [ **新增或移除子規則集**]。

## <a name="to-create-a-rule-set-in-a-text-editor"></a>在文字編輯器中建立規則集

您可以在文字編輯器中建立自訂規則集，並將它儲存在任何副檔名的位置， *`.ruleset`* 然後使用 [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md) 編譯器選項來套用。

下列範例顯示一個基本規則集檔案，您可以將其作為起點：

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="10.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

## <a name="ruleset-schema"></a>規則集架構

下列規則集架構描述規則集檔案的 XML 架構。 規則集架構會儲存在中 *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Schemas\RuleSet.xsd`* 。 您可以使用它，以程式設計方式撰寫您自己的規則集，或驗證您的自訂規則集是否遵守正確的格式。 如需詳細資訊，請參閱 how [to：根據 XSD 架構建立 XML 檔](/visualstudio/xml-tools/how-to-create-an-xml-document-based-on-an-xsd-schema)。

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:annotation>
    <xs:documentation xml:lang="en">
            Visual Studio Code Analysis Rule Set Schema Definition Language.
            Copyright (c) Microsoft Corporation. All rights reserved.
        </xs:documentation>
  </xs:annotation>

  <!-- Every time this file changes, be sure to change the Validate method for the corresponding object in the code -->

  <xs:element name="RuleSet" type="TRuleSet">
  </xs:element>

  <xs:complexType name="TLocalization">
    <xs:all>
      <xs:element name="Name" type="TName" minOccurs="0" maxOccurs="1" />
      <xs:element name="Description" type="TDescription" minOccurs="0" maxOccurs="1" />
    </xs:all>
    <xs:attribute name="ResourceAssembly" type="TNonEmptyString" use="required" />
    <xs:attribute name="ResourceBaseName" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleHintPaths">
    <xs:sequence>
      <xs:element name="Path" type="TNonEmptyString" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="TName">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TDescription">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TInclude">
    <xs:attribute name="Path" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TIncludeAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TIncludeAll">
    <xs:attribute name="Action" type="TIncludeAllAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRule">
    <xs:attribute name="Id" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TRuleAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRules">
    <xs:sequence>
      <xs:element name="Rule" type="TRule" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="AnalyzerId" type="TNonEmptyString" use="required" />
    <xs:attribute name="RuleNamespace" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleSet">
    <xs:sequence minOccurs="0" maxOccurs="1">
      <xs:element name="Localization" type="TLocalization" minOccurs="0" maxOccurs="1" />
      <xs:element name="RuleHintPaths" type="TRuleHintPaths" minOccurs="0" maxOccurs="1" />
      <xs:element name="IncludeAll" type="TIncludeAll" minOccurs="0" maxOccurs="1" />
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Include" type="TInclude" minOccurs="0" maxOccurs="unbounded" />
        <xs:element name="Rules" type="TRules" minOccurs="0" maxOccurs="unbounded">
          <xs:unique name="UniqueRuleName">
            <xs:selector xpath="Rule" />
            <xs:field xpath="@Id" />
          </xs:unique>
        </xs:element>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="Name" type="TNonEmptyString" use="required" />
    <xs:attribute name="Description" type="xs:string" use="optional" />
    <xs:attribute name="ToolsVersion" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:simpleType name="TRuleAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
      <xs:enumeration value="Default"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAllAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TNonEmptyString">
    <xs:restriction base="xs:string">
      <xs:minLength value="1" />
    </xs:restriction>
  </xs:simpleType>
  
</xs:schema>

```

架構元素詳細資料：

| Schema 元素 | 描述 |
|--------------------|--------------|
| `TLocalization` | 當地語系化資訊，包括規則集檔案的名稱、規則集檔案的描述、包含當地語系化資源的資源元件名稱，以及當地語系化資源的基底名稱 |
| `TRuleHintPaths` | 用來當做提示以搜尋規則集檔案的檔案路徑 |
| `TName` | 目前規則集檔案的名稱 |
| `TDescription` | 目前規則集檔案的描述 |
| `TInclude` | 包含規則動作之內含規則集的路徑 |
| `TIncludeAll` | 所有規則的規則動作 |
| `TRule` | 具有規則動作的規則識別碼 |
| `TRules` | 一或多個規則的集合 |
| `TRuleSet` | 包含當地語系化資訊的規則集檔案格式、規則提示路徑、包含所有資訊、包含資訊、規則資訊、名稱、描述和工具版本資訊 |
| `TRuleAction` | 描述規則動作的列舉，例如錯誤、警告、資訊、隱藏或無 |
| `TIncludeAction` | 描述規則動作的列舉，例如錯誤、警告、資訊、隱藏、無或預設值 |
| `TIncludeAllAction` | 描述規則動作（例如錯誤、警告、資訊或隱藏）的列舉 |

若要查看規則集的範例，請參閱， [在文字編輯器中建立規則集](#to-create-a-rule-set-in-a-text-editor)，或儲存在中的任何預設規則集 `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets` 。
