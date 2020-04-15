---
title: COleLinksDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
ms.openlocfilehash: f120678c822749c8f27c3c56c95fcdd54647aca3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374925"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog 類別

用於 OLE 的 [編輯連結] 對話方塊。

## <a name="syntax"></a>語法

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleLinks對話::COleLinks對話](#colelinksdialog)|建構 `COleLinksDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleLinks對話::Do模態](#domodal)|顯示"OLE 編輯連結"對話方塊。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleLinks對話::m_el](#m_el)|控制對話框行為的"OLEUIEDITLINKS"類型的結構。|

## <a name="remarks"></a>備註

要呼叫此對話方塊`COleLinksDialog`時 ,請創建類的物件。 建構`COleLinksDialog`物件后,可以使用[m_el](#m_el)結構在對話框中初始化控制件的值或狀態。 結構`m_el`為奧萊伊迪克斯型。 有關使用此對話方塊類的詳細資訊,請參閱[DoModal](#domodal)成員函數。

> [!NOTE]
> 應用程式精靈生成的容器代碼使用此類。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIEDITLINKS 結構](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw)。

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="colelinksdialogdomodal"></a><a name="domodal"></a>COleLinks對話::Do模態

顯示"OLE 編輯連結"對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話框的完成狀態。 下列其中一個值：

- 如果對話框已成功顯示,則 IDOK。

- 如果使用者取消了對話框,則進行 IDCANCEL。

- 如果發生錯誤,則 IDABORT。 如果返回 IDABORT,請調`COleDialog::GetLastError`用 成員函數以獲取有關所發生錯誤類型的詳細資訊。 有關可能錯誤的清單,請參閱 Windows SDK 中的[OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw)函數。

### <a name="remarks"></a>備註

如果要通過設置[m_el](#m_el)結構的成員來初始化各種對話框控件,則應在`DoModal`調用 之前執行此操作,但在構造對話框物件之後。

## <a name="colelinksdialogcolelinksdialog"></a><a name="colelinksdialog"></a>COleLinks對話::COleLinks對話

建構 `COleLinksDialog` 物件。

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pDoc*<br/>
指向包含要編輯的連結的 OLE 文件。

*pView*<br/>
指向*pDoc*上的當前檢視。

*dwFlags*<br/>
創建標誌,其中包含 0 或ELF_SHOWHELP,用於指定在顯示對話方塊時是否顯示「説明」按鈕。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件`CWnd`(類型)。 如果為 NULL,則對話方塊的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

此函數只建構物件`COleLinksDialog`。 要顯示對話框,請調用[DoModal](#domodal)函數。

## <a name="colelinksdialogm_el"></a><a name="m_el"></a>COleLinks對話::m_el

用於控制「編輯連結」對話框的行為的 OLEUIEDITLINKS 類型的結構。

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>備註

此結構的成員可以直接或通過成員函數進行修改。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIEDITLINKS 結構](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw)。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
