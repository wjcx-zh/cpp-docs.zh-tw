---
title: COleBusyDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: aa3f0d85bcbf34d325125187b22b38c4da01fb43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504398"
---
# <a name="colebusydialog-class"></a>COleBusyDialog 類別

用於 OLE 的 [伺服器沒有回應] 或 [伺服器忙碌] 對話方塊。

## <a name="syntax"></a>語法

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|建構 `COleBusyDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleBusyDialog::DoModal](#domodal)|顯示 [OLE Server Busy] 對話方塊。|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|決定在對話方塊中所做的選擇。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|OLEUIBUSY 類型的結構，可控制對話方塊的行為。|

## <a name="remarks"></a>備註

當您想要呼叫`COleBusyDialog`這些對話方塊時，請建立類別的物件。 在結構化物件之後，您可以使用 [m_bz](#m_bz)結構，在對話方塊中初始化控制項的值或`COleBusyDialog`狀態。 `m_bz`結構的型別為 OLEUIBUSY。 如需使用此對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。

> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)結構。

如需有關 OLE 特定對話方塊的詳細資訊，請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs。h

##  <a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog

此函式只會`COleBusyDialog`構造物件。

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*htaskBusy*<br/>
忙碌中伺服器工作的控制碼。

*bNotResponding*<br/>
若為 TRUE，請呼叫 [沒有回應] 對話方塊，而不是 [伺服器忙碌] 對話方塊。 [沒有回應] 對話方塊中的用語與 [伺服器忙碌] 對話方塊中的用語略有不同，而且 [取消] 按鈕已停用。

*dwFlags*<br/>
建立旗標。 可以包含零或多個與位 OR 運算子結合的下列值：

- BZ_DISABLECANCELBUTTON 在呼叫對話方塊時停用 [取消] 按鈕。

- 呼叫對話方塊時，BZ_DISABLESWITCHTOBUTTON 停用切換至按鈕。

- BZ_DISABLERETRYBUTTON 在呼叫對話方塊時停用 [重試] 按鈕。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或擁有者視窗物件`CWnd`（類型為）。 如果它是 Null，則對話方塊物件的父視窗會設定為主應用程式視窗。

### <a name="remarks"></a>備註

若要顯示對話方塊，請呼叫[DoModal](#domodal)。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)結構。

##  <a name="domodal"></a>  COleBusyDialog::DoModal

呼叫此函式以顯示 [OLE Server 忙碌或伺服器沒有回應] 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊的完成狀態。 下列其中一個值：

- 如果已成功顯示對話方塊，則 IDOK。

- 如果使用者取消對話方塊，則 IDCANCEL。

- 如果發生錯誤，則 IDABORT。 如果傳回 IDABORT，請呼叫`COleDialog::GetLastError`成員函式，以取得所發生錯誤類型的詳細資訊。 如需可能錯誤的清單，請參閱 Windows SDK 中的[OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw)函數。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_bz](#m_bz)結構的成員來初始化各種對話方塊控制項，您應該在呼叫`DoModal`之前執行此動作，但在構造對話方塊物件之後。

如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式，以抓取使用者在對話方塊中輸入的設定或資訊。

##  <a name="getselectiontype"></a>COleBusyDialog::GetSelectionType

呼叫此函式可在 [伺服器忙碌] 對話方塊中，取得使用者所選擇的選擇類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

所選取的類型。

### <a name="remarks"></a>備註

傳回型別值是由`Selection` `COleBusyDialog`類別中宣告的列舉型別所指定。

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

這些值的簡短說明如下：

- `COleBusyDialog::switchTo`已按下 [切換至] 按鈕。

- `COleBusyDialog::retry`按下 [重試] 按鈕。

- `COleBusyDialog::callUnblocked`啟動伺服器的呼叫現在已解除封鎖。

##  <a name="m_bz"></a>  COleBusyDialog::m_bz

OLEUIBUSY 類型的結構，用來控制 [伺服器忙碌] 對話方塊的行為。

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>備註

這個結構的成員可以直接修改，或透過成員函式來修改。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
