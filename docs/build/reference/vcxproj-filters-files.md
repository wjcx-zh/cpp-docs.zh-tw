---
title: .Vcxproj 篩選檔案
ms.date: 09/25/2019
description: 使用 Visual Studio C++專案中的篩選檔案，為中的檔案定義自訂邏輯資料夾方案總管
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: ee44bf3d1cbe06d6c007ed8976ec384a456efca5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686856"
---
# <a name="vcxprojfilters-files"></a>.vcxproj 篩選檔案

*篩選器*檔案（\*. .vcxproj. filters）是 MSBuild 格式的 XML 檔案，位於根專案資料夾中。 它會指定哪些檔案類型會進入**方案總管**中的哪一個邏輯資料夾。 在下圖中， *.cpp*檔案位於 [**來源**檔案] 節點底下。 *.h*檔案位於 [**標頭檔**] 節點底下， *.ico*和 *.rc*檔案則位於 [**資源檔**] 底下。 這個位置是由篩選檔案所控制。

![方案總管中的邏輯資料夾](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>建立自訂篩選檔案

Visual Studio 會自動建立此檔案。 針對桌面應用程式，預先定義的邏輯資料夾（篩選器）為：**原始**檔、**標頭檔**和**資源檔**。 其他專案類型（例如 UWP）可能會有一組不同的預設資料夾。 Visual Studio 會自動將已知的檔案類型指派給每個資料夾。 如果您想要使用自訂名稱或包含自訂檔案類型的篩選來建立篩選器，您可以在專案的根資料夾中，或在現有的篩選準則下建立自己的篩選檔案。 （**參考**和**外部**相依性是不會參與篩選的特殊資料夾）。

## <a name="example"></a>範例

下列範例會顯示先前範例顯示的篩選檔案。 它有一個平面階層;換句話說，沒有任何嵌套的邏輯資料夾。 `UniqueIdentifier` 為選擇性節點。 它可讓 Visual Studio automation 介面尋找篩選準則。 `Extensions` 也是選擇性的。 將新檔案新增至專案時，會將它新增至具有相符副檔名的最上層篩選。 若要將檔案加入至特定篩選，請以滑鼠右鍵按一下篩選器，然後選擇 [**加入新專案**]。

第一次啟動專案時，會建立包含 @no__t 1 節點的 `ItemGroup`。 如果您要產生自己的 .vcxproj 檔案，請確定所有專案專案在篩選檔案中也有一個專案。 @No__t-0 節點中的值會覆寫根據副檔名的預設篩選。 當您使用 Visual Studio 將新專案加入至專案時，IDE 會在篩選檔案中加入個別的檔案專案。 如果您變更檔案的副檔名，則不會自動重新指派篩選。 

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Filter Include="Source Files">
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier>
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions>
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
    <Filter Include="Resource Files">
      <UniqueIdentifier>{67DA6AB6-F800-4c08-8B7A-83BB121AAD01}</UniqueIdentifier>
      <Extensions>rc;ico;cur;bmp;dlg;rc2;rct;bin;rgs;gif;jpg;jpeg;jpe;resx;tiff;tif;png;wav;mfcribbon-ms</Extensions>
    </Filter>
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="MFCApplication1.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="MFCApplication1Dlg.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="stdafx.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="targetver.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="Resource.h">
      <Filter>Header Files</Filter>
    </ClInclude>
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="MFCApplication1.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="MFCApplication1Dlg.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="stdafx.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
  </ItemGroup>
  <ItemGroup>
    <ResourceCompile Include="MFCApplication1.rc">
      <Filter>Resource Files</Filter>
    </ResourceCompile>
  </ItemGroup>
  <ItemGroup>
    <None Include="res\MFCApplication1.rc2">
      <Filter>Resource Files</Filter>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Image Include="res\MFCApplication1.ico">
      <Filter>Resource Files</Filter>
    </Image>
  </ItemGroup>
</Project>
```

若要建立嵌套邏輯資料夾，請在篩選準則中宣告所有節點 `ItemGroup`，如下所示。 每個子節點都必須宣告最上層父系的完整邏輯路徑。 在下列範例中，必須宣告空的 `ParentFilter`，因為在稍後的節點中會參考它。

```xml
  <ItemGroup>
    <Filter Include="ParentFilter">
    </Filter>
    <Filter Include="ParentFilter\Source Files"> <!-- Full path to topmost parent.-->  
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier> <!--  Optional-->
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions> <!-- Optional -->
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
  </ItemGroup>
```

