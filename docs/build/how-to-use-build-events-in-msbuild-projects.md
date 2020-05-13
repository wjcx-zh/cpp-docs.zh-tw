---
title: 如何：在 MSBuild 專案中使用建置事件
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060064"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>如何：在 MSBuild 專案中使用建置事件

組建事件是 MSBuild 在組建程式中的特定階段執行的命令。 *預先組建*事件會在組建開始之前發生;連結步驟開始之前，會先進行*連結前*事件;建立後*事件會在組建*成功結束之後發生。 只有在相關聯的建置步驟發生時，才會發生建置事件。 例如，如果連結步驟沒有執行，則不會發生連結前事件。

這三個組建事件中的每一個都是由執行的 command 元素（`<Command>`）以及**MSBuild**執行組建事件時所顯示的`<Message>`訊息元素（），在專案定義群組中表示。 每個專案都是選擇性的，如果您多次指定相同的專案，則會優先使用最後一次出現的專案。

您可以在屬性群組中指定選擇性的*使用內*建元素（`<`*組建-事件*`UseInBuild>`），以指出是否執行組建事件。 *使用中組建*元素的內容值為**true**或**false**。 根據預設，會執行組建事件，除非其對應的*使用中組建*元素設定為`false`。

下表列出每個 build event XML 元素：

|XML 元素|描述|
|-----------------|-----------------|
|`PreBuildEvent`|這個事件會在組建開始之前執行。|
|`PreLinkEvent`|這個事件會在連結步驟開始之前執行。|
|`PostBuildEvent`|這個事件會在組建完成之後執行。|

下表列出每個*使用中組建*元素：

|XML 元素|描述|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|指定是否要執行*預先建立*的事件。|
|`PreLinkEventUseInBuild`|指定是否執行*連結前*事件。|
|`PostBuildEventUseInBuild`|指定是否要執行*建立後*事件。|

## <a name="example"></a>範例

下列範例可以在[逐步解說：使用 MSBuild 建立 c + + 專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)中建立之 myproject 檔案的專案元素內加入。 *預先組建*事件會建立主要 .cpp 的複本;*連結前*事件會建立主要 .obj 的複本;和*後*置事件會建立 myproject 的複本。 如果專案是使用發行設定所建立，則會執行組建事件。 如果專案是使用 debug 設定建立的，則不會執行組建事件。

``` xml
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

## <a name="see-also"></a>請參閱

[命令列上的 MSBuild - C++](msbuild-visual-cpp.md)<br/>
[逐步解說：使用 MSBuild 建立 c + + 專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
