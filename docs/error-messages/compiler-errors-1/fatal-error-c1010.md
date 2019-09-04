---
title: 嚴重錯誤 C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 0315af63e9fdbbb0b136a85a23cb28936dee6836
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273555"
---
# <a name="fatal-error-c1010"></a>嚴重錯誤 C1010

> 尋找先行編譯的標頭時出現非預期的檔案結尾。 您是否忘了將「#include*名稱*」新增至您的來源？

## <a name="remarks"></a>備註

[/Yu](../../build/reference/yu-use-precompiled-header-file.md)指定的 include 檔案未列在原始程式檔中。 在許多 Visual Studio C++專案類型中, 預設會啟用此選項。 此選項所指定的預設 include 檔案為*pch*, 或 Visual Studio 2017 和更早版本中的*stdafx.h* 。

在 Visual Studio 環境中, 請使用下列其中一種方法來解決此錯誤:

- 請確定您不會不慎刪除、重新命名或移除目前專案中的*pch*標頭檔或*pch*原始檔案。 (在較舊的專案中, 這些檔案可能會命名為*stdafx.h*和*stdafx.h*)。

- 請確定*pch*或*stdafx.h*標頭檔已包含在來源檔案中的任何其他程式碼或預處理器指示詞之前。 (在 Visual Studio 中, 此標頭檔是由先行**編譯標頭檔**專案屬性指定)。

- 您可以關閉先行編譯標頭檔的使用。 如果您關閉先行編譯的標頭, 可能會嚴重影響組建效能。

### <a name="to-turn-off-precompiled-headers"></a>若要關閉先行編譯標頭檔

若要關閉專案中的先行編譯標頭檔使用, 請遵循下列步驟:

1. 在 [**方案總管**] 視窗中, 以滑鼠右鍵按一下專案名稱, 然後選擇 [**屬性**] 以開啟 [專案**屬性頁**] 對話方塊。

1. 在 [設定] 下拉式選單中, 選取 [**所有**設定]。

1. 選取 [設定**屬性** > ] [**CC++/**  > 先行**編譯頭**檔] 屬性頁。

1. 在 [屬性] 清單中, 選取 [先行**編譯頭**檔] 屬性的下拉式清單, 然後選擇 [**不要使用先行編譯頭**檔]。 選取 [確定] 儲存您的變更。

1. 在 [**方案總管**] 視窗中, 以滑鼠右鍵按一下專案中的*pch*原始程式檔。 (在較舊的專案中, 檔案的名稱可能是*stdafx.h)。* 選擇 [**從專案排除**], 將它從組建中移除。

1. 針對您建立的每個設定使用 [**組建** > ] [**清除方案**] 功能表命令, 以刪除中繼組建目錄中的任何*project_name .pch*檔案。

## <a name="see-also"></a>另請參閱

[先行編譯標頭檔](../../build/creating-precompiled-header-files.md)\
[/Yc (建立先行編譯標頭檔)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu (使用先行編譯標頭檔)](../../build/reference/yu-use-precompiled-header-file.md)