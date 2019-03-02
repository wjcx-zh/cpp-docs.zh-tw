---
title: 版本資訊編輯器 （c + +）
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
ms.openlocfilehash: 8382371acfd423f8c6864e816b0357e3ef11718e
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210974"
---
# <a name="version-information-editor-c"></a>版本資訊編輯器 （c + +）

版本資訊包含公司和產品識別碼、產品版本號碼，以及版權和商標通知。 具有**版本資訊編輯器**，您建立和維護這項資料會儲存在版本資訊資源。 應用程式時，不需要版本資訊資源，但它是有用的地方可以收集並識別應用程式的資訊。 安裝程式 API 也使用版本資訊。

> [!NOTE]
> Windows 標準是只能有一個版本資源，名為 VS_VERSION_INFO。

版本資訊資源有一個上層區塊以及一或多個下層區塊：頂端是單一固定的資訊區塊，底部是一或多個版本資訊區塊 (適用於其他語言和/或字元集)。 上層區塊有可編輯的數值方塊和可選取的下拉式清單。 下層區塊只有可編輯的文字方塊。

> [!NOTE]
> 在使用時**版本資訊編輯器**，在許多情況下您可以按一下滑鼠右鍵以顯示資源特定命令的捷徑功能表。 例如，如果您選取指向區塊標頭項目時，快顯功能表會顯示**新增版本區塊資訊**並**刪除版本區塊資訊**命令。

## <a name="how-to"></a>如何

**版本資訊編輯器**可讓您：

### <a name="to-edit-a-string-in-a-version-information-resource"></a>編輯版本資訊資源內的字串

選擇它，然後再次開始編輯選取的項目一次。 請變更直接在**版本資訊**資料表或在[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您所做的變更會反映在這兩個位置。

編輯時`FILEFLAGS`中的索引鍵**版本資訊編輯器**，發現無法設定**偵錯**，**私用組建**，或**Special Build**中的屬性**屬性**.rc 檔的視窗：

   - **版本資訊編輯器**設定**偵錯**屬性`#ifdef`中的資源指令碼中，根據`_DEBUG`組建旗標。

  - 如果`Private Build`機碼具有**值**中設定**版本資訊**資料表中，對應**私用組建**中的屬性**屬性**  視窗`FILEFLAGS`索引鍵會是 **，則為 True**。 如果**值**是空的則屬性會是**False**。 同樣地， **Special Build**中的索引鍵**版本資訊**資料表的繫結至**Special Build**屬性`FILEFLAGS`索引鍵。

您可以選取其中一個來排序字串區塊的資訊順序**金鑰**或**值**資料行標題。 這些標題會自動依照選取的順序重新排列資訊。

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>若要加入另一種語言 （新的版本資訊區塊） 的版本資訊

1. 按兩下版本資訊資源，在 [資源檢視](../windows/resource-view-window.md)中開啟它。

1. 在版本資訊表內按一下滑鼠右鍵，然後選擇 **新的版本資訊區塊**。

   這個命令會將額外的資訊區塊加入目前的版本資訊資源中，並在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中開啟其對應的屬性。

1. 在 [屬性]  視窗中，為新的區塊選擇適當的語言和字元集。

### <a name="to-delete-a-version-information-block"></a>刪除版本資訊區塊

1. 按兩下版本資訊資源圖示，在 [資源檢視](../windows/resource-view-window.md)中開啟它。

1. 以滑鼠右鍵按一下您想要刪除選取的區塊標頭**刪除版本資訊區塊**。

   此命令會刪除選取的標頭，並保留其餘的版本資訊。 您無法復原的動作。

### <a name="to-access-version-information-from-within-your-program"></a>存取程式內的版本資訊

如果您想要存取程式內的版本資訊，請使用 [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) 函式和 [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) 函式。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)<br/>
<!--
[Menus and Other Resources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Version Information (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)-->
