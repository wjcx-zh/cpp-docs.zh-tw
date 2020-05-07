---
title: 命令列上的 MSBuild - C++
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: e95d99cf5c63c824bb9bade8e76bc3ca99079669
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220571"
---
# <a name="msbuild-on-the-command-line---c"></a>命令列上的 MSBuild - C++

一般來說，我們建議您使用 Visual Studio 來設定專案屬性，並叫用 MSBuild 系統。 不過，您可以直接從命令提示字元使用**MSBuild**工具。 組建程式是由您可以建立和編輯的專案檔（. .vcxproj）中的資訊所控制。 專案檔會根據組建階段、條件和事件來指定組建選項。 此外，您可以指定零個或多個命令列*選項*引數。

> **msbuild.exe** [ *project_file* ] [ *options* ]

使用 **/target** （或 **/t**）和 **/property** （或 **/p**）命令列選項來覆寫專案檔中指定的特定屬性和目標。

專案檔的基本功能是指定*目標*，這是套用至專案的特定作業，以及執行該作業所需的輸入和輸出。 專案檔可以指定一或多個目標，其中可以包含預設目標。

每個目標都包含一或*多個工作的序列。* 每項工作都是以包含一個可執行命令的 .NET Framework 類別來表示。 例如， [cl](/visualstudio/msbuild/cl-task)工作包含[cl](reference/compiling-a-c-cpp-program.md)命令。

*Task 參數*是類別工作的屬性，通常代表可執行命令的命令列選項。 例如，工作的`FavorSizeOrSpeed`參數`CL`會對應至 **/os**和 **/ot**編譯器選項。

其他工作參數支援 MSBuild 基礎結構。 例如， `Sources` task 參數會指定一組可由其他工作使用的工作。 如需 MSBuild 工作的詳細資訊，請參閱工作[參考](/visualstudio/msbuild/msbuild-task-reference)。

大部分的工作都需要輸入和輸出，例如檔案名、路徑和字串、數值或布林值參數。 例如，一般輸入是要編譯的 .cpp 原始程式檔的名稱。 重要的輸入參數是一個字串，可指定組建設定和平臺，例如 "Debug\|Win32"。 輸入和輸出是由`Item` `ItemGroup`元素中包含的一或多個使用者定義 XML 元素所指定。

專案檔也可以指定使用者定義的*屬性*和`ItemDefinitionGroup` *專案*。 屬性和專案表單名稱/值組，可以用來做為組建中的變數。 配對的名稱元件會定義*宏*，而值元件則會宣告此*宏值*。 屬性宏是使用 $ （*name*）標記法來存取，而專案宏則是使用% （*名稱*）標記法來存取。

專案檔中的其他 XML 元素可以測試宏，然後有條件地設定任何宏的值，或控制組建的執行。 您可以串連宏名稱和常值字串來產生結構，例如路徑和檔案名。 在命令列上， **/property**選項會設定或覆寫專案屬性。 無法在命令列上參考專案。

MSBuild 系統可以有條件地在另一個目標之前或之後執行目標。 此外，系統也可以根據目標所取用的檔案是否比它所發出的檔案更新，來建立目標。

如需 MSBuild 的詳細資訊，請參閱：

- [MSBuild](/visualstudio/msbuild/msbuild)MSBuild 概念的總覽。

- [MSBuild 參考](/visualstudio/msbuild/msbuild-reference)MSBuild 系統的參考資訊。

- [專案檔案架構參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)列出 MSBuild XML 架構專案，以及其屬性和父元素和子專案。 特別要注意的是[ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild)、 [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild)、 [Target](/visualstudio/msbuild/target-element-msbuild)和[Task](/visualstudio/msbuild/task-element-msbuild)元素。

- [命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)描述可以搭配 msbuild.exe 使用的命令列引數和選項。

- 工作[參考](/visualstudio/msbuild/msbuild-task-reference)描述 MSBuild 工作。 特別要注意的是 Visual C++ 所特有的這些工作： [BscMake](/visualstudio/msbuild/bscmake-task)工作、 [CL](/visualstudio/msbuild/cl-task)工作、 [CPPClean](/visualstudio/msbuild/cppclean-task)工作、 [LIB](/visualstudio/msbuild/lib-task)工作[、連結](/visualstudio/msbuild/link-task)工作、 [MIDL](/visualstudio/msbuild/midl-task)工作、 [MT](/visualstudio/msbuild/mt-task)工作、 [RC](/visualstudio/msbuild/rc-task)工作、 [SetEnv](/visualstudio/msbuild/setenv-task)工作、 [VCMessage](/visualstudio/msbuild/vcmessage-task)工作

## <a name="in-this-section"></a>本節內容

|詞彙|定義|
|----------|----------------|
|[逐步解說：使用 MSBuild 建立 c + + 專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|示範如何使用**MSBuild**建立 Visual Studio c + + 專案。|
|[如何：在 MSBuild 專案中使用建置事件](how-to-use-build-events-in-msbuild-projects.md)|示範如何指定在組建中的 particuler 階段發生的動作：組建開始之前;連結步驟開始之前;或在組建結束之後。|
|[如何：將自訂建置步驟加入至 MSBuild 專案](how-to-add-a-custom-build-step-to-msbuild-projects.md)|示範如何將使用者定義的階段新增至組建序列。|
|[如何：將自訂建置工具新增至 MSBuild 專案](how-to-add-custom-build-tools-to-msbuild-projects.md)|示範如何將組建工具與特定檔案產生關聯。|
|[如何：將自訂工具整合至專案屬性中](how-to-integrate-custom-tools-into-the-project-properties.md)|示範如何將自訂工具的選項新增至專案屬性。|
|[如何：修改目標 Framework 和平台工具組](how-to-modify-the-target-framework-and-platform-toolset.md)|示範如何編譯多個架構或工具組的專案。|

## <a name="see-also"></a>請參閱

[從命令列使用 MSVC 工具組](building-on-the-command-line.md)
