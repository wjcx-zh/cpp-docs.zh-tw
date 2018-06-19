---
title: 如何： 將自訂建置步驟加入至 MSBuild 專案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.addcustombuildstep
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa8d433b782d8436f6211ab9efe55fcaad3492ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367988"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>如何：將自訂建置步驟加入至 MSBuild 專案
自訂建置步驟會在組建中使用者定義的步驟。 自訂建置步驟的行為如同任何其他*命令工具*步驟中，例如標準編譯或連結工具的步驟。  
  
 專案檔 (.vcxproj) 中指定自訂建置步驟。 此步驟可以指定任何其他輸入或輸出檔案和要顯示的訊息執行命令列。 如果**MSBuild**判斷的輸出檔已過期，關於您輸入的檔案，它會顯示訊息，並執行該命令。  
  
 若要指定位置的自訂建置步驟的建置目標序列中，使用一或兩個`CustomBuildAfterTargets`和`CustomBuildBeforeTargets`專案檔中的 XML 項目。 例如，您可以指定自訂建置步驟執行之後連結工具目標、 資訊清單工具、 目標之前。 實際的可用目標集取決於您特定的組建。  
  
 指定`CustomBuildBeforeTargets`前執行之特定目標，執行自訂建置步驟的項目`CustomBuildAfterTargets`項目之後要執行的步驟執行之特定目標或這兩個項目來執行兩個相鄰的目標之間的步驟。 如果指定兩項目，則您的自訂建置工具執行其預設位置，也就是之後在**連結**目標。  
  
 自訂建置步驟和自訂建置工具共用指定的資訊`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`XML 項目。 因此，指定這些目標只一次專案檔中。  
  
### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>若要定義自訂建置步驟所執行的內容  
  
1.  屬性群組加入至專案檔。 在此屬性群組中，指定命令、 其輸入和輸出和訊息，如下列範例所示。 這個範例會從您建立的 main.cpp 檔案建立.cab 檔案[逐步解說： 使用 MSBuild 來建立 Visual c + + 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)。  
  
    ```  
    <ItemDefinitionGroup>  
      <CustomBuildStep>  
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>  
        <Outputs>$(TargetName).cab</Outputs>  
        <Inputs>$(TargetFileName)</Inputs>  
      </CustomBuildStep>  
    </ItemDefinitionGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>若要定義組建中自訂建置步驟會執行位置  
  
1.  下列的屬性群組加入至專案檔。 您可以指定兩個目標，或如果您只想要執行之前或之後之特定目標的自訂步驟省略其中一個。 這個範例會告知**MSBuild**編譯步驟之後，但連結步驟之前執行的自訂步驟。  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 使用 MSBuild 來建立 Visual c + + 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [如何： 在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [如何：將自訂建置工具新增至 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)