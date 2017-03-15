---
title: "如何：在 MSBuild 專案中使用建置事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.howto.usebuildevents"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：在專案中使用建置事件"
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：在 MSBuild 專案中使用建置事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建置事件就是 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 在建置流程中的特定階段執行的命令。  *建置前 \(Pre\-Build\)* 事件發生於建置開始前； *連結前* 事件發生於結步驟開始之前；而在 *建置後* 事件發生於建置成功結束之後。  只有在相關聯的建置步驟發生時，會發生建置事件。  例如，若未執行連結步驟，則不會發生連結前事件。  
  
 在項目定義群組中，這三個建置事件都會以當 **MSBuild** 執行建置事件時所執行的命令項目 \(`<Command>`\) 和所顯示的訊息項目 \(`<Message>`\) 來表示。  每一個項目都是選擇性項目，若您多次指定相同的項目，則最後一次優先。  
  
 可以在屬性群組中指定選擇性「*在建置中使用*」\(Use\-In\-Build\) 項目 \(`<`*build\-event***UseInBuild**`>`\)，表示是否已執行建置事件。  「*在建置中使用*」\(Use\-In\-Build\) 項目的內容值不是 `true` 就是 `false`。  根據預設，除非建置事件的對應「*在建置中使用*」\(Use\-In\-Build\) 項目已設為 `false`，否則會執行建置事件。  
  
 下表列出每一個建置事件 XML 項目：  
  
|XML 項目|說明|  
|------------|--------|  
|`PreBuildEvent`|這個事件會在建置開始之前執行。|  
|`PreLinkEvent`|這個事件會在連結步驟開始之前執行。|  
|`PostBuildEvent`|這個事件會在建置完成之後執行。|  
  
 下表列出每一個「*在建置中使用*」\(Use\-In\-Build\) 項目：  
  
|XML 項目|說明|  
|------------|--------|  
|`PreBuildEventUseInBuild`|指定是否要執行「*建置前*」\(Pre\-Build\) 事件。|  
|`PreLinkEventUseInBuild`|指定是否要執行「*連結前*」\(Pre\-Link\) 事件。|  
|`PostBuildEventUseInBuild`|指定是否要執行「*建置後*」\(Post\-Build\) 事件。|  
  
## 範例  
 下列範例可以加入至在[逐步解說：使用 MSBuild 來建立 Visual C\+\+ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)中建立之 myproject.vcxproj 檔的 Project 項目內部。  「*建置前*」\(Pre\-Build\) 事件會建立 main.cpp 的複本，「*連結前*」\(Pre\-Link\) 事件會建立 main.obj 的複本，而「*建置後*」\(Post\-Build\) 事件則會建立 myproject.exe 的複本。  如果使用發行組態建立專案，則會執行建置事件。  如果使用偵錯組態建立專案，則不會執行建置事件。  
  
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
  
## 請參閱  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)   
 [逐步解說：使用 MSBuild 來建立 Visual C\+\+ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)