---
title: HOW TO：在 MSBuild 專案中使用建置事件
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.usebuildevents
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 7678b975558b245fb730bff35fb156bf21d7f895
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273478"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>HOW TO：在 MSBuild 專案中使用建置事件

建置事件是在建置流程中的特定階段中執行 MSBuild 的命令。 *建置前*在建置開始前，就會發生事件，而*連結前*連結步驟開始; 之前發生的事件和*建置後*建置之後所發生的事件已成功結束。 只有在相關聯的建置步驟發生時，才會發生建置事件。 例如，連結前事件不會發生連結步驟不會執行。

每三個建置事件命令項目所表示的項目定義群組中 (`<Command>`) 時要執行的和訊息項目 (`<Message>`) 也就是顯示何時**MSBuild**執行建置事件。 是選擇性的每個項目，如果您多次指定相同的項目，最後一個相符項目會優先使用。

選擇性*使用內建*項目 (`<`*建置事件*`UseInBuild>`) 可以指定表示是否要執行建置事件屬性群組中。 內容的值*使用內建*項目是 **，則為 true**或是**false**。 根據預設，建置事件時執行，除非其相對應*使用內建*元素設定為`false`。

下表列出每個組建事件 XML 項目：

|XML 項目|描述|
|-----------------|-----------------|
|`PreBuildEvent`|在建置開始之前，就會執行此事件。|
|`PreLinkEvent`|連結步驟開始之前，就會執行此事件。|
|`PostBuildEvent`|建置完成之後，就會執行此事件。|

下表列出每個*使用內建*項目：

|XML 項目|描述|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|指定是否要執行*建置前*事件。|
|`PreLinkEventUseInBuild`|指定是否要執行*連結前*事件。|
|`PostBuildEventUseInBuild`|指定是否要執行*post-build*事件。|

## <a name="example"></a>範例

下列範例可以 myproject.vcxproj 檔案中建立的專案項目內新增[逐步解說：使用 MSBuild 來建立視覺效果C++專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)。 A*建置前*事件會的 main.cpp;*連結前*main.obj; 的複本和 「 事件 」 可讓*建置後*事件會建立一份 myproject.exe。 如果使用發行組態來建置專案時，會執行建置事件。 如果使用的偵錯組態來建置專案時，不會執行建置事件。

```
<ItemDefinitionGroup>
  <PreBuildEvent>
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>
    <Message>Making a copy of main.cpp </Message>
  </PreBuildEvent>
  <PreLinkEvent>
<Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>
    <Message>Making a copy of main.obj</Message>
  </PreLinkEvent>
  <PostBuildEvent>
<Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>
    <Message>Making a copy of myproject.exe</Message>
  </PostBuildEvent>
</ItemDefinitionGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>
</PropertyGroup>
```

## <a name="see-also"></a>另請參閱

[MSBuild 命令列-C++](msbuild-visual-cpp.md)<br/>
[逐步解說：使用 MSBuild 建立 Visual C++ 專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
