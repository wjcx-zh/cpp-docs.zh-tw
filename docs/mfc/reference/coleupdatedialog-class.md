---
title: COleUpdateDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: 74607a2a145025533c660ae68f20ffb8e59d3fad
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281729"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog 類別

用於 OLE [編輯連結] 對話方塊的特殊狀況，當您只需要更新文件中現有的連結或內嵌物件時，應該使用此項。

## <a name="syntax"></a>語法

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|建構 `COleUpdateDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|顯示**編輯連結**處於更新模式的對話方塊。|

## <a name="remarks"></a>備註

如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[對話方塊，在 OLE 中](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs.h

##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog

建構 `COleUpdateDialog` 物件。

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
指向包含的連結，可能需要更新的文件。

*bUpdateLinks*<br/>
連結的物件會決定要更新的旗標。

*bUpdateEmbeddings*<br/>
內嵌的物件會決定要更新的旗標。

*pParentWnd*<br/>
指向的父系或擁有者的視窗物件 (類型的`CWnd`) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊中的父視窗將回到主應用程式視窗。

### <a name="remarks"></a>備註

此函式會建構只`COleUpdateDialog`物件。 若要顯示的對話方塊，請呼叫[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 應該使用這個類別，而不是`COleLinksDialog`當您想要更新只有現有連結或內嵌項目。

##  <a name="domodal"></a>  COleUpdateDialog::DoModal

[編輯連結] 對話方塊會顯示更新模式。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊中的完成狀態。 下列其中一個值：

- IDOK 如果對話方塊傳回成功。

- 如果目前的文件中連結或內嵌項目都不需要更新，IDCANCEL。

- IDABORT 發生錯誤。 如果傳回 IDABORT，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱 < [OleUIEditLinks](/windows/desktop/api/oledlg/nf-oledlg-oleuieditlinksa) Windows SDK 中的函式。

### <a name="remarks"></a>備註

除非使用者選取 [取消] 按鈕，會更新所有的連結和/或內嵌項目。

## <a name="see-also"></a>另請參閱

[MFC 範例 OCLIENT](../../visual-cpp-samples.md)<br/>
[COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)
