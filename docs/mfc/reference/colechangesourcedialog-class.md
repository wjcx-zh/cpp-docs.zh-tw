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
ms.openlocfilehash: 239d7eed89796f414a7665b203ca50fafec51277
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504391"
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
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|建構 `COleChangeSourceDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|顯示 [OLE 變更來源] 對話方塊。|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|取得完整的來源顯示名稱。|
|[COleChangeSourceDialog::GetFileName](#getfilename)|從來源名稱取得檔案名。|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|取得上一個來源的前置詞。|
|[COleChangeSourceDialog::GetItemName](#getitemname)|從來源名稱取得專案名稱。|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|取得新來源的前置詞|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|指出來源是否有效。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|結構，控制對話方塊的行為。|

## <a name="remarks"></a>備註

當您想要呼叫`COleChangeSourceDialog`此對話方塊時，請建立類別的物件。 在結構化物件之後，您可以使用 [m_cs](#m_cs) 結構，在對話方塊中初始化控制項的值或`COleChangeSourceDialog`狀態。 結構的型別為[OLEUICHANGESOURCE。](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) `m_cs` 如需使用此對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

如需有關 OLE 特定對話方塊的詳細資訊，請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs。h

##  <a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

此函式會`COleChangeSourceDialog`建立物件。

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pItem*<br/>
連結的[COleClientItem](../../mfc/reference/coleclientitem-class.md)的指標，其來源會更新。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或擁有者視窗物件`CWnd`（類型為）。 如果它是 Null，則對話方塊的父視窗將會設定為主應用程式視窗。

### <a name="remarks"></a>備註

若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構和[OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew)函數。

##  <a name="domodal"></a>COleChangeSourceDialog：:D oModal

呼叫此函式以顯示 [OLE 變更來源] 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊的完成狀態。 下列其中一個值：

- 如果已成功顯示對話方塊，則 IDOK。

- 如果使用者取消對話方塊，則 IDCANCEL。

- 如果發生錯誤，則 IDABORT。 如果傳回 IDABORT，請呼叫[COleDialog：： GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式，以取得所發生錯誤類型的詳細資訊。 如需可能錯誤的清單，請參閱 Windows SDK 中的[OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew)函數。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_cs](#m_cs)結構的成員來初始化各種對話方塊控制項，您應該在呼叫`DoModal`之前執行此動作，但在構造對話方塊物件之後。

如果`DoModal`傳回 IDOK，您可以呼叫成員函式，從對話方塊中取出使用者輸入的設定或資訊。 下列清單會命名一般查詢函數：

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

##  <a name="getdisplayname"></a>COleChangeSourceDialog：： GetDisplayName

呼叫此函式可取得連結用戶端專案的完整顯示名稱。

```
CString GetDisplayName();
```

### <a name="return-value"></a>傳回值

在此函數中指定之[COleClientItem](../../mfc/reference/coleclientitem-class.md)的完整來源顯示名稱（名字標記）。

##  <a name="getfilename"></a>COleChangeSourceDialog：： GetFileName

呼叫此函式可抓取連結用戶端專案之顯示名稱的檔案標記部分。

```
CString GetFileName();
```

### <a name="return-value"></a>傳回值

在此函數中指定之[COleClientItem](../../mfc/reference/coleclientitem-class.md)的來源顯示名稱的檔案標記部分。

### <a name="remarks"></a>備註

檔案標記和專案的名字標記會提供完整的顯示名稱。

##  <a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

呼叫此函式可取得來源的先前前置詞字串。

```
CString GetFromPrefix();
```

### <a name="return-value"></a>傳回值

來源的先前前置詞字串。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 之後，才呼叫此函式。

這個值直接來自[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構`lpszFrom`的成員。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

##  <a name="getitemname"></a>COleChangeSourceDialog::GetItemName

呼叫此函式可抓取連結用戶端專案之顯示名稱的專案標記部分。

```
CString GetItemName();
```

### <a name="return-value"></a>傳回值

在此函式中指定的[COleClientItem](../../mfc/reference/coleclientitem-class.md)之來源顯示名稱的專案標記部分。

### <a name="remarks"></a>備註

檔案標記和專案的名字標記會提供完整的顯示名稱。

##  <a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

呼叫此函式可取得來源的新前置詞字串。

```
CString GetToPrefix();
```

### <a name="return-value"></a>傳回值

來源的新前置詞字串。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 之後，才呼叫此函式。

這個值直接來自[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構`lpszTo`的成員。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs

此資料成員是[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)類型的結構。

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>備註

`OLEUICHANGESOURCE`是用來控制 [OLE 變更來源] 對話方塊的行為。 此結構的成員可以直接修改。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

##  <a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource

呼叫此函式可判斷新來源是否有效。

```
BOOL IsValidSource();
```

### <a name="return-value"></a>傳回值

如果新來源有效，則為非零，否則為0。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 之後，才呼叫此函式。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
