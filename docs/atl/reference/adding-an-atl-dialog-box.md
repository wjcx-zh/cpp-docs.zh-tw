---
title: 新增 ATL 對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: 71290cf0763ac6594985acc4cb11562efe7028e6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499369"
---
# <a name="adding-an-atl-dialog-box"></a>新增 ATL 對話方塊

若要將 ATL 對話方塊加入至專案，您的專案必須是 ATL 專案或包含 ATL 支援的 MFC 專案。 您可以使用 [ [ATL 專案嚮導]](../../atl/reference/atl-project-wizard.md) 來建立 atl 應用程式，或 [將 atl 物件加入至 mfc 應用](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) 程式，以執行 MFC 應用程式的 atl 支援。

根據預設，ATL 對話方塊 Wizard 會執行衍生自 [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)的對話方塊。 這個類別包含裝載 ActiveX 和 Windows 控制項的支援。 如果您不想要讓 ActiveX 控制項支援的額外負荷，請在嚮導產生您的程式碼後， `CAxDialogImpl` 使用 [CSimpleDialog](../../atl/reference/csimpledialog-class.md) 或 [CDialogImpl](../../atl/reference/cdialogimpl-class.md) 將的所有實例取代為您的基類。

> [!NOTE]
> `CSimpleDialog` 只會建立支援 Windows 通用控制項的強制回應對話方塊。 `CDialogImpl` 建立強制回應或非強制回應對話方塊。

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>將 ATL 對話方塊資源新增至您的專案

1. 使用 [ [Atl 專案嚮導]](../../atl/reference/atl-project-wizard.md)建立 atl 專案。

1. 在 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下專案名稱，然後從快捷方式功能表按一下 [ **新增** ]。 按一下 [加入類別]****。

1. 在 [[加入類別](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)] 對話方塊的 [**範本**] 窗格中，按一下 [ **ATL 對話方塊]**。 按一下 [ **開啟** ] 以顯示 [ATL 對話方塊 Wizard](../../atl/reference/atl-dialog-wizard.md)。

如需詳細資訊，請參閱 [執行對話方塊](../../atl/implementing-a-dialog-box.md)。

## <a name="see-also"></a>另請參閱

[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[視窗類別](../../atl/atl-window-classes.md)<br/>
[訊息對應](../../atl/message-maps-atl.md)
