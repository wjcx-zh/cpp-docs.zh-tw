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
ms.openlocfilehash: 27bf98ea4fe6951624873c1463d50f37558c9234
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159921"
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
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|建構 `COleInsertDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|建立在對話方塊中選取的項目。|
|[COleInsertDialog::DoModal](#domodal)|會顯示 OLE 插入物件 對話方塊。|
|[COleInsertDialog::GetClassID](#getclassid)|取得所選的項目相關聯的 CLSID。|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|會指示是否要繪製為圖示的項目。|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示格式相關聯的中繼檔的控制代碼。|
|[COleInsertDialog::GetPathName](#getpathname)|取得在對話方塊中選擇的檔案的完整路徑。|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|取得所選物件的類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|類型的對話方塊行為的 OLEUIINSERTOBJECT 的結構。|

## <a name="remarks"></a>備註

建立類別的物件`COleInsertDialog`當您想要呼叫此對話方塊。 在後`COleInsertDialog`在建構物件，您可以使用[m_io](#m_io)結構初始化的值或在對話方塊中控制項的狀態。 `m_io`結構屬於 OLEUIINSERTOBJECT 的型別。 如需使用這個對話方塊類別的詳細資訊，請參閱 < [DoModal](#domodal)成員函式。

> [!NOTE]
>  應用程式精靈所產生的容器程式碼會使用這個類別。

如需詳細資訊，請參閱 < [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) Windows SDK 中的結構。

如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[對話方塊，在 OLE 中](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs.h

##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog

此函式會建構只`COleInsertDialog`物件。

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
包含任意數目的下列值來使用位元 OR 運算子加以結合，建立旗標：

- IOF_SHOWHELP 指定對話方塊中呼叫時，會顯示 [說明] 按鈕。

- IOF_SELECTCREATENEW 指定要建立新的選項按鈕選取一開始時呼叫對話方塊。 這是預設值，並不能搭配 IOF_SELECTCREATEFROMFILE。

- IOF_SELECTCREATEFROMFILE 指定要從檔案建立選項按鈕選取一開始時呼叫的對話方塊。 無法搭配 IOF_SELECTCREATENEW。

- IOF_CHECKLINK 指定連結核取方塊將會檢查一開始時呼叫對話方塊。

- IOF_DISABLELINK 指定連結核取方塊將會停用，呼叫對話方塊時。

- IOF_CHECKDISPLAYASICON 指定以圖示顯示核取方塊將會檢查一開始，將會顯示目前的圖示，並呼叫對話方塊時，將會啟用 [變更圖示] 按鈕。

- IOF_VERIFYSERVERSEXIST 指定對話方塊應該驗證它會加入至清單方塊確保系統註冊資料庫中指定的伺服器存在對話方塊顯示之前的類別。 設定這個旗標，可以大幅降低效能。

*pParentWnd*<br/>
指向的父系或擁有者的視窗物件 (類型的`CWnd`) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊物件的父視窗設為主要的應用程式視窗。

### <a name="remarks"></a>備註

若要顯示的對話方塊，請呼叫[DoModal](#domodal)函式。

##  <a name="createitem"></a>  COleInsertDialog::CreateItem

呼叫此函式來建立物件的型別[COleClientItem](../../mfc/reference/coleclientitem-class.md)只有當[DoModal](#domodal)傳回 IDOK。

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
要建立之項目的點。

### <a name="return-value"></a>傳回值

建立項目; 如果為非零否則為 0。

### <a name="remarks"></a>備註

您必須配置`COleClientItem`物件之前，您可以呼叫此函式。

##  <a name="domodal"></a>  COleInsertDialog::DoModal

呼叫此函式可顯示 OLE 插入物件 對話方塊。

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
下列其中一個值：

`COleInsertDialog::DocObjectsOnly` 插入只 DocObjects。

`COleInsertDialog::ControlsOnly` 插入只有 ActiveX 控制項。

DocObject 或 ActiveX 控制項都不會插入為零。 上面所列的這個值會產生相同的實作作為第一個原型。

### <a name="return-value"></a>傳回值

對話方塊中的完成狀態。 下列其中一個值：

- 如果對話方塊已成功顯示，IDOK。

- 如果使用者已取消對話方塊，IDCANCEL。

- IDABORT 發生錯誤。 如果傳回 IDABORT，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱 < [OleUIInsertObject](/windows/desktop/api/oledlg/nf-oledlg-oleuiinsertobjecta) Windows SDK 中的函式。

### <a name="remarks"></a>備註

如果您想要設定的成員初始化各種不同的對話方塊控制項[m_io](#m_io)結構，您應該執行這項操作之前先呼叫`DoModal`，但在建構對話方塊物件之後。

如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式來擷取設定或輸入 [使用者] 對話方塊中的資訊。

##  <a name="getclassid"></a>  COleInsertDialog::GetClassID

呼叫此函式可取得所選的項目只有當相關聯的 CLSID [DoModal](#domodal)傳回 IDOK 及選取項目類型是`COleInsertDialog::createNewItem`。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>傳回值

傳回選取的項目相關聯的 CLSID。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [CLSID 金鑰](/windows/desktop/com/clsid-key-hklm)Windows SDK 中。

##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect

呼叫此函式可判斷使用者是否選擇選取的項目顯示為圖示。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>傳回值

需要來呈現物件的方法。

- 如果未檢查以圖示顯示核取方塊，就會傳回 DVASPECT_CONTENT。

- 如果已核取圖示以顯示核取方塊，就會傳回 DVASPECT_ICON。

### <a name="remarks"></a>備註

呼叫此函式才[DoModal](#domodal)傳回 IDOK。

如需有關繪圖外觀的詳細資訊，請參閱[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的資料結構。

##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile

呼叫此函式可取得包含選取的項目圖示的層面之中繼檔的控制代碼。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含選取的項目圖示的層面，以圖示顯示核取方塊時的中繼檔的控制代碼可讓您檢查時已選擇關閉對話方塊**確定**，否則為 NULL。

##  <a name="getpathname"></a>  COleInsertDialog::GetPathName

呼叫此函式可取得的完整路徑的選取的檔案才[DoModal](#domodal) IDOK 及選取項目類型不會傳回`COleInsertDialog::createNewItem`。

```
CString GetPathName() const;
```

### <a name="return-value"></a>傳回值

在對話方塊中選取的檔案完整路徑。 如果選取項目型別是`createNewItem`，此函數會傳回沒有任何意義`CString`在發行模式中或在偵錯模式下引起判斷提示。

##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType

呼叫此函式，以取得選取項目類型選擇 [插入物件] 對話方塊中選擇時解除**確定**。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

所做的選取項目的類型。

### <a name="remarks"></a>備註

所指定的傳回型別值`Selection`列舉型別中宣告`COleInsertDialog`類別。

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

請依照下列這些值的簡短描述：

- `COleInsertDialog::createNewItem` 建立新的選項按鈕已選取。

- `COleInsertDialog::insertFromFile` 從檔案建立選項按鈕已選取，未檢查連結核取方塊。

- `COleInsertDialog::linkToFile` 從檔案建立選項按鈕已選取，並連結核取方塊已核取。

##  <a name="m_io"></a>  COleInsertDialog::m_io

類型 OLEUIINSERTOBJECT 結構用來控制 [插入物件] 對話方塊中的行為。

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>備註

直接或透過成員函式，則可以修改此結構的成員。

如需詳細資訊，請參閱 < [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) Windows SDK 中的結構。

## <a name="see-also"></a>另請參閱

[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
