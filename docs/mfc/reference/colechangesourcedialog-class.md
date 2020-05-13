---
title: COleChangeSourceDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 78da0a495de6ea951deab984550756a2d6f3e2bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321864"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog 類別

用於 OLE 的 [變更來源] 對話方塊。

## <a name="syntax"></a>語法

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleChange來源對話::COleChange來源對話](#colechangesourcedialog)|建構 `COleChangeSourceDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleChange來源對話::Do模態](#domodal)|顯示"OLE 更改源"對話框。|
|[COleChange 來源對話::取得顯示名稱](#getdisplayname)|獲取完整的源顯示名稱。|
|[COleChange來源對話::取得檔案名](#getfilename)|從源名稱獲取檔名。|
|[COleChange來源對話::從首串取得](#getfromprefix)|獲取前一源的首碼。|
|[COleChange 來源對話::取得項目名稱](#getitemname)|從源名稱獲取項名稱。|
|[COleChange來源對話::取得前置字串](#gettoprefix)|取得新來源的前置字串|
|[COleChange來源::有效來源](#isvalidsource)|指示源是否有效。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleChange來源::m_cs](#m_cs)|控制對話框行為的結構。|

## <a name="remarks"></a>備註

要呼叫此對話方塊`COleChangeSourceDialog`時 ,請創建類的物件。 建構`COleChangeSourceDialog`物件后,可以使用[m_cs](#m_cs)結構在對話框中初始化控制件的值或狀態。 結構`m_cs`為[奧萊圖元。](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) 有關使用此對話方塊類的詳細資訊,請參閱[DoModal](#domodal)成員函數。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a>COleChange來源對話::COleChange來源對話

此函式建構物件`COleChangeSourceDialog`。

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要更新其源的連結[的 COleClientItem](../../mfc/reference/coleclientitem-class.md)的指標。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件`CWnd`(類型)。 如果為 NULL,則對話方塊的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

要顯示對話框,請調用[DoModal](#domodal)函數。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構和[OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew)函數。

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a>COleChange來源對話::Do模態

呼叫此函數以顯示 OLE 更改源對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話框的完成狀態。 下列其中一個值：

- 如果對話框已成功顯示,則 IDOK。

- 如果使用者取消了對話框,則進行 IDCANCEL。

- 如果發生錯誤,則 IDABORT。 如果返回 IDABORT,請呼叫[COleDialog:getLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函數,以獲取有關所發生錯誤類型的詳細資訊。 有關可能錯誤的清單,請參閱 Windows SDK 中的[OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew)函數。

### <a name="remarks"></a>備註

如果要通過設置[m_cs](#m_cs)結構的成員來初始化各種對話框控件,則應在調用`DoModal`之前執行此操作,但在構造對話框物件之後。

如果`DoModal`返回 IDOK,則可以調用成員函數從對話框中檢索使用者輸入的設置或資訊。 以下清單名稱典型的查詢函數:

- [GetFileName](#getfilename)

- [取得顯示名稱](#getdisplayname)

- [取得項目名稱](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a>COleChange 來源對話::取得顯示名稱

呼叫此函數以檢索連結的用戶端項的完整顯示名稱。

```
CString GetDisplayName();
```

### <a name="return-value"></a>傳回值

建構函數中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的完整源顯示名稱(名字)。

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a>COleChange來源對話::取得檔案名

呼叫此函數以檢索連結客戶端項的顯示名稱的檔名稱部分。

```
CString GetFileName();
```

### <a name="return-value"></a>傳回值

在建構函數中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的來源顯示名稱的檔案名稱部分。

### <a name="remarks"></a>備註

檔名稱與專案名稱一起提供完整的顯示名稱。

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a>COleChange來源對話::從首串取得

呼叫此函數以獲取源的前置字串。

```
CString GetFromPrefix();
```

### <a name="return-value"></a>傳回值

源的前置字串。

### <a name="remarks"></a>備註

僅在[DoModal](#domodal)傳回 IDOK 後呼叫此函數。

此值直接來自`lpszFrom`[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構的成員。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a>COleChange 來源對話::取得項目名稱

呼叫此函數以檢索連結客戶端項的顯示名稱的項名稱部分。

```
CString GetItemName();
```

### <a name="return-value"></a>傳回值

在建構函數中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的來源顯示名稱的項目名稱部分。

### <a name="remarks"></a>備註

檔名稱與專案名稱一起提供完整的顯示名稱。

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a>COleChange來源對話::取得前置字串

呼叫此函數獲取源的新前置字串。

```
CString GetToPrefix();
```

### <a name="return-value"></a>傳回值

源的新首碼字串。

### <a name="remarks"></a>備註

僅在[DoModal](#domodal)傳回 IDOK 後呼叫此函數。

此值直接來自`lpszTo`[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構的成員。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a>COleChange來源::m_cs

此數據成員是[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)類型的結構。

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>備註

`OLEUICHANGESOURCE`用於控制 OLE 更改源對話方塊的行為。 可以直接修改此結構的成員。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a>COleChange來源::有效來源

調用此函數以確定新源是否有效。

```
BOOL IsValidSource();
```

### <a name="return-value"></a>傳回值

如果新源有效,則非零,否則為 0。

### <a name="remarks"></a>備註

僅在[DoModal](#domodal)傳回 IDOK 後呼叫此函數。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
