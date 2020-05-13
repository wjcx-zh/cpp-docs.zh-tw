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
ms.openlocfilehash: 5be42463c08cacd83de84900fb4d98771774e897
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364247"
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
|[COleBusy對話::COleBusy對話](#colebusydialog)|建構 `COleBusyDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleBusyDialog::Do模態](#domodal)|顯示"OLE 伺服器忙"對話框。|
|[COleBusy 對話:取得選擇類型](#getselectiontype)|確定在對話框中所做的選擇。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleBusy對話::m_bz](#m_bz)|控制對話框行為的 OLEUIBUSY 類型的結構。|

## <a name="remarks"></a>備註

如果要調用這些對話框,`COleBusyDialog`請建立類的物件。 建構`COleBusyDialog`物件后,可以使用[m_bz](#m_bz)結構在對話框中初始化控制件的值或狀態。 結構`m_bz`為奧萊布布。 有關使用此對話方塊類的詳細資訊,請參閱[DoModal](#domodal)成員函數。

> [!NOTE]
> 應用程式精靈生成的容器代碼使用此類。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)結構。

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a>COleBusy對話::COleBusy對話

此函數只建構物件`COleBusyDialog`。

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*htaskBusy*<br/>
處理忙的伺服器任務。

*b 不回應*<br/>
如果為 TRUE,則調用"不回應"對話框,而不是"伺服器忙"對話方塊。 "不回應"對話框中的措辭與"伺服器忙"對話框中的措詞略有不同,並且禁用"取消"按鈕。

*dwFlags*<br/>
創建標誌。 可以包含與位-OR 運算子結合的以下零個或多個值:

- BZ_DISABLECANCELBUTTON調用對話方塊時禁用"取消"按鈕。

- BZ_DISABLESWITCHTOBUTTON在調用對話方塊時禁用「切換到」按鈕。

- BZ_DISABLERETRYBUTTON調用對話方塊時禁用重試按鈕。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件`CWnd`(類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

要顯示對話框,請呼叫[DoModal](#domodal)。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)結構。

## <a name="colebusydialogdomodal"></a><a name="domodal"></a>COleBusyDialog::Do模態

呼叫此函數以顯示"OLE 伺服器忙"或"伺服器未回應"對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話框的完成狀態。 下列其中一個值：

- 如果對話框已成功顯示,則 IDOK。

- 如果使用者取消了對話框,則進行 IDCANCEL。

- 如果發生錯誤,則 IDABORT。 如果返回 IDABORT,請調`COleDialog::GetLastError`用 成員函數以獲取有關所發生錯誤類型的詳細資訊。 有關可能錯誤的清單,請參閱 Windows SDK 中的[OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw)函數。

### <a name="remarks"></a>備註

如果要通過設置[m_bz](#m_bz)結構的成員來初始化各種對話框控件,則應在`DoModal`調用 之前執行此操作,但在構造對話框物件之後。

如果`DoModal`返回 IDOK,則可以調用其他成員函數來檢索使用者輸入到對話方塊中的設置或資訊。

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a>COleBusy 對話:取得選擇類型

呼叫此函數以獲取使用者在「伺服器忙」對話框中選擇的選擇類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

選擇的類型。

### <a name="remarks"></a>備註

返回類型值由類中聲明的`Selection``COleBusyDialog`枚舉類型指定。

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

這些值的簡要說明如下:

- `COleBusyDialog::switchTo`按下「切換到」按鈕。

- `COleBusyDialog::retry`按下重試按鈕。

- `COleBusyDialog::callUnblocked`現在,啟動伺服器的呼叫已解除阻止。

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a>COleBusy對話::m_bz

用於控制伺服器忙對話方塊的行為的 OLEUIBUSY 類型的結構。

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>備註

此結構的成員可以直接或通過成員函數進行修改。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
