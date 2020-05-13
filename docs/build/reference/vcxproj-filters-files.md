---
title: Vcxproj.過濾器檔案
ms.date: 09/25/2019
description: 使用 Visual Studio 的篩選器檔C++專案為解決方案資源管理員中的檔案定義自訂邏輯資料夾
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: 57735246b543680243994b99b8c05c9ad1211f38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335938"
---
# <a name="vcxprojfilters-files"></a>vcxproj.過濾器檔案

*篩選器*檔案 (.vcxproj.filters)\*是位於根項目資料夾中的 MSBuild 格式的 XML 檔。 它指定解決方案**資源管理員**中的邏輯資料夾中進入哪些檔案類型。 在下圖中 *,.cpp*檔案位於**源檔案**節點下。 *.h*檔案位於 **"標題檔案"** 節點下 *,.ico*和 *.rc*檔案位於**資源檔案**下。 此放置由篩選器檔控制。

![解決方案資源管理員中的邏輯資料夾](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>建立自訂篩選器檔案

可視化工作室會自動創建此檔。 此應用程式,預先定義的邏輯資料夾(篩選器)是:**源檔案**、**標題**檔案**與資源檔案**。 其他項目類型(如UWP)可能具有一組不同的預設資料夾。 Visual Studio 會自動為每個資料夾分配已知的文件類型。 如果要使用自定義名稱或包含自訂檔案類型的篩選器創建篩選器,則可以在專案的根資料夾中或現有篩選器下創建自己的篩選器檔。 (**引用**和**外部依賴項**是不參與篩選的特殊資料夾。

## <a name="example"></a>範例

下面的範例顯示範例之前顯示的篩選器檔。 它有一個平面層次結構;換句話說,沒有嵌套的邏輯資料夾。 `UniqueIdentifier` 為選擇性節點。 它使 Visual Studio 自動化介面能夠找到篩選器。 `Extensions`也是可選的。 將新檔添加到專案時,該檔將添加到具有匹配檔擴展名的最頂層篩選器中。 要將檔案添加到特定篩選器,請右鍵按一下篩選器並選擇「**新增新專案**」。

在`ItemGroup`啟動項目時`ClInclude`建立包含節點的 。 如果要生成自己的 vcxproj 檔,請確保所有專案項在篩選器檔中也有條目。 節點中`ClInclude`的值將覆蓋基於檔副檔名的默認篩選。 當您使用 Visual Studio 向專案添加新項時,IDE 將在篩選器檔中添加單個檔項目。 如果更改檔的副檔名,則不會自動重新分配篩選器。

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

要創建嵌套邏輯資料夾,請聲明篩選器中的所有節點`ItemGroup`,如下所示。 每個子節點必須將完整的邏輯路徑聲明為最上面的父節點。 在下面的示例中,必須聲明空`ParentFilter`,因為它在後面的節點中引用。

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
