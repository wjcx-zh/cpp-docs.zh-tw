---
title: "如何：將自訂建置工具加入至 MSBuild 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.howto.addcustombuildtools"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：加入自訂建置工具"
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 如何：將自訂建置工具加入至 MSBuild 專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自訂建置工具是使用者定義的命令列工具，此工具會與特定檔案相關聯。  
  
 針對特定檔案，在專案檔 \(.vcxproj\) 中指定要執行的命令列、任何其他輸入或輸出檔，以及要顯示的訊息。  如果 **MSBuild** 判斷相對於輸入檔而言，輸出檔已過期，則會顯示訊息並執行命令列工具。  
  
 若要指定何時執行自訂建置工具，請使用專案檔中的 `CustomBuildBeforeTargets` 和 `CustomBuildAfterTargets` XML 項目之一或兩者皆使用。  例如，您可以指定自訂建置工具執行於 MIDL 編譯器之後和 C\/C\+\+ 編譯器之前。  指定 `CustomBuildBeforeTargets` 項目，以在特定目標執行之前執行工具；指定 `CustomBuildAfterTargets` 項目，以在特定目標之後執行工具；或同時指定兩個項目，以在執行兩個目標之間執行工具。  如果兩個項目均未指定，自訂建置工具會在其預設位置執行，也就是在 **MIDL** 目標之前。  
  
 自訂建置步驟和自訂建置工具會共用在 `CustomBuildBeforeTargets` 和 `CustomBuildAfterTargets` XML 項目中指定的資訊。  在專案檔中指定這些目標一次即可。  
  
### 若要加入自訂建置工具  
  
1.  將項目群組加入至專案檔，並且為每一個輸入檔加入一個項目。  如下所示，指定命令、其他輸入、輸出及訊息做為項目中繼資料。  這個範例假設在專案的相同目錄中有 "faq.txt" 檔案。  
  
    ```  
    <ItemGroup>  
      <CustomBuild Include="faq.txt">  
        <Message>Copying readme...</Message>  
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>  
        <Outputs>$(OutDir)%(Identity)</Outputs>  
      </CustomBuild>  
    </ItemGroup>  
    ```  
  
### 若要定義自訂建置工具在組建中的執行位置  
  
1.  將下列屬性群組加入至專案檔。  如果您只對於讓建置步驟在特定目標之前 \(或之後\) 執行有興趣，您必須指定至少一個目標，但您可以略過其他目標。  這個範例是在編譯之後但在連結之前執行自訂步驟。  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## 請參閱  
 [逐步解說：使用 MSBuild 來建立 Visual C\+\+ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [如何：在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [如何：將自訂建置步驟加入至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)