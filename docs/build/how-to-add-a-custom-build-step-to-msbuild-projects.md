---
title: 如何：將自訂建置步驟加入至 MSBuild 專案
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 78d40a5b4a02fe9b065bbbdde33afc6180d75381
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444912"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>如何：將自訂建置步驟加入至 MSBuild 專案

自訂群組建步驟是組建中的使用者定義步驟。 自訂群組建步驟的行為就像任何其他*命令工具*步驟，例如標準編譯或連結工具步驟。

在專案檔（. .vcxproj）中指定自訂的組建步驟。 此步驟可以指定要執行的命令列、任何額外的輸入或輸出檔，以及要顯示的訊息。 如果**MSBuild**判斷出您的輸入檔案已過期，則會顯示訊息，並執行命令。

若要在組建目標的順序中指定自訂群組建步驟的位置，請在專案檔中使用其中一個或兩個 `CustomBuildAfterTargets` 和 `CustomBuildBeforeTargets` XML 元素。 例如，您可以指定自訂群組建步驟在連結工具目標和資訊清單工具目標之前執行。 實際的可用目標集取決於您的特定組建。

指定要在特定目標執行之前執行自訂群組建步驟的 `CustomBuildBeforeTargets` 專案、在特定目標執行後執行步驟的 `CustomBuildAfterTargets` 專案，或這兩個元素，以執行兩個相鄰目標之間的步驟。 如果未指定任何專案，則您的自訂群組建工具會在其預設位置（位於**連結**目標之後）執行。

自訂群組建步驟和自訂群組建工具會共用在 `CustomBuildBeforeTargets` 中指定的資訊，以及 `CustomBuildAfterTargets` XML 元素。 因此，請只在專案檔中指定這些目標一次。

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>若要定義自訂群組建步驟所執行的內容

1. 將屬性群組新增至專案檔。 在此屬性群組中，指定命令、其輸入和輸出，以及訊息，如下列範例所示。 這個範例會從您在[逐步解說：使用C++ MSBuild 建立專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)中建立的主要 .cpp 檔案建立 .cab 檔案。

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>若要定義組建中的自訂群組建步驟將在何處執行

1. 將下列屬性群組新增至專案檔。 您可以指定這兩個目標，如果您只想要在特定目標之前或之後執行自訂步驟，也可以省略一個。 這個範例會告知**MSBuild**在編譯步驟之後，但在連結步驟之前執行自訂步驟。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>另請參閱

[逐步解說：使用 MSBuild 建立C++專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[如何：在 MSBuild 專案中使用建置事件](how-to-use-build-events-in-msbuild-projects.md)<br/>
[如何：將自訂建置工具新增至 MSBuild 專案](how-to-add-custom-build-tools-to-msbuild-projects.md)
