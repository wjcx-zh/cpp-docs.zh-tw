---
title: 建置系統變更 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- vc.msbuild.changes
dev_langs:
- C++
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09e0fc8c29b6fe79f90440d19cc4d025d002a944
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707404"
---
# <a name="build-system-changes"></a>建置系統變更

MSBuild 系統用於建置 Visual C++ 專案。 不過，在 Visual Studio 2008 和較早版本使用 VCBuild 系統。 某些檔案類型和依賴 VCBuild 的概念不存在，或在目前的系統中以不同方式表示。 本文件討論了目前的建置系統中的差異。

## <a name="vcproj-is-now-vcxproj"></a>.vcproj 現.vcxproj

專案檔無法再使用.vcproj 檔案的副檔名。 Visual Studio 會自動轉換舊版 Visual c + + 的格式，以供目前的系統所建立的專案檔。 如需如何手動升級專案的詳細資訊，請參閱[/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe)。

在目前的版本中，專案檔的副檔名為.vcxproj。

## <a name="vsprops-is-now-props"></a>.vsprops 現.props

在舊版中，*專案屬性工作表*是以 XML 為基礎的檔案具有.vsprops 檔案的副檔名。 專案屬性工作表可讓您指定的建置工具，例如編譯器或連結器參數，並建立使用者定義的巨集。

在目前的版本中，專案屬性工作表的副檔名為.props。

## <a name="custom-build-rules-and-rules-files"></a>自訂建置規則和.rules 檔案

在舊版中，*規則檔案*是以 XML 為基礎的檔案，副檔名為.rules 檔案名稱。 規則檔案可讓您定義自訂建置規則，並將它們合併到 Visual c + + 專案的建置程序。 自訂建置規則，它可以是一或多個檔案名稱副檔名相關聯，可讓您傳遞的輸入的檔的工具，會建立一個或多個輸出檔案。

在此版本中，自訂建置規則被以三種檔案類型、.xml、.props 和.targets，而不是.rules 檔案。 當您使用舊版的 Visual c + + 所建立的.rules 檔案移轉至目前版本相等的.xml、.props 和.targets 檔案建立並儲存在您的專案與原始的.rules 檔案中。

> [!IMPORTANT]
>  在目前的版本中，IDE 不支援建立新的規則。 因此，若要使用以舊版 Visual C++ 所建立之專案的規則檔，最簡單的方式就是將專案移轉為目前版本。

## <a name="inheritance-macros"></a>繼承巨集

在舊版中， **inherit**巨集由專案組建系統在命令列上指定繼承的屬性出現的順序。 **Noinherit**巨集造成要忽略的 $ （inherit） 的所有項目，並讓原本會被繼承，不會繼承任何屬性。 比方說，根據預設為 $ （inherit） 巨集會導致使用指定的檔案[/I （其他 Include 目錄）](../build/reference/i-additional-include-directories.md)附加至命令列編譯器選項。

在目前的版本中，藉由指定屬性的值串連一或多個常值和屬性巨集以支援繼承。 **Inherit**並 **$ （noinherit)** 巨集不支援。

在下列範例中，以分號分隔的清單被指派給屬性頁上的屬性。 清單所組成的串連*\<值 >* 常值，而值`MyProperty`屬性，會使用巨集標記法來存取，其中 **$(** <em>MyProperty</em>**)**。

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>.vcxproj.user 檔案

使用者檔案 (.vcxproj.user) 會儲存使用者特定的屬性，例如偵錯和部署設定。 .Vcxproj.user 檔案適用於特定使用者的所有專案。

## <a name="vcxprojfilters-file"></a>。 vcxproj.filters 檔案

當**方案總管中**用來將檔案加入專案時，篩選檔 (。 vcxproj.filters) 定義中的 where**方案總管中**樹狀的檢視新增檔案時，根據檔案的副檔名。

## <a name="vc-directories-settings"></a>VC + + 目錄設定

Visual c + + 目錄設定中指定[VC + + Directories Property Page](../ide/vcpp-directories-property-page.md)。 在舊版的 Visual Studio 中，目錄設定會套用每個使用者而 sysincl.dat 檔案中指定的排除的目錄清單。

您無法變更的 VC + + 目錄設定，如果您執行[devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe)在命令列。 您也無法變更設定如果您開啟**工具**功能表上，按一下**匯入和匯出設定**，然後選取**重設所有設定**選項。

移轉 VC + + 目錄設定從舊版 Visual c + + 所建立的.vssettings 檔。 開啟**工具**功能表上，按一下**匯入和匯出設定**，選取**匯入選取的環境設定**，然後依照精靈的指示進行。 或當您啟動 Visual Studio 第一次，在**選擇預設環境設定**對話方塊中，選取**從舊版移轉我符合資格的設定，並將其套用的預設值選取下面**。

## <a name="see-also"></a>另請參閱

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)