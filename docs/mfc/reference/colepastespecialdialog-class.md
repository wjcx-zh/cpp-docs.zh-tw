---
title: COlePasteSpecialDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
ms.openlocfilehash: 247514c37ef62987baa31be83efc73e05735904a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530022"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog 類別

用於 OLE 的 [選擇性貼上] 對話方塊。

## <a name="syntax"></a>語法

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|建構 `COlePasteSpecialDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|將的格式可以貼上您的應用程式清單中的自訂格式。|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|將新的項目加入至支援的剪貼簿格式的清單。|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|新增 CF_BITMAP，CF_DIB，CF_METAFILEPICT，並選擇性地 CF_LINKSOURCE 格式的清單到您的應用程式可以貼上。|
|[COlePasteSpecialDialog::CreateItem](#createitem)|使用指定的格式的容器文件中建立項目。|
|[COlePasteSpecialDialog::DoModal](#domodal)|會顯示 OLE 貼上 對話方塊。|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|會指示是否要繪製在項目做為圖示，或不。|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示格式相關聯的中繼檔的控制代碼。|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|取得已由使用者選擇可用的貼上選項的索引。|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|取得選取範圍選擇的型別。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|類型 OLEUIPASTESPECIAL 控制對話方塊中的函式的結構。|

## <a name="remarks"></a>備註

建立類別的物件`COlePasteSpecialDialog`當您想要呼叫此對話方塊。 在後`COlePasteSpecialDialog`在建構物件，您可以使用[AddFormat](#addformat)並[AddStandardFormats](#addstandardformats)剪貼簿格式加入對話方塊中的成員函式。 您也可以使用[m_ps](#m_ps)結構初始化的值或在對話方塊中控制項的狀態。 `m_ps`結構屬於 OLEUIPASTESPECIAL 的型別。

如需詳細資訊，請參閱 < [OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) Windows SDK 中的結構。

如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[對話方塊，在 OLE 中](../../mfc/dialog-boxes-in-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs.h

##  <a name="addformat"></a>  COlePasteSpecialDialog::AddFormat

呼叫此函式可將新的格式加入至您的應用程式可以選擇性貼上作業中支援的格式清單。

```
void AddFormat(
    const FORMATETC& formatEtc,
    LPTSTR lpszFormat,
    LPTSTR lpszResult,
    DWORD flags);

void AddFormat(
    UINT cf,
    DWORD tymed,
    UINT nFormatID,
    BOOL bEnableIcon,
    BOOL bLink);
