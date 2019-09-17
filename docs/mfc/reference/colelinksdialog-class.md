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
ms.openlocfilehash: 911108f9a231b752790abfdf86d1b4042d30b149
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504113"
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
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|建構 `COleLinksDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleLinksDialog::DoModal](#domodal)|顯示 [OLE 編輯連結] 對話方塊。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|OLEUIEDITLINKS 類型的結構，可控制對話方塊的行為。|

## <a name="remarks"></a>備註

當您想要呼叫`COleLinksDialog`此對話方塊時，請建立類別的物件。 在結構化物件之後，您可以使用 [m_el](#m_el) 結構，在對話方塊中初始化控制項的值或`COleLinksDialog`狀態。 `m_el`結構的型別為 OLEUIEDITLINKS。 如需使用此對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。

> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw)結構。

如需有關 OLE 特定對話方塊的詳細資訊，請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs。h

##  <a name="domodal"></a>COleLinksDialog：:D oModal

顯示 [OLE 編輯連結] 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊的完成狀態。 下列其中一個值：

- 如果已成功顯示對話方塊，則 IDOK。

- 如果使用者取消對話方塊，則 IDCANCEL。

- 如果發生錯誤，則 IDABORT。 如果傳回 IDABORT，請呼叫`COleDialog::GetLastError`成員函式，以取得所發生錯誤類型的詳細資訊。 如需可能錯誤的清單，請參閱 Windows SDK 中的[OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw)函數。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_el](#m_el)結構的成員來初始化各種對話方塊控制項，您應該在呼叫`DoModal`之前先這麼做，但在構造對話方塊物件之後。

##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

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
指向包含要編輯之連結的 OLE 檔。

*pView*<br/>
指向*pDoc*上的目前視圖。

*dwFlags*<br/>
建立旗標，其中包含0或 ELF_SHOWHELP，以指定顯示對話方塊時是否要顯示 [說明] 按鈕。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或擁有者視窗物件`CWnd`（類型為）。 如果它是 Null，則對話方塊的父視窗會設定為主應用程式視窗。

### <a name="remarks"></a>備註

此函式只會`COleLinksDialog`對物件進行結構。 若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。

##  <a name="m_el"></a>COleLinksDialog::m_el

OLEUIEDITLINKS 類型的結構，用來控制 [編輯連結] 對話方塊的行為。

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>備註

這個結構的成員可以直接或透過成員函式來修改。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
