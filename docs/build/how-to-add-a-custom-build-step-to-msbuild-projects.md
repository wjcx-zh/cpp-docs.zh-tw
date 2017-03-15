---
title: "如何：將自訂建置步驟加入至 MSBuild 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.howto.addcustombuildstep"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：加入自訂建置步驟"
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：將自訂建置步驟加入至 MSBuild 專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自訂建置步驟是組建中使用者定義的步驟。  自訂建置步驟的行為方式類似於任何其他「*命令工具*」\(Command Tool\) 步驟，例如標準編譯或連結工具步驟。  
  
 在專案檔 \(.vcxproj\) 中指定自訂建置步驟。  這個步驟可以指定要執行的命令列、任何其他輸入或輸出檔，以及要顯示的訊息。  如果 **MSBuild** 判斷相對於輸入檔而言，輸出檔已過期，則會顯示訊息並執行命令。  
  
 若要指定自訂建置步驟在建置目標序列中的位置，請使用專案檔中的 `CustomBuildAfterTargets` 和 `CustomBuildBeforeTargets` XML 項目之一或兩者皆指定。  例如，您可以指定自訂建置步驟執行於連結工具目標之後和資訊清單工具目標之前。  實際的可用目標集視您特定的組建而定。  
  
 指定 `CustomBuildBeforeTargets` 項目，以在特定目標執行之前執行自訂建置步驟；指定 `CustomBuildAfterTargets` 項目，以在特定目標執行之後執行該步驟；或同時指定兩個項目，以在兩個相鄰的目標之間執行該步驟。  如果兩個項目均未指定，自訂建置工具會在其預設位置執行，也就是在 **Link** 目標之後。  
  
 自訂建置步驟和自訂建置工具會共用在 `CustomBuildBeforeTargets` 和 `CustomBuildAfterTargets` XML 項目中指定的資訊。  因此，在專案檔中指定這些目標一次即可。  
  
### 若要定義自訂建置步驟所執行的內容  
  
1.  將屬性群組加入至專案檔。  在這個屬性群組中，指定命令、其輸入和輸出以及訊息，如下列範例所示。  這個範例會根據您在[逐步解說：使用 MSBuild 來建立 Visual C\+\+ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)中建立的 main.cpp 檔來建立 .cab 檔。  
  
    ```  
    <ItemDefinitionGroup>  
      <CustomBuildStep>  
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>  
        <Outputs>$(TargetName).cab</Outputs>  
        <Inputs>$(TargetFileName)</Inputs>  
      </CustomBuildStep>  
    </ItemDefinitionGroup>  
    ```  
  
### 若要定義自訂建置步驟在組建中的執行位置  
  
1.  將下列屬性群組加入至專案檔。  您可以同時指定兩個目標，但如果您只要讓自訂步驟在特定目標之前或之後執行，則可以略過其中一個目標。  這個範例告知 **MSBuild** 在編譯步驟之後但在連結步驟之前執行自訂步驟。  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## 請參閱  
 [逐步解說：使用 MSBuild 來建立 Visual C\+\+ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [如何：在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [如何：將自訂建置工具加入至 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)