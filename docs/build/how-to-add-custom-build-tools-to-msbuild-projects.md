---
title: 如何：將自訂建置工具加入至 MSBuild 專案
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 812932d9e668ab5ee0eb75eadbf75be3d791cddb
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220714"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>如何：將自訂建置工具加入至 MSBuild 專案

自訂群組建工具是與特定檔案相關聯的使用者定義命令列工具。

針對特定檔案，請在專案檔（. .vcxproj）中指定要執行的命令列、任何額外的輸入或輸出檔，以及要顯示的訊息。 如果**MSBuild**判斷出您的輸入檔案已過期，則會顯示訊息，並執行命令列工具。

若要指定自訂群組建工具的執行時間，請使用專案檔`CustomBuildBeforeTargets`中`CustomBuildAfterTargets`的一或兩個和 XML 元素。 例如，您可以指定自訂群組建工具在 MIDL 編譯器之後和 C/c + + 編譯器之前執行。 指定要`CustomBuildBeforeTargets`在特定目標執行之前執行工具的元素;要`CustomBuildAfterTargets`在特定目標之後執行工具的元素;或這兩個專案都可以在執行兩個目標之間執行此工具。 如果未指定任何專案，則您的自訂群組建工具會在其預設位置（位於**MIDL**目標之前）執行。

自訂群組建步驟和自訂群組建工具會共用`CustomBuildBeforeTargets`和`CustomBuildAfterTargets` XML 元素中指定的資訊。 在您的專案檔中指定這些目標一次。

### <a name="to-add-a-custom-build-tool"></a>若要新增自訂群組建工具

1. 將專案群組新增至專案檔，並為每個輸入檔案加入專案。 將命令、額外的輸入、輸出和訊息指定為專案中繼資料，如下所示。 這個範例假設 "faq" 檔案存在於與專案相同的目錄中。

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>定義自訂群組建工具將在組建中的何處執行

1. 將下列屬性群組新增至專案檔。 您必須指定至少一個目標，但如果您只想要在特定目標之前（或之後）執行組建步驟，則可以省略另一個目標。 這個範例會在編譯後但在連結之前執行自訂步驟。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>請參閱

[逐步解說：使用 MSBuild 建立 c + + 專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[如何：在 MSBuild 專案中使用建置事件](how-to-use-build-events-in-msbuild-projects.md)<br/>
[如何：將自訂建置步驟加入至 MSBuild 專案](how-to-add-a-custom-build-step-to-msbuild-projects.md)
