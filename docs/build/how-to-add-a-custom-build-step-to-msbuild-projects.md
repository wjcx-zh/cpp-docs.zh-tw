---
title: HOW TO：新增自訂建置步驟至 MSBuild 專案
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.addcustombuildstep
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 57b7636c58a245bfea3a71dfb6aa7ee853329f19
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413221"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>HOW TO：新增自訂建置步驟至 MSBuild 專案

自訂建置步驟是在組建中使用者定義的步驟。 自訂建置步驟的行為就像任何其他*命令工具*步驟中，例如標準編譯或連結工具的步驟。

專案檔 (.vcxproj) 中指定自訂建置步驟。 步驟可以指定命令列執行的任何其他輸入或輸出檔案，以及要顯示的訊息。 如果**MSBuild**判斷您的輸出檔案已過期有關您的輸入檔案，它會顯示訊息，並執行命令。

若要指定位置的自訂建置步驟的建置目標序列中，使用其中一個或多個`CustomBuildAfterTargets`和`CustomBuildBeforeTargets`專案檔中的 XML 項目。 例如，您可以指定自訂建置步驟會在連結工具目標之後，以及資訊清單工具、 目標之前執行。 實際的可用目標集取決於您特定的組建。

指定`CustomBuildBeforeTargets`項目來執行自訂建置步驟之前執行特定目標，`CustomBuildAfterTargets`後執行特定目標，執行步驟的項目或這兩個項目來執行兩個相鄰的目標之間的步驟。 如果指定兩項目，則您的自訂建置工具會執行在其預設位置，也就是之後**連結**目標。

自訂建置步驟和自訂建置工具共用指定的資訊`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`XML 項目。 因此，指定這些目標只是一次在您的專案檔中。

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>若要定義自訂建置步驟所執行的內容

1. 加入專案檔中的屬性群組。 此屬性群組中指定的命令、 其輸入和輸出和訊息，如下列範例所示。 這個範例會從您建立的 main.cpp 檔案來建立.cab 檔案[逐步解說：使用 MSBuild 來建立 Visual c + + 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)。

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(TargetFileName)</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>若要定義組建中自訂建置步驟會執行的位置

1. 下列的屬性群組加入至專案檔。 您可以指定兩個目標，或如果您只想要執行之前或之後的特定目標的自訂步驟省略其中一個。 此範例會告訴**MSBuild**編譯步驟之後，但連結步驟之前，執行自訂步驟。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>另請參閱

[逐步解說：使用 MSBuild 建立 Visual C++ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[如何：在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)<br/>
[如何：將自訂建置工具新增至 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)
