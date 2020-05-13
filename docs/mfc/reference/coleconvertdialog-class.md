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
ms.openlocfilehash: 6d6690b8d06df29ce9fcd323eb8724009ee3cca9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366170"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 類別

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)結構。

## <a name="syntax"></a>語法

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COle 轉換對話框::COleConvert對話](#coleconvertdialog)|建構 `COleConvertDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleConvert對話::DoConvert](#doconvert)|執行對話框中指定的轉換。|
|[COleConvert對話::Do模態](#domodal)|顯示"OLE 更改項目"對話方塊。|
|[COleConvert 對話:取得類別ID](#getclassid)|獲取與所選項關聯的 CLSID。|
|[COleConvert對話::取得繪製方面](#getdrawaspect)|指定是否將項目繪製為圖示。|
|[COleConvert 對話:取得圖示Meta檔案](#geticonicmetafile)|獲取與此項目的標誌性形式關聯的元檔的句柄。|
|[COleConvert 對話:取得選擇類型](#getselectiontype)|獲取所選選擇的類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleConvert對話::m_cv](#m_cv)|控制對話框行為的結構。|

## <a name="remarks"></a>備註

> [!NOTE]
> 應用程式精靈生成的容器代碼使用此類。

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COle 轉換對話框::COleConvert對話

只建構物件`COleConvertDialog`。

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要轉換或啟動的專案。

*dwFlags*<br/>
建立標誌,其中包含使用位或運算子組合的以下任意數量的值:

- CF_SELECTCONVERTTO 指定在調用對話方塊時,最初將選擇"轉換為單選"按鈕。 這是預設值。

- CF_SELECTACTIVATEAS 指定在調用對話方塊時,最初將選擇"啟動為單選"按鈕。

- CF_SETCONVERTDEFAULT 指定選擇"轉換為單選"按鈕時`clsidConvertDefault`,`m_cv`由結構成員指定的 CLSID 的類將作為類清單框中的預設選擇。

- CF_SETACTIVATEDEFAULT 指定選擇「啟動為單選」按鈕`clsidActivateDefault`時,`m_cv`由結構成員指定的 CLSID 的類將作為類清單框中的預設選擇。

- CF_SHOWHELPBUTTON 指定在調用對話框時將顯示"説明"按鈕。

*pClassID*<br/>
指向要轉換或啟動的專案的 CLSID。 如果為 NULL,將使用與*pItem*關聯的 CLSID。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件`CWnd`(類型)。 如果為 NULL,則對話方塊的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

要顯示對話框,請調用[DoModal](#domodal)函數。

有關詳細資訊,請參閱[CLSID 密鑰](/windows/win32/com/clsid-key-hklm)和[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)結構。

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvert對話::DoConvert

呼叫此函數,從[DoModal](#domodal)成功傳回後,以轉換或啟動[COleClientItem](../../mfc/reference/coleclientitem-class.md)類型的物件。

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要轉換或啟動的專案。 不能是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

根據使用者在「轉換」對話框中選擇的資訊轉換或啟動該專案。

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvert對話::Do模態

呼叫此函數以顯示"OLE 轉換"對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話框的完成狀態。 下列其中一個值：

- 如果對話框已成功顯示,則 IDOK。

- 如果使用者取消了對話框,則進行 IDCANCEL。

- 如果發生錯誤,則 IDABORT。 如果返回 IDABORT,請呼叫[COleDialog:getLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函數,以獲取有關所發生錯誤類型的詳細資訊。 有關可能錯誤的清單,請參閱 Windows SDK 中的[OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw)函數。

### <a name="remarks"></a>備註

如果要通過設置[m_cv](#m_cv)結構的成員來初始化各種對話框控件,則應在調用`DoModal`之前執行此操作,但在構造對話框物件之後。

如果`DoModal`返回 IDOK,則可以調用其他成員函數來檢索使用者輸入到對話方塊中的設置或資訊。

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvert 對話:取得類別ID

呼叫此函數以取得與使用者在"轉換"對話框中選擇的項關聯的 CLSID。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>傳回值

與"轉換"對話框中選擇的項關聯的 CLSID。

### <a name="remarks"></a>備註

僅在[DoModal](#domodal)傳回 IDOK 後呼叫此函數。

關於詳細資訊,請參閱 Windows SDK 中的[CLSID 金鑰](/windows/win32/com/clsid-key-hklm)。

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvert對話::取得繪製方面

呼叫此函數以確定使用者是否選擇將選取項目顯示為圖示。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>傳回值

呈現物件所需的方法。

- 如果未選中「顯示為圖示」複選框,則DVASPECT_CONTENT返回。

- DVASPECT_ICON如果選中「顯示為圖示」複選框,則返回。

### <a name="remarks"></a>備註

僅在[DoModal](#domodal)傳回 IDOK 後呼叫此函數。

有關繪圖方面的詳細資訊,請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)資料結構。

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvert 對話:取得圖示Meta檔案

呼叫此函數以獲取包含所選項標誌性方面的元檔的句柄。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含選定項目標誌性方面的元檔的句柄,如果通過選擇「確定」在對話框被取消時選中「顯示為圖示」複選框;否則 NULL。

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvert 對話:取得選擇類型

呼叫此函數以確定在"轉換"對話框中選擇的轉換類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

選擇的類型。

### <a name="remarks"></a>備註

返回類型值由類中聲明的`Selection``COleConvertDialog`枚舉類型指定。

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

這些值的簡要說明如下:

- `COleConvertDialog::noConversion`如果對話框已取消或使用者未選擇轉換,則返回。 如果`COleConvertDialog::DoModal`返回 IDOK,則使用者可能選擇了與以前選擇的圖示不同的圖示。

- `COleConvertDialog::convertItem`如果選中「轉換為單選」按鈕,則返回該用戶選擇了要轉換為的不同專案,並`DoModal`返回 IDOK。

- `COleConvertDialog::activateAs`如果選中"激活作為單選"按鈕,則返回該用戶選擇要啟動的不同專案,並`DoModal`返回 IDOK。

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a>COleConvert對話::m_cv

用於控制「轉換」對話框的行為的 OLEUICONVERT 類型的結構。

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>備註

此結構的成員可以直接或通過成員函數進行修改。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)結構。

## <a name="see-also"></a>另請參閱

[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
