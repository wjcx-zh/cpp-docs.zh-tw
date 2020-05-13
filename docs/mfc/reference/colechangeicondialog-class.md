---
title: COleChangeIconDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 6cdc0ed6bfa4765817de8b7628f339db5e7e5bf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369628"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog 類別

用於 OLE 的 [變更圖示] 對話方塊。

## <a name="syntax"></a>語法

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleChangeIcon對話::COleChangeIcon對話](#colechangeicondialog)|建構 `COleChangeIconDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleChangeIcon對話::DoChangeIcon](#dochangeicon)|執行對話框中指定的更改。|
|[COleChangeIcon對話::D模態](#domodal)|顯示 OLE 2 更改圖示對話方塊。|
|[COleChangeIcon對話::取得圖示Meta檔案](#geticonicmetafile)|獲取與此項目的標誌性形式關聯的元檔的句柄。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleChangeIcon對話::m_ci](#m_ci)|控制對話框行為的結構。|

## <a name="remarks"></a>備註

要呼叫此對話方塊`COleChangeIconDialog`時 ,請創建類的物件。 建構`COleChangeIconDialog`物件后,可以使用[m_ci](#m_ci)結構在對話框中初始化控制件的值或狀態。 結構`m_ci`為奧萊維圖森。 有關使用此對話方塊類的詳細資訊,請參閱[DoModal](#domodal)成員函數。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)結構。

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a>COleChangeIcon對話::COleChangeIcon對話

此函數只建構物件`COleChangeIconDialog`。

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要轉換的專案。

*dwFlags*<br/>
建立標誌,其中包含使用位或運算子組合的以下任意數量的值:

- CIF_SELECTCURRENT 指定在調用對話方塊時最初將選擇「當前單選」按鈕。 這是預設值。

- CIF_SELECTDEFAULT指定在調用對話方塊時,最初將選擇默認單選按鈕。

- CIF_SELECTFROMFILE 指定在調用對話方塊時,最初將選擇「從檔單選」按鈕。

- CIF_SHOWHELP 指定在調用對話框時將顯示"説明"按鈕。

- CIF_USEICONEXE 指定應`szIconExe`從[m_ci](#m_ci)欄位中指定的可執行檔中提取圖示,而不是從類型中檢索。 這對於嵌入或連結到非 OLE 檔非常有用。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件`CWnd`(類型)。 如果為 NULL,則對話方塊的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

要顯示對話框,請調用[DoModal](#domodal)函數。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)結構。

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a>COleChangeIcon對話::DoChangeIcon

調用此函數以將表示項的圖示更改為[DoModal](#domodal)返回 IDOK 後對話方塊中選擇的圖示。

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向其圖示正在更改的專案。

### <a name="return-value"></a>傳回值

如果更改成功,則非零;否則 0。

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a>COleChangeIcon對話::D模態

呼叫此函數以顯示"OLE 更改圖示"對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話框的完成狀態。 下列其中一個值：

- 如果對話框已成功顯示,則 IDOK。

- 如果使用者取消了對話框,則進行 IDCANCEL。

- 如果發生錯誤,則 IDABORT。 如果返回 IDABORT,請調`COleDialog::GetLastError`用 成員函數以獲取有關所發生錯誤類型的詳細資訊。 有關可能錯誤的清單,請參閱 Windows SDK 中的[OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw)函數。

### <a name="remarks"></a>備註

如果要通過設置[m_ci](#m_ci)結構的成員來初始化各種對話框控件,則應在`DoModal`調用 之前執行此操作,但在構造對話框物件之後。

如果`DoModal`返回 IDOK,則可以調用其他成員函數來檢索使用者輸入到對話方塊中的設置或資訊。

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleChangeIcon對話::取得圖示Meta檔案

呼叫此函數以獲取包含所選項標誌性方面的元檔的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含新圖示標誌性方面的元檔的句柄,如果對話方塊通過選擇 **「確定」** 而取消;否則,圖示與顯示對話方塊之前的圖示相同。

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a>COleChangeIcon對話::m_ci

用於控制更改圖示對話方塊的行為的 OLEUICHANGEICON 類型的結構。

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>備註

此結構的成員可以直接或通過成員函數進行修改。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
