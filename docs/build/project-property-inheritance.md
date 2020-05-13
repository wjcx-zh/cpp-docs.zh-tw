---
title: Visual Studio 專案中的屬性繼承 - C++
description: 屬性繼承在原生（MSBuild） Visual Studio c + + 專案中的運作方式。
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

Visual Studio 的原生專案系統是以 MSBuild 為基礎。 MSBuild 會定義用來建立任何類型專案的檔案格式和規則。 它會管理建立多個設定和平臺的大部分複雜性。 您會發現瞭解其運作方式很有説明。 如果您想要定義自訂設定，這一點特別重要。 或者，建立可重複使用的屬性集，您可以共用並匯入至多個專案。

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>.vcxproj 檔案、.props 檔案和 .targets 檔案

專案屬性會直接儲存在專案檔（*`.vcxproj`*）中，或是存放在*`.targets`* 專案*`.props`* 檔匯入的其他或檔案中，並提供預設值。 針對 Visual Studio 2015，這些檔案位於*`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`*。 針對 Visual Studio 2017，這些檔案位於*`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`*，其中*`<edition>`* 是已安裝 Visual Studio 版本。 在 Visual Studio 2019 中，這些檔案位於*`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`*。 屬性也會儲存在您可以*`.props`* 加入至自己專案的任何自訂檔案中。 我們強烈建議您不要手動編輯這些檔案。 相反地，請使用 IDE 中的屬性頁來修改所有屬性，特別是參與繼承的內容，除非您對 MSBuild 有深入的瞭解。

如先前所示，相同組態的相同屬性可能會在這些不同的檔案中指派不同的值。 當您建置專案時，MSBuild 引擎會以妥善定義的順序 (如下所述) 評估專案檔與所有匯入的檔案。 評估每個檔案時，任何在該檔案中定義的屬性值都會覆寫現有值。 未指定的任何值都會繼承自先前評估的檔案。 當您使用屬性頁來設定屬性時，請務必留意您設定的位置。 如果您在檔案中*`.props`* 將屬性設定為 "X"，但屬性在專案檔中設定為 "y"，則專案會建立，並將屬性設定為 "y"。 如果專案專案（例如*`.cpp`* 檔案）上的相同屬性設定為 "z"，則 MSBuild 引擎會使用 "z" 值。

以下是基本繼承樹狀結構：

1. MSBuild CPP 工具組的預設設定（.。\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props，由*`.vcxproj`* 檔案匯入）。

1. 屬性工作表

1. *`.vcxproj`* 文字檔. (可以覆寫預設及屬性工作表設定)。

1. 項目中繼資料

> [!TIP]
> 在屬性頁上，以**粗體顯示**的屬性是在目前的內容中定義。 以一般字型表示的屬性是繼承的。

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>檢視展開的專案檔和所有匯入的值

有時候，檢視展開的檔案以判斷指定的屬性值如何繼承，十分有用。 若要檢視展開的版本，請在 Visual Studio 命令提示字元輸入下列命令  (將預留位置檔案名稱變更為您要使用的名稱)。

> **msbuild /pp:**_temp_**.txt** _myapp_**.vcxproj**

擴充的專案檔可能會很大，而且很容易瞭解，除非您已經熟悉 MSBuild。 以下是專案檔的基本結構：

1. 不會在 IDE 中公開的基本專案屬性。

1. 匯入*`Microsoft.cpp.default.props`*，它會定義一些與工具組無關的基本屬性。

1. 全域設定屬性（在 [設定] **[一般**] 頁面上公開為**PlatformToolset**和**專案**預設屬性）。 這些屬性會決定下一個步驟中匯入的工具*`Microsoft.cpp.props`* 組和內建屬性工作表。

1. 匯入*`Microsoft.cpp.props`*，這會設定大部分的專案預設值。

1. 匯入所有屬性工作表，包括*`.user`* 檔案。 這些屬性工作表可以覆寫**PlatformToolset**和 Project 預設屬性以外的所有**專案**。

1. 其餘的專案設定屬性。 這些值可以覆寫屬性工作表上已設定的屬性。

1. 項目 (檔案) 以及其中繼資料。 這些專案一律是 MSBuild 評估規則中的最後一個單字，即使它們發生在其他屬性和匯入之前也一樣。

如需詳細資訊，請參閱[MSBuild 屬性](/visualstudio/msbuild/msbuild-properties)。

## <a name="build-configurations"></a>組建組態

組態只是已指定名稱的任意一組屬性。 Visual Studio 提供了 Debug 和 Release 設定。 每個都會針對 debug 組建或發行組建適當地設定各種屬性。 您可以使用**Configuration Manager**來定義自訂設定。 它們是針對特定組建類別的屬性進行分組的便利方式。

若要更加瞭解組建設定，請開啟**屬性管理員**。 您可以視您的設定而定，選擇 [ **view > 屬性管理員**] 或 [ **View] > 其他 Windows > 屬性管理員**] 來開啟它。 **屬性管理員**在專案中具有每個設定和平臺配對的節點。 在每個節點底下，都是屬性工作表（*`.props`* 檔案）的節點，其會針對該設定設定一些特定屬性。

![屬性管理員](media/property-manager.png "屬性管理員")

例如，您可以移至屬性頁中的 [一般] 窗格。 將 [字元集] 屬性變更為 [未設定]，而不是 [使用 Unicode]，然後按一下 **[確定]**。 屬性管理員現在不會顯示**Unicode 支援**屬性工作表。 它會從目前的設定中移除，但仍會用於其他設定。

如需有關屬性管理員和屬性工作表的詳細資訊，請參閱[共用或重複使用 Visual StudioC++ 專案設定](create-reusable-property-configurations.md)。

> [!TIP]
> *`.user`* 檔案是舊版功能。 我們建議您將其刪除，以根據設定和平臺將屬性正確分組。
