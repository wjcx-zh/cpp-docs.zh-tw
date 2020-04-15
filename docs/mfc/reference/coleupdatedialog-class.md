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
ms.openlocfilehash: 9e2c7a8d79ebf5e6483a06354b280e474d7b8e61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374842"
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
|[COle 更新對話::COle 更新對話](#coleupdatedialog)|建構 `COleUpdateDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle更新對話::Do模態](#domodal)|在更新模式下顯示 **「編輯連結」** 對話框。|

## <a name="remarks"></a>備註

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a>COle 更新對話::COle 更新對話

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
指向包含可能需要更新的連結的文檔。

*b更新連結*<br/>
確定連結物件是否要更新的標誌。

*b 更新嵌入*<br/>
確定是否要更新嵌入物件的標誌。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件`CWnd`(類型)。 如果為 NULL,則對話方塊的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

此函數只建構物件`COleUpdateDialog`。 要顯示對話框,請呼叫[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 應使用此類,而不是`COleLinksDialog`僅更新現有連結或嵌入專案。

## <a name="coleupdatedialogdomodal"></a><a name="domodal"></a>COle更新對話::Do模態

在更新模式下顯示"編輯連結"對話框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話框的完成狀態。 下列其中一個值：

- 如果對話框成功返回,則 IDOK。

- 如果當前文檔中的連結或嵌入專案不需要更新,則 IDCANCEL。

- 如果發生錯誤,則 IDABORT。 如果返回 IDABORT,請呼叫[COleDialog:getLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函數,以獲取有關所發生錯誤類型的詳細資訊。 有關可能錯誤的清單,請參閱 Windows SDK 中的[OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw)函數。

### <a name="remarks"></a>備註

除非用戶選擇"取消"按鈕,否則所有連結和/或嵌入都將更新。

## <a name="see-also"></a>另請參閱

[MFC 樣品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)
