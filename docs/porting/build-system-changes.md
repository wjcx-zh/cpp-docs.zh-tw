---
title: VCBuild 與 MSBuild 的比較
description: VIsual Studio C++組建系統在 Visual Studio 2010 中已從 VCBuild 變更為 MSBuild。
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: afa9324d6074db72fd065cfa07c16349f86a615c
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626605"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild 與 MSBuild 的比較：在 Visual Studio 2010 中組建系統變更

C++專案的 MSBuild 系統是在 Visual Studio 2010 中引進。 在 Visual Studio 2008 和較舊版本中，使用 VCBuild 系統。 相依于 VCBuild 的特定檔案類型和概念不存在，也不會在 MSBuild 中以不同方式表示。 本文探討目前建置系統中的差異。 若要將 Visual Studio 2008 專案轉換成 MSBuild，您必須使用 Visual Studio 2010。 轉換專案之後，您應該使用最新版本的 Visual Studio 升級至目前的 IDE 和編譯器工具組。 如需詳細資訊，包括如何取得 Visual Studio 2010，請參閱[Visual Studio 2008 的指示](use-native-multi-targeting.md#instructions-for-visual-studio-2008)。

下列各節摘要說明從 VCBuild 到 MSBuild 的變更。 如果您的 VCBuild 專案具有 MSBuild 無法辨識的自訂群組建規則或宏，請參閱[Visual Studio C++專案-](../build/creating-and-managing-visual-cpp-projects.md)以瞭解如何將這些指令轉譯為 msbuild 系統。 從 VCBuild 到 MSBuild 的初始轉換只是一個中間步驟。 不需要完全正確地取得專案檔，或讓程式編譯而不會發生錯誤。 您只會使用 Visual Studio 2010 將專案轉換成 MSBuild 格式，讓專案可以在最新版本的 Visual Studio 中運作。

## <a name="vcproj-is-now-vcxproj"></a>.vcproj 現已變更為 .vcxproj

專案檔已不再使用 .vcproj 副檔名。 Visual Studio 2010 會自動將舊版視覺效果C++所建立的專案檔轉換成 MSBuild 格式，這會使用專案檔的 .vcxproj 副檔名。

## <a name="vsprops-is-now-props"></a>.vsprops 現已變更為 .props

在 Visual Studio 2008 和更早版本中，*專案屬性工作表*是以 XML 為基礎的檔案，副檔名為 .vsprops。 專案屬性工作表可讓您指定建置工具的交換器，像是編譯器或連結器，以及建立使用者定義的巨集。 在 MSBuild 中，專案屬性工作表的副檔名為 .props。

## <a name="custom-build-rules-and-rules-files"></a>自訂群組建規則和規則檔案

在 Visual Studio 2008 和更早版本中，*規則*檔是以 XML 為基礎的檔案，其副檔名為 rules。 規則檔可讓您定義自訂建置規則，以及將這些規則納入 Visual Studio C++ 專案的建置流程。 自訂建置規則可與一或多個副檔名建立關聯，讓您能夠將輸入檔傳遞到可建立一或多個輸出檔案的工具。

在 MSBuild 系統中，自訂群組建規則會以三種檔案類型（.xml、.props 和 .targets）來表示，而不是使用 rules 檔案。 當使用舊版視覺效果C++所建立的 rules 檔案遷移至 Visual Studio 2010 時，會建立對應的 .xml、.props 和 .targets 檔案，並與原始的 rules 檔案一起儲存在您的專案中。

> [!IMPORTANT]
> 在 Visual Studio 2010 中，IDE 不支援建立新的規則。 基於這個理由，使用舊版視覺效果C++所建立之專案中的規則檔案最簡單的方式，就是將專案遷移至 Visual Studio 2010。

## <a name="inheritance-macros"></a>繼承宏

在 Visual Studio 2008 和更早版本中， **$ （Inherit）** 宏會指定繼承屬性在專案組建系統所組成的命令列上出現的順序。 **$(NoInherit)** 巨集會導致忽略所有 $(Inherit) 的存在，且會使所有應繼承的屬性均不受繼承。 例如，根據預設，$(Inherit) 巨集會導致使用 [/I (額外包含目錄)](../build/reference/i-additional-include-directories.md) 編譯器選項指定的檔案附加至命令列。

在 Visual Studio 2010 中，藉由將屬性的值指定為一或多個常值和屬性宏的串連，即可支援繼承。 不支援 **$(Inherit)** 及 **$(NoInherit)** 巨集。

在下列範例中，會將以分號分隔的清單指派到屬性頁上的屬性。 此清單由 *\<value>* 常值和 `MyProperty` 屬性的值串連而成，且透過使用巨集標記法 **$(** <em>MyProperty</em> **)** 加以存取。

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>. .vcxproj. user 檔案

使用者檔案 (.vcxproj.user) 會儲存使用者指定的屬性，例如偵錯及部署設定。 *.Vcxproj*會套用至特定使用者的所有專案。

## <a name="vcxprojfilters-file"></a>.vcxproj. filters 檔案

當**方案總管**用來將檔案新增至專案時，篩選器檔案（ *. .vcxproj. filters*）會根據檔案的副檔名，定義要在**方案總管**樹狀檢視中新增檔案的位置。

## <a name="vc-directories-settings"></a>VC + + 目錄設定

Visual C++ 目錄設定會在 [VC++ 目錄屬性頁](../ide/vcpp-directories-property-page.md)上指定。 在 Visual Studio 2008 和更早版本中，目錄設定會套用每個使用者，而排除的目錄清單則指定于*sysincl .dat*檔案中。 

若您在命令列執行 [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe)，就無法變更 VC++ 目錄設定。 即使您開啟 [工具] 功能表，按一下 [匯入和匯出設定]，然後選取 [重設所有設定] 選項，也同樣無法變更設定。

若要從舊版 Visual Studio 所建立的 *.vssettings*檔案遷移 VC + + 目錄設定：

1. 開啟 [**工具**] 功能表，然後按一下 [匯**入和匯出設定**]
2. 選取 [匯**入選取的環境設定**]
3. 遵循 wizard 中的指示。

## <a name="see-also"></a>請參閱

[MSBuild on the Command Line - C++](../build/msbuild-visual-cpp.md) (命令列上的 MSBuild)
