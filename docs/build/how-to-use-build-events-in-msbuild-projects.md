---
title: "如何： 在 MSBuild 專案中使用建置事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.howto.usebuildevents
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cc8b3b21cdc9aad183f39bf709f93e022e790eef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>如何：在 MSBuild 專案中使用建置事件
建置事件是一個命令，[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]執行建置流程中的特定階段。 *建置前*建置開始前，就會發生事件;*連結前*連結步驟開始; 之前發生的事件和*建置後*組建之後發生的事件已成功結束。 只有在相關聯的建置步驟發生時，才會發生建置事件。 例如，連結前事件不會發生連結步驟不會執行。  
  
 每個組建的三個事件由在項目定義群組 command 元素 (`<Command>`) 執行和訊息項目 (`<Message>`) 也就是顯示時**MSBuild**執行建置事件。 每個項目是選擇性，而且如果您多次指定相同的項目，最後一個出現項目會優先使用。  
  
 選擇性*在組建中使用*元素 (`<`*建置事件***UseInBuild**`>`) 指出屬性群組中可以指定是否執行建置事件。 內容的值*在組建中使用*項目是`true`或`false`。 根據預設，建置事件執行，除非其對應*在組建中使用*元素設定為`false`。  
  
 下表列出每個組建事件 XML 項目：  
  
|XML 項目|描述|  
|-----------------|-----------------|  
|`PreBuildEvent`|在建置開始之前，就會執行此事件。|  
|`PreLinkEvent`|連結步驟開始之前，就會執行此事件。|  
|`PostBuildEvent`|組建完成後，就會執行此事件。|  
  
 下表列出每個*在組建中使用*項目：  
  
|XML 項目|描述|  
|-----------------|-----------------|  
|`PreBuildEventUseInBuild`|指定是否要執行*建置前*事件。|  
|`PreLinkEventUseInBuild`|指定是否要執行*連結前*事件。|  
|`PostBuildEventUseInBuild`|指定是否要執行*建置後*事件。|  
  
## <a name="example"></a>範例  
 下列範例可以 myproject.vcxproj 檔案中建立的專案項目內加入[逐步解說： 使用 MSBuild 來建立 Visual c + + 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)。 A*建置前*事件進行的 main.cpp;*連結前*事件可讓一 main.obj; 的複本及*建置後*事件會建立一份 myproject.exe。 如果使用發行組態建置專案時，會執行建置事件。 如果使用的偵錯組態建置專案時，不會執行建置事件。  
  
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
  
## <a name="see-also"></a>請參閱  
 [MSBuild （Visual c + +）](../build/msbuild-visual-cpp.md)   
 [逐步解說：使用 MSBuild 來建立 Visual C++ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)