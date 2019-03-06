---
title: HOW TO：新增自訂建置工具至 MSBuild 專案
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: d07c8de3405791e94193368e921c0f594845a418
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413845"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>HOW TO：新增自訂建置工具至 MSBuild 專案

自訂建置工具是與特定的檔案相關聯的使用者定義的命令列工具。

針對特定的檔案中，指定專案檔 (.vcxproj) 命令列執行，任何額外的輸入或輸出檔案和要顯示的訊息。 如果**MSBuild**判斷您的輸出檔案已過期的關於您的輸入檔案，它會顯示訊息，並執行命令列工具。

若要指定自訂建置工具在執行時，使用其中一個或多個`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`專案檔中的 XML 項目。 例如，您可以指定自訂建置工具執行之後 MIDL 編譯器和 C/c + + 編譯器之前。 指定`CustomBuildBeforeTargets`要執行此工具，才可以執行特定的目標; 項目`CustomBuildAfterTargets`後要執行此工具特定的目標; 的項目或執行此工具執行兩個目標之間的兩個項目。 如果指定兩項目，則您的自訂建置工具會執行在其預設位置，也就是之前**MIDL**目標。

自訂建置步驟和自訂建置工具共用指定的資訊`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`XML 項目。 在您的專案檔中指定這些目標一次。

### <a name="to-add-a-custom-build-tool"></a>若要加入自訂建置工具

1. 將項目群組加入至專案檔，並將每個輸入檔案項目。 為項目中繼資料，指定命令、 其他輸入、 輸出和訊息，如下所示。 這個範例假設 「 faq.txt"檔案位於與專案相同的目錄。

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>若要定義組建中的自訂建置工具會執行的位置

1. 下列的屬性群組加入至專案檔。 您必須指定至少其中一個目標，但如果您只想要讓您的建置步驟之前 （或之後） 執行省略其他特定的目標。 此範例會在編譯之後，但連結之前，執行自訂步驟。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>另請參閱

[逐步解說：使用 MSBuild 建立 Visual C++ 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[如何：在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)<br/>
[如何：將自訂建置步驟新增至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)
