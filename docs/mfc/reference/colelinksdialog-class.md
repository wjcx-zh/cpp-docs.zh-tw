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
ms.openlocfilehash: fa32236dfdaef0966dca0e2f131e6adace747f10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502956"
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
|[COleLinksDialog::DoModal](#domodal)|會顯示 OLE [編輯連結] 對話方塊。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|類型的對話方塊行為的 OLEUIEDITLINKS 的結構。|

## <a name="remarks"></a>備註

建立類別的物件`COleLinksDialog`當您想要呼叫此對話方塊。 在後`COleLinksDialog`在建構物件，您可以使用[m_el](#m_el)結構初始化的值或在對話方塊中控制項的狀態。 `m_el`結構屬於 OLEUIEDITLINKS 的型別。 如需使用這個對話方塊類別的詳細資訊，請參閱 < [DoModal](#domodal)成員函式。

> [!NOTE]
>  應用程式精靈所產生的容器程式碼會使用這個類別。

如需詳細資訊，請參閱 < [OLEUIEDITLINKS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuieditlinksa) Windows SDK 中的結構。

如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[對話方塊，在 OLE 中](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs.h

##  <a name="domodal"></a>  COleLinksDialog::DoModal

會顯示 OLE [編輯連結] 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊中的完成狀態。 下列其中一個值：

- 如果對話方塊已成功顯示，IDOK。

- 如果使用者已取消對話方塊，IDCANCEL。

- IDABORT 發生錯誤。 如果傳回 IDABORT，呼叫`COleDialog::GetLastError`成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱 < [OleUIEditLinks](/windows/desktop/api/oledlg/nf-oledlg-oleuieditlinksa) Windows SDK 中的函式。

### <a name="remarks"></a>備註

如果您想要設定的成員初始化各種不同的對話方塊控制項[m_el](#m_el)結構，這樣才能呼叫`DoModal`，但在建構對話方塊物件之後。

##  <a name="colelinksdialog"></a>  COleLinksDialog::COleLinksDialog

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
指向包含要編輯連結的 OLE 文件。

*pView*<br/>
指向目前的檢視上*pDoc*。

*dwFlags*<br/>
建立旗標，其中包含 0 或 ELF_SHOWHELP 來指定當顯示對話方塊時，是否會顯示 [說明] 按鈕。

*pParentWnd*<br/>
指向的父系或擁有者的視窗物件 (類型的`CWnd`) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊中的父視窗設為主要的應用程式視窗。

### <a name="remarks"></a>備註

此函式會建構只`COleLinksDialog`物件。 若要顯示的對話方塊，請呼叫[DoModal](#domodal)函式。

##  <a name="m_el"></a>  COleLinksDialog::m_el

型別的 OLEUIEDITLINKS 結構用來控制行為的編輯連結 對話方塊。

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>備註

直接或透過成員函式，則可以修改此結構的成員。

如需詳細資訊，請參閱 < [OLEUIEDITLINKS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuieditlinksa) Windows SDK 中的結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
