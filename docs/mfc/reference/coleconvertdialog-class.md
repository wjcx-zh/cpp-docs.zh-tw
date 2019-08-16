---
title: COleConvertDialog 類別
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: ba57e756457fcffca806eeba7454ddf7bcf99d34
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504301"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 類別

如需詳細資訊, 請參閱 Windows SDK 中的[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)結構。

## <a name="syntax"></a>語法

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|建構 `COleConvertDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleConvertDialog::DoConvert](#doconvert)|執行對話方塊中所指定的轉換。|
|[COleConvertDialog::DoModal](#domodal)|顯示 [OLE 變更專案] 對話方塊。|
|[COleConvertDialog::GetClassID](#getclassid)|取得與所選項目相關聯的 CLSID。|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|指定是否要將專案繪製為圖示。|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個專案的 iconic 表單相關聯之中繼檔的控制碼。|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|取得所選選取範圍的類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|結構, 控制對話方塊的行為。|

## <a name="remarks"></a>備註

> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。

如需有關 OLE 特定對話方塊的詳細資訊, 請參閱[ole 中](../../mfc/dialog-boxes-in-ole.md)的文章對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>需求

**標頭:** afxodlgs。h

##  <a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog

只會構造`COleConvertDialog`物件。

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要轉換或啟用的專案。

*dwFlags*<br/>
建立旗標, 其中包含使用位 or 運算子結合的下列任何數目的值:

- CF_SELECTCONVERTTO 指定在呼叫對話方塊時, 一開始會選取 [轉換成] 選項按鈕。 這是預設值。

- CF_SELECTACTI加值稅EAS 指定在呼叫對話方塊時, 一開始會選取 [啟動為] 選項按鈕。

- CF_SETCONVERTDEFAULT 指定當選取 [轉換成] 選項按鈕時`clsidConvertDefault` , 由`m_cv`結構的成員指定其 CLSID 的類別會當做 [類別] 清單方塊中的預設選項使用。

- CF_SETACTI加值稅EDEFAULT 指定當選取 [啟動為] 選項按鈕時`clsidActivateDefault` , 由`m_cv`結構的成員指定其 CLSID 的類別會當做 [類別] 清單方塊中的預設選項使用。

- CF_SHOWHELPBUTTON 指定對話方塊被呼叫時, 將會顯示 [說明] 按鈕。

*pClassID*<br/>
指向要轉換或啟用之專案的 CLSID。 如果是 Null, 將會使用與*pItem*相關聯的 CLSID。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或擁有者視窗物件`CWnd`(類型為)。 如果它是 Null, 則對話方塊的父視窗會設定為主應用程式視窗。

### <a name="remarks"></a>備註

若要顯示對話方塊, 請呼叫[DoModal](#domodal)函式。

如需詳細資訊, 請參閱[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)和[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)結構。

##  <a name="doconvert"></a>COleConvertDialog::D oConvert

從[DoModal](#domodal)成功傳回之後呼叫此函式, 以轉換或啟動[COleClientItem](../../mfc/reference/coleclientitem-class.md)類型的物件。

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要轉換或啟用的專案。 不可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

專案會根據使用者在 [轉換] 對話方塊中選取的資訊進行轉換或啟用。

##  <a name="domodal"></a>COleConvertDialog::D oModal

呼叫此函式以顯示 [OLE 轉換] 對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話方塊的完成狀態。 下列其中一個值：

- 如果已成功顯示對話方塊, 則 IDOK。

- 如果使用者取消對話方塊, 則 IDCANCEL。

- 如果發生錯誤, 則 IDABORT。 如果傳回 IDABORT, 請呼叫[COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式, 以取得所發生錯誤類型的詳細資訊。 如需可能錯誤的清單, 請參閱 Windows SDK 中的[OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw)函數。

### <a name="remarks"></a>備註

如果您想要藉由設定[m_cv](#m_cv)結構的成員來初始化各種對話方塊控制項, 您應該在呼叫`DoModal`之前執行此動作, 但在構造對話方塊物件之後。

如果`DoModal`傳回 IDOK, 您可以呼叫其他成員函式, 以抓取使用者在對話方塊中輸入的設定或資訊。

##  <a name="getclassid"></a>COleConvertDialog::GetClassID

呼叫此函式可取得與使用者在 [轉換] 對話方塊中選取之專案相關聯的 CLSID。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>傳回值

與 [轉換] 對話方塊中所選取之專案相關聯的 CLSID。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 之後, 才呼叫此函式。

如需詳細資訊, 請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

##  <a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect

呼叫此函式可判斷使用者是否選擇將選取的專案顯示為圖示。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>傳回值

呈現物件所需的方法。

- 如果未核取 [顯示為圖示] 核取方塊, 則會傳回 DVASPECT_CONTENT。

- 如果已核取 [顯示為圖示] 核取方塊, 則會傳回 DVASPECT_ICON。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 之後, 才呼叫此函式。

如需有關繪製外觀的詳細資訊, 請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)資料結構。

##  <a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

呼叫此函式可取得中繼檔的控制碼, 其中包含所選取專案的 iconic 層面。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含所選取專案之 iconic 層面的中繼檔控制碼, 如果在對話方塊關閉時, 選取 [確定], 就會核取 [顯示為圖示] 核取方塊。否則為 Null。

##  <a name="getselectiontype"></a>COleConvertDialog::GetSelectionType

呼叫此函式可決定 [轉換] 對話方塊中所選取的轉換類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

所選取的類型。

### <a name="remarks"></a>備註

傳回型別值是由`Selection` `COleConvertDialog`類別中宣告的列舉型別所指定。

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

這些值的簡短說明如下:

- `COleConvertDialog::noConversion`如果已取消對話方塊, 或使用者未選取任何轉換, 則傳回。 如果`COleConvertDialog::DoModal`傳回 IDOK, 則使用者可能選取了與先前所選取不同的圖示。

- `COleConvertDialog::convertItem`如果已核取 [轉換成] 選項按鈕, 則會傳回, 使用者選取不同的專案以`DoModal`轉換成, 並傳回 IDOK。

- `COleConvertDialog::activateAs`如果已核取 [啟用為] 選項按鈕, 則會傳回, 使用者選取不同的專案`DoModal`來啟動, 並傳回 IDOK。

##  <a name="m_cv"></a>  COleConvertDialog::m_cv

OLEUICONVERT 類型的結構, 用來控制 [轉換] 對話方塊的行為。

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>備註

這個結構的成員可以直接或透過成員函式來修改。

如需詳細資訊, 請參閱 Windows SDK 中的[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
