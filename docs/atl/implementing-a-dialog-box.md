---
title: 執行對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: fa7b4122b513d48194dedeb39daecd1dfd7223eb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499572"
---
# <a name="implementing-a-dialog-box"></a>執行對話方塊

有兩種方式可將對話方塊新增至 ATL 專案：使用 ATL 對話方塊 Wizard 或手動加入。

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>使用 ATL 對話方塊 Wizard 新增對話方塊

在 [ [加入類別] 對話方塊](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)中，選取 [Atl] 對話方塊物件以將對話方塊新增至 atl 專案。 適當地填寫 ATL 對話方塊嚮導，然後按一下 **[完成]**。 Wizard 將衍生自 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) 的類別加入至您的專案。 從 [ **View** ] 功能表開啟**資源檢視**，找出您的對話方塊，然後按兩下以在資源編輯器中開啟它。

> [!NOTE]
> 如果您的對話方塊衍生自 `CAxDialogImpl` ，它可以裝載 ActiveX 和 Windows 控制項。 如果您不想要在您的對話方塊類別中使用 ActiveX 控制項支援的額外負荷，請改用 [CSimpleDialog](../atl/reference/csimpledialog-class.md) 或 [CDialogImpl](../atl/reference/cdialogimpl-class.md) 。

訊息和事件處理常式可以從類別檢視新增至您的對話方塊類別。 如需詳細資訊，請參閱 [加入 ATL 訊息處理常式](../atl/adding-an-atl-message-handler.md)。

## <a name="adding-a-dialog-box-manually"></a>手動新增對話方塊

執行對話方塊類似于執行視窗。 您可以從 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)、 [CDialogImpl](../atl/reference/cdialogimpl-class.md)或 [CSimpleDialog](../atl/reference/csimpledialog-class.md) 衍生類別，並宣告 [訊息對應](../atl/message-maps-atl.md) 來處理訊息。 不過，您也必須在衍生類別中指定對話方塊範本資源識別碼。 您的類別必須有一個稱為的資料成員 `IDD` ，才能保存此值。

> [!NOTE]
> 當您使用 ATL 對話方塊 Wizard 建立對話方塊時，Wizard 會自動將 `IDD` 成員加入為 **`enum`** 型別。

`CDialogImpl` 可讓您執行裝載 Windows 控制項的強制回應或非強制回應對話方塊。 `CAxDialogImpl` 可讓您執行裝載 ActiveX 和 Windows 控制項的強制回應或非強制回應對話方塊。

若要建立強制回應對話方塊，請建立 `CDialogImpl` 衍生 (或衍生) 類別的實例，然後 `CAxDialogImpl` 呼叫 [DoModal](../atl/reference/cdialogimpl-class.md#domodal) 方法。 若要關閉強制回應對話方塊，請從訊息處理常式呼叫 [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) 方法。 若要建立非強制回應對話方塊，請呼叫 [create](../atl/reference/cdialogimpl-class.md#create) 方法，而不是 `DoModal` 。 若要摧毀非強制回應對話方塊，請呼叫 [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)。

接收事件會在 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)中自動完成。 如同衍生類別中的處理常式一樣，執行對話方塊的訊息處理常式 `CWindowImpl` 。 如果有訊息特定的傳回值，請將其傳回做為 `LRESULT` 。 傳回的 `LRESULT` 值會由 ATL 對應，以供 Windows 對話管理員進行適當的處理。 如需詳細資訊，請參閱 atlwin 中的 CDialogImplBaseT 的原始程式碼 [：:D ialogproc](../atl/reference/cdialogimpl-class.md#dialogproc) 。

## <a name="example"></a>範例

下列類別會執行對話方塊：

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>另請參閱

[視窗類別](../atl/atl-window-classes.md)
