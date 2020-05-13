---
title: COleInsertDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
ms.openlocfilehash: b5de4ff5daa80e1d8727444a4cfd275597e18c08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374965"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog 類別

用於 OLE 的 [插入物件] 對話方塊。

## <a name="syntax"></a>語法

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COle 插入對話框::COle 插入對話框](#coleinsertdialog)|建構 `COleInsertDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleInsert 對話::建立專案](#createitem)|建立對話框中選擇的專案。|
|[COleInsertDialog::Do模態](#domodal)|顯示"OLE 插入物件"對話框。|
|[COleInsert對話::取得類ID](#getclassid)|獲取與所選項關聯的 CLSID。|
|[COleInsert對話::取得繪製方面](#getdrawaspect)|告訴是否將項目繪製為圖示。|
|[COleInsert 對話::取得圖示Meta檔案](#geticonicmetafile)|獲取與此項目的標誌性形式關聯的元檔的句柄。|
|[COleInsert 對話::獲取路徑名稱](#getpathname)|獲取對話框中選擇的檔的完整路徑。|
|[COleInsert 對話::取得選擇類型](#getselectiontype)|獲取所選物件的類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleInsert對話::m_io](#m_io)|控制對話框行為的 OLEUIINSERTOBJECT 類型的結構。|

## <a name="remarks"></a>備註

要呼叫此對話方塊`COleInsertDialog`時 ,請創建類的物件。 建構`COleInsertDialog`物件后,可以使用[m_io](#m_io)結構在對話框中初始化控制件的值或狀態。 結構`m_io`為「奧萊伊插入對象」類型。 有關使用此對話方塊類的詳細資訊,請參閱[DoModal](#domodal)成員函數。

> [!NOTE]
> 應用程式精靈生成的容器代碼使用此類。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIINSERTOBJECT 結構](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw)。

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="coleinsertdialogcoleinsertdialog"></a><a name="coleinsertdialog"></a>COle 插入對話框::COle 插入對話框

此函數只建構物件`COleInsertDialog`。

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
建立標誌,其中包含要使用位-OR 運算子組合的任意數量的以下值:

- IOF_SHOWHELP 指定在調用對話框時將顯示"説明"按鈕。

- IOF_SELECTCREATENEW 指定在調用對話方塊時,最初將選擇"創建新單選"按鈕。 這是預設值,不能與IOF_SELECTCREATEFROMFILE一起使用。

- IOF_SELECTCREATEFROMFILE 指定在調用對話方塊時,最初將選擇「從檔案創建單選」按鈕。 不能與IOF_SELECTCREATENEW一起使用。

- IOF_CHECKLINK 指定在調用對話方塊時,將首先選中「連結」複選框。

- IOF_DISABLELINK 指定在調用對話方塊時將禁用"連結"複選框。

- IOF_CHECKDISPLAYASICON 指定最初將選中"顯示為圖示"複選框,將顯示當前圖示,並在調用對話框時啟用"更改圖示"按鈕。

- IOF_VERIFYSERVERSEXIST 指定對話框應通過確保在顯示對話方塊之前在註冊資料庫中指定的伺服器來驗證它添加到清單框中的類。 設置此標誌可能會顯著削弱性能。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件`CWnd`(類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

要顯示對話框,請調用[DoModal](#domodal)函數。

## <a name="coleinsertdialogcreateitem"></a><a name="createitem"></a>COleInsert 對話::建立專案

僅當[DoModal](#domodal)傳回 IDOK 時,才呼叫此函數以創建[COleClientItem](../../mfc/reference/coleclientitem-class.md)類型的物件。

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要創建的項。

### <a name="return-value"></a>傳回值

創建項時非零;否則 0。

### <a name="remarks"></a>備註

必須先分配物件,`COleClientItem`然後才能呼叫此函數。

## <a name="coleinsertdialogdomodal"></a><a name="domodal"></a>COleInsertDialog::Do模態

呼叫此函數以顯示"OLE 插入物件"對話框。

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
下列其中一個值：

`COleInsertDialog::DocObjectsOnly`僅插入文件物件。

`COleInsertDialog::ControlsOnly`僅插入 ActiveX 控件。

零既不插入文檔物件,也不插入 ActiveX 控制項。 此值導致與上面列出的第一個原型相同的實現。

### <a name="return-value"></a>傳回值

對話框的完成狀態。 下列其中一個值：

- 如果對話框已成功顯示,則 IDOK。

- 如果使用者取消了對話框,則進行 IDCANCEL。

- 如果發生錯誤,則 IDABORT。 如果返回 IDABORT,請呼叫[COleDialog:getLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函數,以獲取有關所發生錯誤類型的詳細資訊。 有關可能錯誤的清單,請參閱 Windows SDK 中的[OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw)函數。

### <a name="remarks"></a>備註

如果要通過設置[m_io](#m_io)結構的成員來初始化各種對話框控件,則應在調用`DoModal`之前執行此操作,但在構造對話框物件之後。

如果`DoModal`返回 IDOK,則可以調用其他成員函數來檢索使用者輸入到對話方塊中的設置或資訊。

## <a name="coleinsertdialoggetclassid"></a><a name="getclassid"></a>COleInsert對話::取得類ID

僅當[DoModal](#domodal)傳回 IDOK`COleInsertDialog::createNewItem`並且選擇類型為 時,才調用此函數以獲取與選定項關聯的 CLSID。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>傳回值

返回與所選項關聯的 CLSID。

### <a name="remarks"></a>備註

關於詳細資訊,請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

## <a name="coleinsertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleInsert對話::取得繪製方面

呼叫此函數以確定使用者是否選擇將選取項目顯示為圖示。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>傳回值

呈現物件所需的方法。

- 如果未選中「顯示為圖示」複選框,則DVASPECT_CONTENT返回。

- DVASPECT_ICON如果選中「顯示為圖示」複選框,則返回。

### <a name="remarks"></a>備註

僅當[DoModal](#domodal)返回 IDOK 時才呼叫此函數。

有關繪圖方面的詳細資訊,請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)資料結構。

## <a name="coleinsertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleInsert 對話::取得圖示Meta檔案

呼叫此函數以獲取包含所選項標誌性方面的元檔的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含選定項目標誌性方面的元檔的句柄,如果通過選擇 **「確定**」在對話框中取消對話框時選中「顯示為圖示」複選框。否則 NULL。

## <a name="coleinsertdialoggetpathname"></a><a name="getpathname"></a>COleInsert 對話::獲取路徑名稱

僅當[DoModal](#domodal)傳回 IDOK`COleInsertDialog::createNewItem`並且選擇類型不是 時,才調用此函數獲取所選檔的完整路徑。

```
CString GetPathName() const;
```

### <a name="return-value"></a>傳回值

對話框中選擇的檔的完整路徑。 如果選擇類型為`createNewItem`,則此函數在`CString`發佈 模式下返回無意義,或在調試模式下導致斷言。

## <a name="coleinsertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleInsert 對話::取得選擇類型

呼叫此函數,在通過選擇 **「確定**」來取消「插入物件」對話框時選擇選擇類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

選擇的類型。

### <a name="remarks"></a>備註

返回類型值由類中聲明的`Selection``COleInsertDialog`枚舉類型指定。

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

這些值的簡要說明如下:

- `COleInsertDialog::createNewItem`選擇了"創建新單選"按鈕。

- `COleInsertDialog::insertFromFile`選擇了「從檔案創建」單選按鈕,並且未選中「連結」複選框。

- `COleInsertDialog::linkToFile`選擇了「從檔案創建」單選按鈕,並選中了「連結」複選框。

## <a name="coleinsertdialogm_io"></a><a name="m_io"></a>COleInsert對話::m_io

用於控制「插入物件」對話框的行為的 OLEUIINSERTOBJECT 類型的結構。

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>備註

此結構的成員可以直接或通過成員函數進行修改。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIINSERTOBJECT 結構](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw)。

## <a name="see-also"></a>另請參閱

[MFC 樣品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