```

### <a name="parameters"></a>參數

*fmt*<br/>
要加入的資料類型的參考。

*lpszFormat*<br/>
描述使用者所要的格式字串。

*lpszResult*<br/>
如果選擇此格式在對話方塊中，描述結果的字串。

*flags*<br/>
其他連結和內嵌選項適用於這種格式。 這個旗標的位元組合的其中一個或多個不同的值在 OLEUIPASTEFLAG 列舉型別。

*cf*<br/>
要加入的剪貼簿格式。

*tymed*<br/>
在這種格式中可用的媒體類型。 這是合的其中一個或多個 TYMED 中值的列舉型別。

*nFormatID*<br/>
識別此格式的字串識別碼。 此字串的格式是以 '\n' 字元分隔的兩個不同的字串。 第一個字串會相同，會傳入*lpstrFormat*參數，而第二個是相同*lpstrResult*參數。

*bEnableIcon*<br/>
旗標，決定是否要在清單方塊中選擇這種格式時，啟用以圖示顯示核取方塊。

*閃爍*<br/>
旗標，決定是否要在清單方塊中選擇這種格式時，啟用 [貼上連結] 選項按鈕。

### <a name="remarks"></a>備註

在呼叫此函式時，可以新增 CF_TEXT 或 CF_TIFF 之類的標準格式，或是自訂的格式，您的應用程式已向系統。 如需有關如何將資料物件貼到您的應用程式的詳細資訊，請參閱[資料物件和資料來源： 操作](../../mfc/data-objects-and-data-sources-manipulation.md)。

如需詳細資訊，請參閱 < [TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed)列舉型別並[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的結構。

如需詳細資訊，請參閱 < [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag)列舉 Windows SDK 中的型別。

##  <a name="addlinkentry"></a>  COlePasteSpecialDialog::AddLinkEntry

將新的項目加入至支援的剪貼簿格式的清單。

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
要加入的剪貼簿格式。

### <a name="return-value"></a>傳回值

[OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag)結構，其中包含新的連結項目的資訊。

##  <a name="addstandardformats"></a>  COlePasteSpecialDialog::AddStandardFormats

呼叫此函式可將下列的剪貼簿格式新增至您的應用程式可以選擇性貼上作業中支援的格式清單：

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>參數

*bEnableLink*<br/>
旗標，決定是否要加入的格式清單 CF_LINKSOURCE 您的應用程式可以貼上。

### <a name="remarks"></a>備註

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **「 內嵌的物件 」**

- （選擇性）**[連結來源]**

這些格式用來支援內嵌和連結。

##  <a name="colepastespecialdialog"></a>  COlePasteSpecialDialog::COlePasteSpecialDialog

建構 `COlePasteSpecialDialog` 物件。

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
建立旗標，會包含任意數目的使用位元 OR 運算子結合下列旗標：

- PSF_SELECTPASTE 指定貼上選項按鈕將會檢查一開始呼叫對話方塊時。 不能搭配 PSF_SELECTPASTELINK。 這是預設值。

- PSF_SELECTPASTELINK 指定貼上連結 選項按鈕將會檢查一開始呼叫對話方塊時。 不能搭配 PSF_SELECTPASTE。

- PSF_CHECKDISPLAYASICON 指定以圖示顯示核取方塊將會檢查一開始呼叫對話方塊時。

- PSF_SHOWHELP 指定對話方塊中呼叫時，會顯示 [說明] 按鈕。

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md)貼上文字。 如果這個值是 NULL，它會取得`COleDataObject`從剪貼簿。

*pParentWnd*<br/>
指向的父系或擁有者的視窗物件 (類型的`CWnd`) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊中的父視窗設為主要的應用程式視窗。

### <a name="remarks"></a>備註

此函式只會建構`COlePasteSpecialDialog`物件。 若要顯示的對話方塊，請呼叫[DoModal](#domodal)函式。

如需詳細資訊，請參閱 < [OLEUIPASTEFLAG](/windows/desktop/api/oledlg/ne-oledlg-tagoleuipasteflag)列舉 Windows SDK 中的型別。

##  <a name="createitem"></a>  COlePasteSpecialDialog::CreateItem

建立 [選擇性貼上] 對話方塊中選擇新項目。

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>參數

*pNewItem*<br/>
指向`COleClientItem`執行個體。 不可以是 NULL。

### <a name="return-value"></a>傳回值

如果已成功; 建立的項目，非零值。否則為 0。

### <a name="remarks"></a>備註

此函式應該只呼叫之後[DoModal](#domodal)傳回 IDOK。

##  <a name="domodal"></a>  COlePasteSpecialDialog::DoModal

會顯示 OLE 貼上 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊中的完成狀態。 下列其中一個值：

- 如果對話方塊已成功顯示，IDOK。

- 如果使用者已取消對話方塊，IDCANCEL。

- IDABORT 發生錯誤。 如果傳回 IDABORT，呼叫`COleDialog::GetLastError`成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱 < [OleUIPasteSpecial](/windows/desktop/api/oledlg/nf-oledlg-oleuipastespeciala) Windows SDK 中的函式。

### <a name="remarks"></a>備註

如果您想要設定的成員初始化各種不同的對話方塊控制項[m_ps](#m_ps)結構，您應該執行這項操作之前先呼叫`DoModal`，但在建構對話方塊物件之後。

如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式來擷取在對話方塊中的 設定 或 使用者的資訊輸入。

##  <a name="getdrawaspect"></a>  COlePasteSpecialDialog::GetDrawAspect

判斷使用者是否選擇選取的項目顯示為圖示。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>傳回值

需要來呈現物件的方法。

- DVASPECT_CONTENT 傳回，如果以圖示顯示核取方塊未核取時關閉對話方塊。

- 如果已關閉對話方塊時，選取 顯示為圖示的核取方塊，就會傳回 DVASPECT_ICON。

### <a name="remarks"></a>備註

此函式之後，才呼叫[DoModal](#domodal)傳回 IDOK。

如需有關繪圖外觀的詳細資訊，請參閱[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的結構。

##  <a name="geticonicmetafile"></a>  COlePasteSpecialDialog::GetIconicMetafile

取得使用者所選取的項目相關聯的中繼檔。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

如果以圖示顯示核取方塊已選取對話方塊中選擇解除時，包含選取的項目圖示的層面之中繼檔的控制代碼**確定**，否則為 NULL。

##  <a name="getpasteindex"></a>  COlePasteSpecialDialog::GetPasteIndex

取得索引值相關聯的項目選取的使用者。

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>傳回值

陣列索引`OLEUIPASTEENTRY`使用者所選取的結構。 執行貼上作業時，應對應至選取之索引的格式。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [OLEUIPASTEENTRY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipasteentrya) Windows SDK 中的結構。

##  <a name="getselectiontype"></a>  COlePasteSpecialDialog::GetSelectionType

判斷使用者所做的選取項目的類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

傳回型別所做的選擇。

### <a name="remarks"></a>備註

所指定的傳回型別值`Selection`列舉型別中宣告`COlePasteSpecialDialog`類別。

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

請依照下列這些值的簡短 desccriptions:

- `COlePasteSpecialDialog::pasteLink` [貼上連結] 選項按鈕已核取，而且所選的格式的標準 OLE 格式。

- `COlePasteSpecialDialog::pasteNormal` 貼上選項按鈕已核取，而且所選的格式的標準 OLE 格式。

- `COlePasteSpecialDialog::pasteOther` 選取的格式不是標準的 OLE 格式。

- `COlePasteSpecialDialog::pasteStatic` 所選的格式的中繼檔。

##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps

類型 OLEUIPASTESPECIAL 結構用來控制 [選擇性貼上] 對話方塊中的行為。

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>備註

直接或透過成員函式，則可以修改此結構的成員。

如需詳細資訊，請參閱 < [OLEUIPASTESPECIAL](/windows/desktop/api/oledlg/ns-oledlg-tagoleuipastespeciala) Windows SDK 中的結構。

## <a name="see-also"></a>另請參閱

[MFC 範例 OCLIENT](../../visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
