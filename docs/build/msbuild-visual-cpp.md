---
title: MSBuild 命令列-C++
ms.date: 12/12/2018
f1_keywords:
- MSBuild
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: 565b1c47b4476fa7cb830e15b978b389f4344ee1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273309"
---
# <a name="msbuild-on-the-command-line---c"></a>MSBuild 命令列-C++

一般情況下，我們建議您使用 Visual Studio，來設定專案屬性，並叫用 MSBuild 系統。 不過，您可以使用**MSBuild**直接從命令提示字元工具。 建置程序是由在專案檔 (.vcxproj)，您可以建立和編輯資訊控制。 專案檔指定為基礎的建置選項建置階段、 條件和事件。 此外，您可以指定零或多個命令列*選項*引數。

> **msbuild.exe** [ *project_file* ] [ *options* ]

使用 **/target** (或 **/t**) 和 **/property** (或 **/p**) 命令列選項來覆寫特定的屬性和目標在專案檔中指定。

專案檔有一個重要功能是指定*目標*，這是套用至您的專案，並輸入和輸出執行該作業所需的特定作業。 專案檔可以指定一或多個目標，其中可以包括預設目標。

每個目標是由一或多個序列所組成*任務*。 每個工作被以.NET Framework 類別，其中包含一個可執行命令。 例如， [CL 工作](/visualstudio/msbuild/cl-task)包含[cl.exe](reference/compiling-a-c-cpp-program.md)命令。

A*工作參數*是類別工作的屬性，通常代表可執行命令的命令列選項。 例如，`FavorSizeOrSpeed`的參數`CL`工作會對應至 **/Os**並 **/Ot**編譯器選項。

其他工作參數都支援 MSBuild 基礎結構。 比方說，`Sources`工作參數指定一組可供其他工作的工作。 如需有關 MSBuild 工作的詳細資訊，請參閱[工作參考](/visualstudio/msbuild/msbuild-task-reference)。

大部分工作都需要輸入和輸出，例如檔案名稱、 路徑和字串、 數值或布林參數。 比方說，一般輸入是編譯的.cpp 原始程式檔的名稱。 重要的輸入的參數是一個字串，指定建置組態與平台，例如 「 偵錯\|Win32"。 輸入和輸出由一或多個使用者定義的 XML`Item`中所包含的項目`ItemGroup`項目。

專案檔也可以指定使用者定義*屬性*並`ItemDefinitionGroup`*項目*。 屬性和項目會形成名稱/值組，可用來當做組建中的變數。 定義一組的名稱元件*巨集*，和值的部分宣告*巨集值*。 屬性巨集可使用 $(*名稱*) 表示法和項目巨集使用存取 %(*名稱*) 標記法。

在專案檔中的其他 XML 項目可以測試巨集，然後有條件地設定任何巨集的值或控制組建的執行。 巨集名稱和常值字串可以串連來產生建構，例如路徑和檔案名稱。 在命令列 **/property**選項可以設定或覆寫專案屬性。 在命令列上，不能參考項目。

MSBuild 系統可以有條件地目標之前或之後執行另一個目標。 此外，系統可以建置目標，根據目標所取用的檔案是否比更新的檔案就會發出。

如需 MSBuild 的詳細資訊，請參閱：

- [MSBuild](/visualstudio/msbuild/msbuild)概觀的 MSBuild 概念。

- [MSBuild 參考](/visualstudio/msbuild/msbuild-reference)參考 MSBuild 系統的相關資訊。

- [專案檔案結構描述參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)列出 MSBuild XML 結構描述的項目，以及其屬性和父系和子系的項目。 請特別注意[ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild)， [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild)，[目標](/visualstudio/msbuild/target-element-msbuild)，以及[工作](/visualstudio/msbuild/task-element-msbuild)項目。

- [命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)說明的命令列引數和選項可供您使用 msbuild.exe。

- [工作參考](/visualstudio/msbuild/msbuild-task-reference)描述 MSBuild 工作。 特別注意這些工作，也就是特定視覺效果C++:[BscMake 工作](/visualstudio/msbuild/bscmake-task)， [CL 工作](/visualstudio/msbuild/cl-task)， [CPPClean 工作](/visualstudio/msbuild/cppclean-task)， [LIB 工作](/visualstudio/msbuild/lib-task)，[連結工作](/visualstudio/msbuild/link-task)， [MIDL 工作](/visualstudio/msbuild/midl-task)， [MT 工作](/visualstudio/msbuild/mt-task)， [RC 工作](/visualstudio/msbuild/rc-task)， [SetEnv 工作](/visualstudio/msbuild/setenv-task)， [VCMessage 工作](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>本節內容

|詞彙|定義|
|----------|----------------|
|[逐步解說：使用 MSBuild 建立 Visual C++ 專案](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|示範如何建立視覺效果C++使用的專案**MSBuild**。|
|[如何：在 MSBuild 專案中使用建置事件](how-to-use-build-events-in-msbuild-projects.md)|示範如何指定在組建中 particuler 階段，就會發生的動作： 在建置開始之前;連結步驟開始; 之前或在建置結束後。|
|[如何：將自訂建置步驟新增至 MSBuild 專案](how-to-add-a-custom-build-step-to-msbuild-projects.md)|示範如何將使用者定義的階段新增至組建順序。|
|[如何：將自訂建置工具新增至 MSBuild 專案](how-to-add-custom-build-tools-to-msbuild-projects.md)|示範如何建置工具相關聯的特定檔案。|
|[如何：將自訂工具整合至專案屬性中](how-to-integrate-custom-tools-into-the-project-properties.md)|示範如何將自訂工具的選項新增至專案屬性。|
|[如何：修改目標 Framework 和平台工具組](how-to-modify-the-target-framework-and-platform-toolset.md)|示範如何編譯專案，以供多個架構或工具組。|

## <a name="see-also"></a>另請參閱

[從命令列使用 MSVC 工具組](building-on-the-command-line.md)
