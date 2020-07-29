---
title: 執行對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 7866afd26c901181f2b4193a87daf5dca2b0c67f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226681"
---
# <a name="implementing-a-dialog-box"></a>執行對話方塊

有兩種方式可以將對話方塊新增至 ATL 專案：使用 ATL 對話方塊 Wizard 或手動新增。

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>使用 ATL 對話方塊嚮導加入對話方塊

在 [[加入類別] 對話方塊](../ide/add-class-dialog-box.md)中，選取 [Atl] 對話方塊物件，將對話方塊新增至 atl 專案。 視需要填入 [ATL 對話方塊嚮導]，然後按一下 **[完成]**。 此嚮導會將衍生自[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)的類別新增至您的專案。 從 [ **View** ] 功能表開啟**資源檢視**，找到您的對話方塊，然後按兩下以在資源編輯器中開啟它。

> [!NOTE]
> 如果您的對話方塊衍生自 `CAxDialogImpl` ，它可以同時裝載 ActiveX 和 Windows 控制項。 如果您不想要在對話方塊類別中使用 ActiveX 控制項支援的額外負荷，請改用[CSimpleDialog](../atl/reference/csimpledialog-class.md)或[CDialogImpl](../atl/reference/cdialogimpl-class.md) 。

訊息和事件處理常式可以從類別檢視新增至您的對話方塊類別。 如需詳細資訊，請參閱[新增 ATL 訊息處理常式](../atl/adding-an-atl-message-handler.md)。

## <a name="adding-a-dialog-box-manually"></a>手動新增對話方塊

執行對話方塊類似于執行視窗。 您可以從[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)、 [CDialogImpl](../atl/reference/cdialogimpl-class.md)或[CSimpleDialog](../atl/reference/csimpledialog-class.md)衍生一個類別，並宣告[訊息對應](../atl/message-maps-atl.md)來處理訊息。 不過，您也必須在衍生類別中指定對話方塊範本資源識別碼。 您的類別必須有一個稱為的資料成員 `IDD` ，才能保存此值。

> [!NOTE]
> 當您使用 ATL 對話方塊嚮導建立對話方塊時，嚮導會自動將該成員加入 `IDD` 為 **`enum`** 類型。

`CDialogImpl`可讓您執行模式或非強制回應對話方塊，以裝載 Windows 控制項。 `CAxDialogImpl`可讓您執行同時裝載 ActiveX 和 Windows 控制項的模式或非強制回應對話方塊。

若要建立強制回應對話方塊，請建立 `CDialogImpl` 衍生（或 `CAxDialogImpl` 衍生）類別的實例，然後呼叫[DoModal](../atl/reference/cdialogimpl-class.md#domodal)方法。 若要關閉強制回應對話方塊，請從訊息處理常式呼叫[EndDialog](../atl/reference/cdialogimpl-class.md#enddialog)方法。 若要建立非強制回應對話方塊，請呼叫[create](../atl/reference/cdialogimpl-class.md#create)方法，而不是 `DoModal` 。 若要終結非強制回應對話方塊，請呼叫[DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)。

接收事件會自動在[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)中完成。 如同衍生類別中的處理常式一樣，執行對話方塊的訊息處理常式 `CWindowImpl` 。 如果有訊息特定的傳回值，則傳回做為 `LRESULT` 。 傳回的 `LRESULT` 值會由 ATL 對應，以便由 Windows 對話方塊管理員進行適當的處理。 如需詳細資訊，請參閱[CDialogImplBaseT：:D ialogproc](../atl/reference/cdialogimpl-class.md#dialogproc) in atlwin.h 的原始程式碼。

## <a name="example"></a>範例

下列類別會實作為一個對話方塊：

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>另請參閱

[視窗類別](../atl/atl-window-classes.md)
