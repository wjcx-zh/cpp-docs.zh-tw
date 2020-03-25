---
title: 版本資訊編輯器（C++）
ms.date: 02/14/2019
f1_keywords:
- vc.editors.version.F1
- vc.editors.version
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
- version information resources [C++]
- resources [C++], editing version information
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: b083ed27b6b1f471dbec9b96e7be7a6165f8d125
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214366"
---
# <a name="version-information-editor-c"></a>版本資訊編輯器（C++）

版本資訊包含公司和產品識別碼、產品版本號碼，以及版權和商標通知。 使用**版本資訊編輯器**，您可以建立和維護此資料，這會儲存在版本資訊資源中。 應用程式不需要版本資訊資源，但這是收集識別應用程式之資訊的實用位置。 安裝程式 API 也使用版本資訊。

> [!NOTE]
> Windows 標準是只能有一個版本資源，名為 VS_VERSION_INFO。

版本資訊資源有一個上層區塊以及一或多個下層區塊：頂端是單一固定的資訊區塊，底部是一或多個版本資訊區塊 (適用於其他語言和/或字元集)。 上層區塊有可編輯的數值方塊和可選取的下拉式清單。 下層區塊只有可編輯的文字方塊。

> [!NOTE]
> 使用**版本資訊編輯器**時，在許多情況下，您可以用滑鼠右鍵按一下，以顯示資源特定命令的快捷方式功能表。 例如，如果您選取 [當指向區塊標頭專案時]，快捷方式功能表會顯示新的 [**版本區塊資訊**] 和 [**刪除版本區塊資訊**] 命令。

## <a name="how-to"></a>作法

**版本資訊編輯器**可讓您：

### <a name="to-edit-a-string-in-a-version-information-resource"></a>編輯版本資訊資源內的字串

選取一次專案來選擇它，然後再次開始編輯它。 直接在**版本資訊**資料表或[屬性視窗](/visualstudio/ide/reference/properties-window)中進行變更。 您所做的變更會反映在這兩個位置。

在 [**版本資訊編輯器**] 中編輯 `FILEFLAGS` 金鑰時，請注意，您無法在 .rc 檔的 [**屬性**] 視窗中設定 [ **Debug**]、[ **Private build**] 或 [**特殊組建**] 屬性：

- **版本資訊編輯器**會根據 `_DEBUG` 組建旗標，以資源腳本中的 `#ifdef` 來設定**Debug**屬性。

- 如果 `Private Build` 索引鍵在**版本資訊**表中有設定的**值**，則 `FILEFLAGS` 索引鍵之 [**屬性**] 視窗中的對應**私用組建**屬性將會是**True**。 如果**Value**是空的，屬性將會是**False**。 同樣地，**版本資訊**表中的**特殊組建**金鑰會系結至 `FILEFLAGS` 索引鍵的**特殊組建**屬性。

您可以選取 [索引**鍵**] 或 [**值**] 資料行標題，來排序字串區塊的資訊順序。 這些標題會自動依照選取的順序重新排列資訊。

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>新增其他語言的版本資訊（新的版本資訊區塊）

1. 按兩下版本資訊資源，在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中開啟它。

1. 以滑鼠右鍵按一下 [版本資訊] 資料表，然後選擇 [**新增版本資訊區塊**]。

   這個命令會將額外的資訊區塊加入目前的版本資訊資源中，並在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中開啟其對應的屬性。

1. 在 [屬性] 視窗中，為新的區塊選擇適當的語言和字元集。

### <a name="to-delete-a-version-information-block"></a>刪除版本資訊區塊

1. 按兩下版本資訊資源圖示，在 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中開啟它。

1. 以滑鼠右鍵按一下您想要刪除的區塊標頭，然後選擇 [**刪除版本資訊區塊**]。

   此命令會刪除選取的標頭，並將其餘的版本資訊保留不變。 您無法復原此動作。

### <a name="to-access-version-information-from-within-your-program"></a>存取程式內的版本資訊

如果您想要存取程式內的版本資訊，請使用 [GetFileVersionInfo](/windows/win32/api/winver/nf-winver-getfileversioninfow) 函式和 [VerQueryValue](/windows/win32/api/winver/nf-winver-verqueryvaluew) 函式。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
[功能表與其他資源](/windows/win32/menurc/resources)<br/>
[版本資訊 (Windows)](/windows/win32/menurc/version-information)
