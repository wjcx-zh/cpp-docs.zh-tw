---
title: 新增 ATL 對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: ebbb610debe5d480cd1161149f89c4d357f9cd02
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275791"
---
# <a name="adding-an-atl-dialog-box"></a>新增 ATL 對話方塊

若要到您的專案新增 ATL 對話方塊，您的專案必須 ATL 專案或包含 ATL 支援的 MFC 專案。 您可以使用 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)建立 ATL 應用程式，或[將 ALT 物件新增至 MFC 應用程式](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)，以實作 MFC 應用程式的 ATL 支援。

根據預設，ATL 對話方塊精靈會實作衍生自的對話方塊[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 這個類別包含用於裝載 ActiveX 和 Windows 控制項的支援。 如果精靈已產生程式碼之後，您不會想的 ActiveX 控制項支援，額外負荷，取代的所有執行個體`CAxDialogImpl`加[CSimpleDialog](../../atl/reference/csimpledialog-class.md)或[CDialogImpl](../../atl/reference/cdialogimpl-class.md)作為基底類別.

> [!NOTE]
> `CSimpleDialog` 建立支援 Windows 通用控制項的強制回應對話方塊方塊。 `CDialogImpl` 建立其中一個強制回應或非強制回應對話方塊。

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>將 ATL 對話方塊資源新增至您的專案

1. 建立 ATL 專案使用[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)。

1. 從[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)，以滑鼠右鍵按一下專案名稱，然後按一下**新增**從捷徑功能表。 按一下 **加入類別**。

1. 在 **範本**窗格[加入類別](../../ide/add-class-dialog-box.md)] 對話方塊中，按一下 [ **ATL 對話方塊**。 按一下 **開放**顯示[ATL 對話方塊精靈](../../atl/reference/atl-dialog-wizard.md)。

如需詳細資訊，請參閱 <<c0> [ 實作對話方塊](../../atl/implementing-a-dialog-box.md)。

## <a name="see-also"></a>另請參閱

[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[視窗類別](../../atl/atl-window-classes.md)<br/>
[訊息對應](../../atl/message-maps-atl.md)
