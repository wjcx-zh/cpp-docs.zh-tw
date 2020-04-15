---
title: Visual Studio 專案中的屬性繼承 - C++
description: 屬性繼承在本機 (MSBuild) 可視化工作室中的工作方式C++專案。
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328468"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Visual Studio 專案中的屬性繼承

可視化工作室本機專案系統基於 MSBuild。 MSBuild 定義了用於建置任何類型的專案的檔案格式和規則。 它管理多個配置和平臺構建的大部分複雜性。 你會發現瞭解它是如何工作的是很有用的。 如果要定義自定義配置,這一點尤其重要。 或者,創建可重用的屬性集,可以共用並導入多個專案。

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>.vcxproj 檔案、.props 檔案和 .targets 檔案

專案屬性直接儲存在專案檔 ()*`.vcxproj`* 中,或者存儲*`.targets`* 在*`.props`* 專案 檔案匯入和提供預設值的其他或檔中。 對於 Visual Studio 2015,*`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* 這些文件位於 中。 對於 Visual Studio 2017,*`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* 這些*`<edition>`* 文件位於的 ,安裝的可視化工作室版本在哪裡。 在 Visual Studio 2019 中,*`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* 這些文件位於中。 屬性也會存儲在可能添加到自己的專案*`.props`* 的任何自定義檔中。 我們強烈建議您不要手動編輯這些檔。 相反,使用 IDE 中的屬性頁修改所有屬性,尤其是參與繼承的屬性,除非您對 MSBuild 有深刻的理解。

如先前所示，相同組態的相同屬性可能會在這些不同的檔案中指派不同的值。 當您建置專案時，MSBuild 引擎會以妥善定義的順序 (如下所述) 評估專案檔與所有匯入的檔案。 評估每個檔案時，任何在該檔案中定義的屬性值都會覆寫現有值。 未指定的任何值都是從之前計算的文件繼承的。 當您設置具有屬性頁的屬性時,注意設置屬性的位置也很重要。 如果在*`.props`* 檔中將屬性設置為"X",但屬性在專案檔中設置為"Y",則專案將生成屬性設置為"Y"。 如果同一屬性在專案項(如*`.cpp`* 檔)上設置為"Z",則 MSBuild 引擎將使用"Z"值。

以下是基本繼承樹狀結構：

1. MSBuild CPP 工具集中的預設設定 (..{程式檔案\MSBuild\Microsoft.Cpp_v4.0\Microsoft.Cpp.default.props,該文件匯入*`.vcxproj`*。

1. 屬性工作表

1. *`.vcxproj`* 檔。 (可以覆寫預設及屬性工作表設定)。

1. 項目中繼資料

> [!TIP]
> 在屬性頁上,在當前上下文中定義**粗體**屬性。 以一般字型表示的屬性是繼承的。

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>檢視展開的專案檔和所有匯入的值

有時候，檢視展開的檔案以判斷指定的屬性值如何繼承，十分有用。 若要檢視展開的版本，請在 Visual Studio 命令提示字元輸入下列命令  (將預留位置檔案名稱變更為您要使用的名稱)。

> **msbuild /pp:**_temp_**.txt** _myapp_**.vcxproj**

擴展的專案檔可能很大,很難理解,除非您熟悉 MSBuild。 以下是專案檔的基本結構：

1. 基本項目屬性,這些屬性未在IDE中公開。

1. 導入*`Microsoft.cpp.default.props`*,它定義了一些與工具集無關的基本屬性。

1. 全域設定屬性(在 **「設定常規」** 頁上作為**PlatformToolset 和** **Project**預設屬性公開。 這些屬性確定在下一步中*`Microsoft.cpp.props`* 導入了哪些工具集和內部屬性表。

1. 匯入*`Microsoft.cpp.props`*,它設置大多數項目預設值。

1. 匯入所有屬性表,包括*`.user`* 檔。 這些屬性表可以覆蓋除**PlatformToolset**和**Project**預設屬性之外的所有內容。

1. 專案配置屬性的其餘部分。 這些值可以覆寫屬性工作表上已設定的屬性。

1. 項目 (檔案) 以及其中繼資料。 這些項目始終是 MSBuild 計算規則中的最後一個單詞,即使它們發生在其他屬性和導入之前也是如此。

有關詳細資訊,請參閱[MSBuild 屬性](/visualstudio/msbuild/msbuild-properties)。

## <a name="build-configurations"></a>組建組態

組態只是已指定名稱的任意一組屬性。 Visual Studio 提供調試和發佈配置。 每個屬性都適當地為調試生成或發佈生成設置各種屬性。 您可以使用**設定管理員**定義自訂配置。 它們是為特定版本的特性對屬性進行分組的便捷方法。

要更好地瞭解產生設定,應開啟**屬性管理員**。 您可以通過選擇 **「查看>屬性管理員**」或 **>「查看其他 Windows >属性管理器**」來打開它,具體取決於您的設定。 **屬性管理員**具有專案中每個配置和平臺對的節點。 在每個節點下,都是為該配置設置特定屬性*`.props`* 的屬性表(檔)的節點。

![屬性管理員](media/property-manager.png "屬性管理員")

例如,您可以轉到"屬性頁"中的"一般"窗格。 將字元集屬性更改為"未設置"而不是"使用 Unicode",然後單擊"**確定**"。 屬性管理員現在不顯示**Unicode 支援**屬性表。 它已為當前配置刪除,但它仍然存在其他配置。

如需有關屬性管理員和屬性工作表的詳細資訊，請參閱[共用或重複使用 Visual StudioC++ 專案設定](create-reusable-property-configurations.md)。

> [!TIP]
> 該檔*`.user`* 是一個舊功能。 我們建議您將其刪除,以便根據配置和平臺正確分組屬性。
