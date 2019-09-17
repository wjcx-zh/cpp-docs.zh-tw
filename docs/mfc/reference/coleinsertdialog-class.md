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
ms.openlocfilehash: a884f946b60be0567f39477f434db8efe041e393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503936"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog 類別

用於 OLE 的 [插入物件] 對話方塊。

## <a name="syntax"></a>語法

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|建構 `COleInsertDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|建立在對話方塊中選取的專案。|
|[COleInsertDialog::DoModal](#domodal)|顯示 [OLE 插入物件] 對話方塊。|
|[COleInsertDialog::GetClassID](#getclassid)|取得與所選項目相關聯的 CLSID。|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|告訴您是否要將專案繪製為圖示。|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個專案的 iconic 表單相關聯之中繼檔的控制碼。|
|[COleInsertDialog::GetPathName](#getpathname)|取得在對話方塊中所選擇之檔案的完整路徑。|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|取得選取之物件的類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|OLEUIINSERTOBJECT 類型的結構，可控制對話方塊的行為。|

## <a name="remarks"></a>備註

當您想要呼叫`COleInsertDialog`此對話方塊時，請建立類別的物件。 在結構化物件之後，您可以使用 [m_io](#m_io)結構，在對話方塊中初始化控制項的值或`COleInsertDialog`狀態。 `m_io`結構的型別為 OLEUIINSERTOBJECT。 如需使用此對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。

> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw)結構。

如需有關 OLE 特定對話方塊的詳細資訊，請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs。h

##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

此函式只會`COleInsertDialog`對物件進行結構。

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
建立旗標，其中包含要使用位 OR 運算子結合的下列任意數目的值：

- IOF_SHOWHELP 指定對話方塊被呼叫時，將會顯示 [說明] 按鈕。

- IOF_SELECTCREATENEW 指定在呼叫對話方塊時，一開始會選取 [建立新的] 選項按鈕。 這是預設值，無法與 IOF_SELECTCREATEFROMFILE 搭配使用。

- IOF_SELECTCREATEFROMFILE 指定在呼叫對話方塊時，一開始會選取 [從檔案建立] 選項按鈕。 不能與 IOF_SELECTCREATENEW 搭配使用。

- IOF_CHECKLINK 指定在呼叫對話方塊時，一開始就會檢查連結核取方塊。

- IOF_DISABLELINK 指定在呼叫對話方塊時，將會停用 [連結] 核取方塊。

- IOF_CHECKDISPLAYASICON 指定一開始會檢查顯示為圖示的核取方塊，將會顯示目前的圖示，而且在呼叫對話方塊時，將會啟用 [變更圖示] 按鈕。

- IOF_VERIFYSERVERSEXIST 指定對話方塊應該藉由確保註冊資料庫中指定的伺服器存在，然後才會顯示對話方塊，以驗證它新增至清單方塊的類別。 設定此旗標可能會大幅降低效能。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或擁有者視窗物件`CWnd`（類型為）。 如果它是 Null，則對話方塊物件的父視窗會設定為主應用程式視窗。

### <a name="remarks"></a>備註

若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。

##  <a name="createitem"></a>COleInsertDialog：： CreateItem

只有在[DoModal](#domodal)傳回 IDOK 時，才能呼叫此函式來建立類型為[COleClientItem](../../mfc/reference/coleclientitem-class.md)的物件。

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要建立的專案。

### <a name="return-value"></a>傳回值

如果已建立專案，則為非零值;否則為0。

### <a name="remarks"></a>備註

您必須先配置`COleClientItem`物件，才能呼叫此函式。

##  <a name="domodal"></a>COleInsertDialog：:D oModal

呼叫此函式以顯示 [OLE 插入物件] 對話方塊。

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
下列其中一個值：

`COleInsertDialog::DocObjectsOnly`只插入 DocObjects。

`COleInsertDialog::ControlsOnly`只插入 ActiveX 控制項。

零不會插入 DocObject 或 ActiveX 控制項。 這個值會產生與上面所列的第一個原型相同的執行。

### <a name="return-value"></a>傳回值

對話方塊的完成狀態。 下列其中一個值：

- 如果已成功顯示對話方塊，則 IDOK。

- 如果使用者取消對話方塊，則 IDCANCEL。

- 如果發生錯誤，則 IDABORT。 如果傳回 IDABORT，請呼叫[COleDialog：： GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式，以取得所發生錯誤類型的詳細資訊。 如需可能錯誤的清單，請參閱 Windows SDK 中的[OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw)函數。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_io](#m_io)結構的成員來初始化各種對話方塊控制項，您應該在呼叫`DoModal`之前執行此動作，但在構造對話方塊物件之後。

如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式，以抓取使用者在對話方塊中的設定或資訊輸入。

##  <a name="getclassid"></a>COleInsertDialog::GetClassID

只有在[DoModal](#domodal)傳回 IDOK，且選取類型為時`COleInsertDialog::createNewItem`，才可呼叫此函式來取得與所選項目的關聯的 CLSID。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>傳回值

傳回與所選項目的關聯的 CLSID。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

呼叫此函式可判斷使用者是否選擇將選取的專案顯示為圖示。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>傳回值

呈現物件所需的方法。

- 如果未核取 [顯示為圖示] 核取方塊，則會傳回 DVASPECT_CONTENT。

- 如果已核取 [顯示為圖示] 核取方塊，則會傳回 DVASPECT_ICON。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 時，才呼叫此函式。

如需有關繪製外觀的詳細資訊，請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)資料結構。

##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

呼叫此函式可取得中繼檔的控制碼，其中包含所選取專案的 iconic 層面。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含所選取專案之 iconic 層面的中繼檔控制碼，如果在對話方塊關閉時，選取 [**確定**]，就會核取 [顯示為圖示] 核取方塊。否則為 Null。

##  <a name="getpathname"></a>COleInsertDialog::GetPathName

只有在[DoModal](#domodal)傳回 IDOK，且選取類型不是時，才會`COleInsertDialog::createNewItem`呼叫此函式來取得選取之檔案的完整路徑。

```
CString GetPathName() const;
```

### <a name="return-value"></a>傳回值

在對話方塊中選取之檔案的完整路徑。 如果選取類型為`createNewItem`，則此函式會在發行模式中傳回無意義`CString`的，或在 debug 模式中造成判斷提示。

##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType

選擇 [**確定]** 以在關閉 [插入物件] 對話方塊時，呼叫此函式以取得選擇的類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

所選取的類型。

### <a name="remarks"></a>備註

傳回型別值是由`Selection` `COleInsertDialog`類別中宣告的列舉型別所指定。

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

這些值的簡短說明如下：

- `COleInsertDialog::createNewItem`已選取 [建立新的] 選項按鈕。

- `COleInsertDialog::insertFromFile`已選取 [從檔案建立] 選項按鈕，且未核取 [連結] 核取方塊。

- `COleInsertDialog::linkToFile`已選取 [從檔案建立] 選項按鈕，並已核取 [連結] 核取方塊。

##  <a name="m_io"></a>COleInsertDialog::m_io

OLEUIINSERTOBJECT 類型的結構，用來控制 [插入物件] 對話方塊的行為。

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>備註

這個結構的成員可以直接或透過成員函式來修改。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw)結構。

## <a name="see-also"></a>另請參閱

[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
