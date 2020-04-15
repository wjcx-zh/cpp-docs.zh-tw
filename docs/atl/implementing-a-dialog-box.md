---
title: 實交對話框
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 435926b0a0affde03580ceb2b479cb08a17d0454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319480"
---
# <a name="implementing-a-dialog-box"></a>實交對話框

有兩種方法可以將對話框添加到 ATL 專案:使用 ATL 對話方塊精靈或手動添加它。

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>使用 ATL 對話框精靈加入對話框

在[「添加類」對話框](../ide/add-class-dialog-box.md)中,選擇 ATL 對話方塊物件以向 ATL 專案添加對話方塊。 根據需要填寫 ATL 對話框精靈,然後單擊 **「完成**」。 該嚮導將派生自[CAxDialogImpl 的](../atl/reference/caxdialogimpl-class.md)類添加到專案中。 從 **"查看"功能表**打開 **"資源檢視**",找到對話框,然後按兩下該檢視以在資源編輯器中打開它。

> [!NOTE]
> 如果對話方塊派生`CAxDialogImpl`自 ,它可以同時承載 ActiveX 和 Windows 控件。 如果不希望對話方塊類中出現 ActiveX 控制項支援的開銷,請使用[CSimpleDialog](../atl/reference/csimpledialog-class.md)或[CDialogImpl。](../atl/reference/cdialogimpl-class.md)

可以從類檢視將消息和事件處理程式添加到對話方塊類中。 有關詳細資訊,請參閱新增[ATL 訊息處理程式](../atl/adding-an-atl-message-handler.md)。

## <a name="adding-a-dialog-box-manually"></a>手動新增對話框

實現對話框類似於實現視窗。 從[CAxDialogImpl、CDialogImpl](../atl/reference/caxdialogimpl-class.md)[CDialogImpl](../atl/reference/cdialogimpl-class.md)或[CSimpleDialog](../atl/reference/csimpledialog-class.md)派生一個類,並聲明[消息映射](../atl/message-maps-atl.md)來處理消息。 但是,還必須在派生類中指定對話框範本資源 ID。 類必須具有調用`IDD`的數據成員才能保存此值。

> [!NOTE]
> 使用 ATL 對話框精靈建立對話框時,向導會自動`IDD`將成員添加為**枚舉**類型。

`CDialogImpl`允許您實現承載 Windows 控制件的模式或無模式對話方塊。 `CAxDialogImpl`允許您實現承載 ActiveX 和 Windows 控制件的模式或無模式對話方塊。

要創建模態對話方塊,請`CDialogImpl`創建派生(`CAxDialogImpl`或派生)類的實例,然後調用[DoModal](../atl/reference/cdialogimpl-class.md#domodal)方法。 要關閉模式對話框,請從消息處理程式呼叫[EndDialog](../atl/reference/cdialogimpl-class.md#enddialog)方法。 要建立無模式對話框,請呼叫[Create](../atl/reference/cdialogimpl-class.md#create)`DoModal`方法而不是 。 要銷毀無模式對話框,請調用[「銷毀視窗](../atl/reference/cdialogimpl-class.md#destroywindow)」。

下沉事件在[CAxDialogImpl 中](../atl/reference/caxdialogimpl-class.md)自動完成。 實現對話框的消息處理程式,就像派生類中的處理程序一`CWindowImpl`樣。 如果有特定於消息的返回值,則將其作為返回。 `LRESULT` 返回`LRESULT`的值由 ATL 映射,以便 Windows 對話方塊管理員正確處理。 有關詳細資訊,請參閱 atlwin.h 中的[CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc)的原始程式碼。

## <a name="example"></a>範例

以下類別實現一對話框:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>另請參閱

[視窗類](../atl/atl-window-classes.md)
