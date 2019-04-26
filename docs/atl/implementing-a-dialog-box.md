---
title: 實作對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 1a3084d4655e173234d3bb6e8d411b28e8968377
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198049"
---
# <a name="implementing-a-dialog-box"></a>實作對話方塊

有兩種方式可 ATL 專案中加入對話方塊中： 使用 ATL 對話方塊精靈或以手動方式新增。

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>新增 ATL 對話方塊精靈對話方塊

在 [加入類別對話方塊](../ide/add-class-dialog-box.md)，選取 ATL 專案中加入對話方塊中的 ATL 對話方塊物件。 在 ATL 對話方塊精靈 中，適當地填入，然後按一下**完成**。 精靈會新增一個衍生自類別[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)至您的專案。 開啟**資源檢視**從**檢視** 功能表中，找出您的對話方塊，然後按兩下以在資源編輯器中開啟它。

> [!NOTE]
>  如果您的對話方塊中衍生自`CAxDialogImpl`，它可以裝載這兩個 ActiveX 和 Windows 控制項。 如果您不想 ActiveX 控制項支援的額外負荷，在您的對話方塊類別中，使用[CSimpleDialog](../atl/reference/csimpledialog-class.md)或是[CDialogImpl](../atl/reference/cdialogimpl-class.md)改。

訊息和事件處理常式可以加入您的對話方塊類別，從 類別檢視。 如需詳細資訊，請參閱 <<c0> [ 新增 ATL 訊息處理常式](../atl/adding-an-atl-message-handler.md)。

## <a name="adding-a-dialog-box-manually"></a>以手動方式加入對話方塊

實作對話方塊是類似於實作視窗。 從衍生類別[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)， [CDialogImpl](../atl/reference/cdialogimpl-class.md)，或[CSimpleDialog](../atl/reference/csimpledialog-class.md) ，並宣告[訊息對應](../atl/message-maps-atl.md)來處理訊息。 不過，您也必須在衍生類別中指定對話方塊範本資源識別碼。 您的類別必須有一個名為的資料成員`IDD`來保存此值。

> [!NOTE]
>  當您建立對話方塊，使用 ATL 對話方塊精靈時，精靈會自動新增`IDD`做為成員**列舉**型別。

`CDialogImpl` 可讓您實作強制回應或裝載 Windows 控制項的強制回應對話方塊。 `CAxDialogImpl` 可讓您實作強制回應或主控 ActiveX 和 Windows 控制項的強制回應對話方塊。

若要建立強制回應對話方塊中，建立的執行個體您`CDialogImpl`-衍生 (或`CAxDialogImpl`-衍生) 類別，然後呼叫[DoModal](../atl/reference/cdialogimpl-class.md#domodal)方法。 若要關閉強制回應對話方塊，請呼叫[EndDialog](../atl/reference/cdialogimpl-class.md#enddialog)從訊息處理常式的方法。 若要建立非強制回應對話方塊，請呼叫[Create](../atl/reference/cdialogimpl-class.md#create)方法，而非`DoModal`。 若要摧毀非強制回應對話方塊，請呼叫[DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)。

在 自動完成接收事件[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)。 實作對話方塊中的訊息處理常式，如同在處理常式`CWindowImpl`-衍生的類別。 如果沒有特定訊息的傳回值，將它傳回為`LRESULT`。 傳回`LRESULT`值會對應由 ATL，如 Windows 對話方塊管理員的正確處理。 如需詳細資訊，請參閱的原始程式碼[CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) atlwin.h 中。

## <a name="example"></a>範例

下列類別會實作的對話方塊：

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>另請參閱

[視窗類別](../atl/atl-window-classes.md)
