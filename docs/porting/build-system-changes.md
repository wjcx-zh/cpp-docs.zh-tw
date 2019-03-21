---
title: Visual Studio 2010 中的建置系統變更
ms.date: 11/04/2016
f1_keywords:
- vc.msbuild.changes
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: 621e62379657da66d6eaec7a3ceff780fd610066
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57828168"
---
# <a name="build-system-changes"></a>建置系統變更

MSBuild 系統用於建置 Visual C++ 專案。 不過，在 Visual Studio 2008 和較早版本使用 VCBuild 系統。 依賴 VCBuild 的某些檔案類型和概念已不存在，或是目前系統以不同方式表示。 本文探討目前建置系統中的差異。

## <a name="vcproj-is-now-vcxproj"></a>.vcproj 現已變更為 .vcxproj

專案檔已不再使用 .vcproj 副檔名。 Visual Studio 會將舊版 Visual C++ 建立的專案檔自動轉換為目前系統使用的格式。 如需如何手動升級專案的詳細資訊，請參閱 [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe)。

在目前的版本中，專案檔的副檔名為 .vcxproj。

## <a name="vsprops-is-now-props"></a>.vsprops 現已變更為 .props

在舊版中，「專案屬性工作表」是 XML 檔案，且副檔名為 .vsprops。 專案屬性工作表可讓您指定建置工具的交換器，像是編譯器或連結器，以及建立使用者定義的巨集。

在目前的版本中，專案屬性工作表的副檔名為 .props。

## <a name="custom-build-rules-and-rules-files"></a>自訂建置規則及 .rules 檔案

在舊版中，「規則檔」是 XML 檔案，且副檔名為 .rules。 規則檔可讓您定義自訂建置規則，以及將這些規則納入 Visual C++ 專案的建置流程。 自訂建置規則可與一或多個副檔名建立關聯，讓您能夠將輸入檔傳遞到可建立一或多個輸出檔案的工具。

在此版本中，自訂建置規則會以三種檔案類型呈現，分別為 .xml、.props 及 .targets，而非 .rules 檔案。 當使用舊版 Visual C++ 建立的 .rules 檔案移轉至目前版本時，就會建立對等的 .xml、.props 及 .targets 檔案，並與原始的 .rules 檔案一併儲存在您的專案中。

> [!IMPORTANT]
>  在目前版本中，IDE 不支援建立新規則。 因此，若要使用以舊版 Visual C++ 所建立之專案的規則檔，最簡單的方式就是將專案移轉為目前版本。

## <a name="inheritance-macros"></a>繼承巨集

在舊版中，**$(Inherit)** 巨集會指定繼承屬性在命令列上顯示的順序，且該命令列是由專案建置系統撰寫。 **$(NoInherit)** 巨集會導致忽略所有 $(Inherit) 的存在，且會使所有應繼承的屬性均不受繼承。 例如，根據預設，$(Inherit) 巨集會導致使用 [/I (額外包含目錄)](../build/reference/i-additional-include-directories.md) 編譯器選項指定的檔案附加至命令列。

在目前版本中，可透過將屬性的值指定為一或多個常值及屬性巨集的串連來支援繼承。 不支援 **$(Inherit)** 及 **$(NoInherit)** 巨集。

在下列範例中，會將以分號分隔的清單指派到屬性頁上的屬性。 此清單由 *\<value>* 常值和 `MyProperty` 屬性的值串連而成，且透過使用巨集標記法 **$(**<em>MyProperty</em>**)** 加以存取。

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>.vcxproj.user 檔案

使用者檔案 (.vcxproj.user) 會儲存使用者指定的屬性，例如偵錯及部署設定。 vcxproj.user 檔案適用於特定使用者的全部專案。

## <a name="vcxprojfilters-file"></a>.vcxproj.filters 檔案

使用**方案總管**將檔案新增至專案時，篩選檔 (.vcxproj.filters) 會根據檔案的副檔名，定義要在**方案總管**樹狀檢視中的哪個位置新增檔案。

## <a name="vc-directories-settings"></a>VC++ 目錄設定

Visual C++ 目錄設定會在 [VC++ 目錄屬性頁](../ide/vcpp-directories-property-page.md)上指定。 在舊版的 Visual Studio 中，會在 sysincl.dat 檔案中指定目錄設定套用已排除目錄的各使用者及清單。

若您在命令列執行 [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe)，就無法變更 VC++ 目錄設定。 即使您開啟 [工具] 功能表，按一下 [匯入和匯出設定]，然後選取 [重設所有設定] 選項，也同樣無法變更設定。

從使用舊版 Visual C++ 建立的 .vssettings 檔案移轉 VC++ 目錄設定。 開啟 [工具] 功能表，按一下 [匯入和匯出設定]，選取 [匯入選取的環境設定]，接著遵循精靈中的指示。 或者在您初次啟動 Visual Studio 時，在 [選擇預設環境設定] 對話方塊中，選取 [從舊版移轉我的合適設定，並連同底下選取的預設值一起套用]。

## <a name="see-also"></a>另請參閱

[MSBuild on the Command Line - C++](../build/msbuild-visual-cpp.md) (命令列上的 MSBuild)
