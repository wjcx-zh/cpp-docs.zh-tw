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
ms.openlocfilehash: f4174369620f14f2d1ac410aa5d756c75097ad0f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421244"
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
|[COlePasteSpecialDialog::AddFormat](#addformat)|將自訂格式新增至您的應用程式可以貼上的格式清單。|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|將新專案新增至支援的剪貼簿格式清單。|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|將 CF_BITMAP、CF_DIB、CF_METAFILEPICT，以及選擇性地 CF_LINKSOURCE 新增至您的應用程式可以貼上的格式清單。|
|[COlePasteSpecialDialog：： CreateItem](#createitem)|使用指定的格式，在容器檔案中建立專案。|
|[COlePasteSpecialDialog：:D oModal](#domodal)|顯示 [OLE 貼上特殊] 對話方塊。|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|告訴您是否要將專案繪製為圖示。|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個專案的 iconic 表單相關聯之中繼檔的控制碼。|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|取得使用者所選擇之可用貼上選項的索引。|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|取得所選選取範圍的類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COlePasteSpecialDialog：： m_ps](#m_ps)|OLEUIPASTESPECIAL 類型的結構，可控制對話方塊的功能。|

## <a name="remarks"></a>備註

當您想要呼叫此對話方塊時，請建立類別 `COlePasteSpecialDialog` 的物件。 在結構化 `COlePasteSpecialDialog` 物件之後，您可以使用[AddFormat](#addformat)和[AddStandardFormats](#addstandardformats)成員函式，將剪貼簿格式加入至對話方塊。 您也可以使用[m_ps](#m_ps)結構，在對話方塊中初始化控制項的值或狀態。 `m_ps` 結構的類型是 OLEUIPASTESPECIAL。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw)結構。

如需有關 OLE 特定對話方塊的詳細資訊，請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>需求

**標頭：** afxodlgs。h

##  <a name="addformat"></a>COlePasteSpecialDialog::AddFormat

呼叫此函式可將新格式加入至您的應用程式可在貼上特殊作業中支援的格式清單。

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

*bcp.fmt*<br/>
要加入之資料類型的參考。

*lpszFormat*<br/>
描述使用者格式的字串。

*lpszResult*<br/>
字串，描述在對話方塊中選擇此格式時的結果。

*flags*<br/>
適用于此格式的不同連結和內嵌選項。 此旗標是 OLEUIPASTEFLAG 列舉類型中，一或多個不同值的位元組合。

*cf*<br/>
要加入的剪貼簿格式。

*tymed*<br/>
以這種格式提供的媒體類型。 這是 TYMED 列舉類型中一或多個值的位元組合。

*nFormatID*<br/>
識別此格式之字串的識別碼。 這個字串的格式是以 ' \n ' 字元分隔的兩個不同字串。 第一個字串與*lpstrFormat*參數中傳遞的是相同的，第二個則與*lpstrResult*參數相同。

*bEnableIcon*<br/>
決定在清單方塊中選擇此格式時，是否啟用 [顯示為圖示] 核取方塊的旗標。

*閃光*<br/>
決定在清單方塊中選擇此格式時，是否啟用 [貼上連結] 選項按鈕的旗標。

### <a name="remarks"></a>備註

您可以呼叫此函式來新增標準格式，例如 CF_TEXT 或 CF_TIFF，或是應用程式已向系統註冊的自訂格式。 如需將資料物件貼入應用程式的詳細資訊，請參閱[資料物件和資料來源：操作](../../mfc/data-objects-and-data-sources-manipulation.md)一文。

如需詳細資訊，請參閱[TYMED](/windows/win32/api/objidl/ne-objidl-tymed)列舉類型和在 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)列舉型別。

##  <a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry

將新專案新增至支援的剪貼簿格式清單。

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
要加入的剪貼簿格式。

### <a name="return-value"></a>傳回值

包含新連結專案之資訊的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)結構。

##  <a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats

呼叫此函式可將下列剪貼簿格式新增至您的應用程式可在貼上特殊作業中支援的格式清單：

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>參數

*bEnableLink*<br/>
旗標，決定是否要將 CF_LINKSOURCE 新增至您的應用程式可以貼上的格式清單。

### <a name="remarks"></a>備註

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **「Embedded 物件」**

- 也「**連結來源**」

這些格式是用來支援內嵌和連結。

##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog

建構 `COlePasteSpecialDialog` 物件。

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
建立旗標，包含使用位 OR 運算子結合的下列任意數目的旗標：

- PSF_SELECTPASTE 指定在呼叫對話方塊時，一開始會檢查 [貼上] 選項按鈕。 不能與 PSF_SELECTPASTELINK 搭配使用。 這是預設值。

- PSF_SELECTPASTELINK 指定在呼叫對話方塊時，一開始會檢查 [貼上連結] 選項按鈕。 不能與 PSF_SELECTPASTE 搭配使用。

- PSF_CHECKDISPLAYASICON 指定在呼叫對話方塊時，一開始就會檢查顯示為圖示的核取方塊。

- PSF_SHOWHELP 指定在呼叫對話方塊時，將會顯示 [說明] 按鈕。

*pDataObject*<br/>
指向要貼上的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。 如果此值為 Null，則會從剪貼簿取得 `COleDataObject`。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或擁有者視窗物件（屬於 `CWnd`類型）。 如果它是 Null，則對話方塊的父視窗會設定為主應用程式視窗。

### <a name="remarks"></a>備註

此函式只會 `COlePasteSpecialDialog` 物件的結構。 若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)列舉型別。

##  <a name="createitem"></a>COlePasteSpecialDialog：： CreateItem

建立 [貼上特殊] 對話方塊中所選擇的新專案。

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>參數

*pNewItem*<br/>
指向 `COleClientItem` 實例。 不能是 NULL。

### <a name="return-value"></a>傳回值

如果成功建立專案，則為非零;否則為0。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 之後，才能呼叫此函式。

##  <a name="domodal"></a>COlePasteSpecialDialog：:D oModal

顯示 [OLE 貼上特殊] 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊的完成狀態。 下列其中一個值：

- 如果已成功顯示對話方塊，則 IDOK。

- 如果使用者取消對話方塊，則 IDCANCEL。

- 如果發生錯誤，則 IDABORT。 如果傳回 IDABORT，請呼叫 `COleDialog::GetLastError` 成員函式，以取得所發生錯誤類型的詳細資訊。 如需可能錯誤的清單，請參閱 Windows SDK 中的[OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw)函數。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_ps](#m_ps)結構的成員來初始化各種對話方塊控制項，您應該先執行此動作，再呼叫 `DoModal`，但在構造對話方塊物件之後。

如果 `DoModal` 傳回 IDOK，您可以呼叫其他成員函式，以抓取使用者在對話方塊中輸入的設定或資訊。

##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

決定使用者是否選擇將選取的專案顯示為圖示。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>傳回值

呈現物件所需的方法。

- 當關閉對話方塊時，如果未核取 [顯示為圖示] 核取方塊，則會傳回 DVASPECT_CONTENT。

- 當關閉對話方塊時，如果已核取 [顯示為圖示] 核取方塊，則會傳回 DVASPECT_ICON。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 之後，才呼叫此函式。

如需有關繪製外觀的詳細資訊，請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

取得與使用者選取之專案相關聯的中繼檔。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含所選取專案之 iconic 層面的中繼檔控制碼，如果在對話方塊關閉時選取 [顯示為圖示] 核取方塊，請選擇 **[確定]** 。否則為 Null。

##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

取得與使用者選取之專案相關聯的索引值。

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>傳回值

使用者所選取 `OLEUIPASTEENTRY` 結構陣列中的索引。 執行貼上作業時，應該使用對應于所選索引的格式。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw)結構。

##  <a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType

決定使用者所做的選擇類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

傳回選取的類型。

### <a name="remarks"></a>備註

傳回型別值是由 `COlePasteSpecialDialog` 類別中宣告的 `Selection` 列舉型別所指定。

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

這些值的簡短 desccriptions 如下：

- `COlePasteSpecialDialog::pasteLink` 已核取 [貼上連結] 選項按鈕，而選擇的格式為標準 OLE 格式。

- `COlePasteSpecialDialog::pasteNormal` 已核取 [貼上] 選項按鈕，而選擇的格式為標準 OLE 格式。

- `COlePasteSpecialDialog::pasteOther` 選取的格式不是標準的 OLE 格式。

- `COlePasteSpecialDialog::pasteStatic` 選擇的格式是中繼檔。

##  <a name="m_ps"></a>COlePasteSpecialDialog：： m_ps

OLEUIPASTESPECIAL 類型的結構，用來控制 [貼上特殊] 對話方塊的行為。

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>備註

這個結構的成員可以直接修改，或透過成員函式來修改。

如需詳細資訊，請參閱 Windows SDK 中的[OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw)結構。

## <a name="see-also"></a>另請參閱

[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
