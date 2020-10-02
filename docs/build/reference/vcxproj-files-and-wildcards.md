---
title: .vcxproj 檔案和萬用字元
description: C + + 原生 MSBuild 專案系統 .vcxproj 檔如何處理萬用字元。
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 23d36a63f328e14cca59d1d57838173b4dcb0954
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662877"
---
# <a name="vcxproj-files-and-wildcards"></a>`.vcxproj` 檔案和萬用字元

Visual Studio IDE 不支援檔案中專案專案的特定結構 *`.vcxproj`* 。 這些不支援的結構包括以萬用字元、分號分隔的清單，或展開至多個檔案的 MSBuild 宏。 `.vcxproj`C + + 組建的專案系統比 MSBuild 更受限制。 每個專案專案都必須有自己的 MSBuild 專案。 如需有關檔案格式的詳細資訊 `.vcxproj` ，請參閱[ `.vcxproj` 和 `.props` 檔結構](vcxproj-file-structure.md)。

IDE 不支援這些結構範例：

```xml
<ItemGroup>
  <None Include="*.txt">
  <ClCompile Include="a.cpp;b.cpp"/>
  <ClCompile Include="@(SomeItems)" />
</ItemGroup>
```

如果 `.vcxproj` 包含這些結構的專案檔在 IDE 中載入，則專案可能會先運作。 不過，一旦 Visual Studio 修改專案，然後將其儲存在磁片上，就可能會發生問題。 您可能會遇到隨機損毀和未定義的行為。

在 Visual Studio 2019 16.7 版中，Visual Studio 載入專案檔時 `.vcxproj` ，它會自動偵測專案專案中不支援的專案。 您將會在解決方案載入期間于 [輸出] 視窗中看到警告。

Visual Studio 2019 16.7 版也會新增唯讀專案的支援。 唯讀支援可讓 IDE 使用手動撰寫的專案，而這些專案沒有 IDE 可編輯專案的其他限制。

如果您有 `.vcxproj` 使用一或多個不支援之結構的檔案，您可以使用下列其中一個選項讓它在 IDE 中載入而不發出警告：

- 明確列出所有專案
- 將您的專案標示為唯讀
- 將萬用字元專案移至目標主體

## <a name="list-all-items-explicitly"></a>明確列出所有專案

目前沒有任何方法可讓您在非唯讀專案的方案總管視窗中看到萬用字元展開專案。 方案總管預期專案必須明確列出所有專案。

若要讓 `.vcxproj` 專案自動展開 Visual Studio 2019 16.7 版或更新版本中的萬用字元，請將 `ReplaceWildcardsInProjectItems` 屬性設定為 `true` 。 建議您 *`Directory.Build.props`* 在根目錄中建立檔案，然後使用下列內容：

```xml
<Project>
  <PropertyGroup>
    <ReplaceWildcardsInProjectItems>true</ReplaceWildcardsInProjectItems>
  </PropertyGroup>
</Project>
```

## <a name="mark-your-project-as-read-only"></a>將您的專案標示為唯讀

在 Visual Studio 2019 16.7 版和更新版本中，您可以將專案標記為 *唯讀*。 若要將您的專案標記為唯讀，請將下列屬性新增至您的檔案 *`.vcxproj`* ，或新增至它所匯入的任何檔案：

```xml
<PropertyGroup>
    <ReadOnlyProject>true</ReadOnlyProject>
</PropertyGroup>
```

此 `<ReadOnlyProject>` 設定可防止 Visual Studio 編輯和儲存專案，因此您可以使用其中的任何 MSBuild 結構，包括萬用字元。

如果 Visual Studio 在檔案或其任何匯入的專案專案中偵測到萬用字元，就必須知道專案快取無法使用 *`.vcxproj`* 。 如果您有許多使用萬用字元的專案，IDE 中的方案載入時間會更長。

## <a name="move-wildcard-items-to-a-target-body"></a>將萬用字元專案移至目標主體

您可能會想要使用萬用字元來收集資源、新增產生的來源等等。 如果您不需要將它們列在 [方案總管] 視窗中，您可以改為使用這個程式：

1. 變更專案群組的名稱以加入萬用字元。 例如，而不是：

   ```xml
   <Image Include="*.bmp" />
   <ClCompile Include="*.cpp" />
   ```

   將它變更為：

   ```xml
   <_WildCardImage Include="*.bmp" />
   <_WildCardClCompile Include="*.cpp" />
   ```

1. 將此內容新增至您的檔案  *`.vcxproj`* 。或者，將它新增到 *`Directory.Build.targets`* 根目錄中的檔案，以影響該根目錄下的所有專案：

   ```xml
   <Target Name="AddWildCardItems"
       AfterTargets="BuildGenerateSources">
     <ItemGroup>
       <Image Include="@(_WildCardImage)" />
       <ClCompile Include="@(_WildCardClCompile)" />
     </ItemGroup>
   </Target>
   ```

   這項變更可讓組建在檔案中定義時看到專案  *`.vcxproj`* 。 不過，現在它們在方案總管視窗中看不到，而且不會在 IDE 中造成問題。

1.  `_WildCardClCompile`   當您在編輯器中開啟這些檔案時，若要顯示專案的正確 IntelliSense，請新增下列內容：

   ```xml
   <PropertyGroup>
     <ComputeCompileInputsTargets>
       AddWildCardItems
       $(ComputeCompileInputsTargets)
     </ComputeCompileInputsTargets>
   </PropertyGroup>
   ```

實際上，您可以將萬用字元用於目標主體內的任何專案。 您也可以在  `ItemGroup`   未定義為專案專案的中使用萬用字元 [`ProjectSchemaDefinition`](https://devblogs.microsoft.com/cppblog/vc-MSBuild-extensibility-example/) 。

> [!NOTE]
> 如果您將萬用字元包含從檔案移 *`.vcxproj`* 至匯入的檔案，則不會顯示在方案總管視窗中。 這項變更也可讓您的專案在 IDE 中載入，而不需要修改。 不過，我們不建議採用這種方法，因為它會停用專案快取。

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)<br/>
[屬性頁面 XML 檔案](property-page-xml-files.md)
