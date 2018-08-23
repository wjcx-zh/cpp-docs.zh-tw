---
title: 如何： 在 MSBuild 專案中使用建置事件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.usebuildevents
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59863911072b491eb19a1296f3cb40d4f4ab4dce
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613052"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>如何：在 MSBuild 專案中使用建置事件
建置事件是在建置流程中的特定階段中執行 MSBuild 的命令。 *建置前*在建置開始前，就會發生事件，而*連結前*連結步驟開始; 之前發生的事件和*建置後*建置之後所發生的事件已成功結束。 只有在相關聯的建置步驟發生時，才會發生建置事件。 例如，連結前事件不會發生連結步驟不會執行。  
  
 每三個建置事件命令項目所表示的項目定義群組中 (`<Command>`) 時要執行的和訊息項目 (`<Message>`) 也就是顯示何時**MSBuild**執行建置事件。 是選擇性的每個項目，如果您多次指定相同的項目，最後一個相符項目會優先使用。  
  
 選擇性*使用內建*項目 (`<`* 建置-事件 ***UseInBuild**`>`) 可以指定表示是否要執行建置事件屬性群組中。 內容的值*使用內建*項目是`true`或`false`。 根據預設，建置事件時執行，除非其相對應*使用內建*元素設定為`false`。  
  
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
 下列範例可以 myproject.vcxproj 檔案中建立的專案項目內新增[逐步解說： 使用 MSBuild 來建立 Visual c + + 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)。 A*建置前*事件會的 main.cpp;*連結前*main.obj; 的複本和 「 事件 」 可讓*建置後*事件會建立一份 myproject.exe。 如果使用發行組態來建置專案時，會執行建置事件。 如果使用的偵錯組態來建置專案時，不會執行建置事件。  
  
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
 [MSBuild （Visual c + +）](../build/msbuild-visual-cpp.md)   
 [逐步解說：使用 MSBuild 來建立 Visual C++ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)