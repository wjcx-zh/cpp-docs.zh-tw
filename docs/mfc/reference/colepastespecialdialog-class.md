---
title: COlePaste 特殊對話類
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
ms.openlocfilehash: 5e67a81f48b8cdf0dae6dc90fc2ded8dc44a73ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376980"
---
# <a name="colepastespecialdialog-class"></a>COlePaste 特殊對話類

用於 OLE 的 [選擇性貼上] 對話方塊。

## <a name="syntax"></a>語法

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COlePaste 特殊對話::COlePaste 特殊對話](#colepastespecialdialog)|建構 `COlePasteSpecialDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COlePaste 特別對話::添加格式](#addformat)|將自訂格式添加到應用程式可以貼上的格式清單中。|
|[COlePaste 特殊對話::添加連結輸入](#addlinkentry)|向受支援的剪貼簿格式清單添加新條目。|
|[COlePaste 特別對話::添加標準格式](#addstandardformats)|將CF_BITMAP、CF_DIB、CF_METAFILEPICT以及可選CF_LINKSOURCE添加到應用程式可以貼上的格式清單中。|
|[COlePaste 特殊對話::創建專案](#createitem)|使用指定的格式在容器文件中創建項。|
|[COlePaste特殊對話::Do模態](#domodal)|顯示"OLE 貼貼特殊"對話框。|
|[COlePaste 特別對話::獲取繪製Aspect](#getdrawaspect)|是否將項目繪製為圖示。|
|[COlePaste 特別對話::獲取圖示Meta檔](#geticonicmetafile)|獲取與此項目的標誌性形式關聯的元檔的句柄。|
|[COlePaste 特別對話::獲取粘貼索引](#getpasteindex)|獲取使用者選擇的可用粘貼選項的索引。|
|[COlePaste 特殊對話::獲取選擇類型](#getselectiontype)|獲取所選選擇的類型。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COlePaste 特別對話::m_ps](#m_ps)|控制對話方塊功能的 OLEUIPASTE 特別類型的結構。|

## <a name="remarks"></a>備註

要呼叫此對話方塊`COlePasteSpecialDialog`時 ,請創建類的物件。 建構`COlePasteSpecialDialog`物件後,可以使用[AddFormat](#addformat)和[AddStandard格式](#addstandardformats)成員函數將剪貼簿格式添加到對話方塊中。 您還可以使用[m_ps](#m_ps)結構在對話框中初始化控制項的值或狀態。 結構`m_ps`為「奧萊圖斯特」 型。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIPASTE 特別](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw)結構。

有關特定於 OLE 的對話方塊的詳細資訊,請參閱 OLE[中的「對話框](../../mfc/dialog-boxes-in-ole.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>需求

**標題:** afxodlgs.h

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a>COlePaste 特別對話::添加格式

呼叫此函數以將新格式添加到應用程式在 Paste 特殊操作中可以支援的格式清單中。

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

*Fmt*<br/>
引用要添加的數據類型。

*lpsz格式*<br/>
向使用者描述格式的字串。

*lpszResult*<br/>
如果在對話框中選擇此格式,則描述結果的字串。

*標誌*<br/>
可用於此格式的不同連結和嵌入選項。 此標誌是 OLEUIPASTEFLAG 枚舉類型中一個或多個不同值的位形組合。

*cf*<br/>
要添加的剪貼簿格式。

*泰梅德*<br/>
此格式可用的媒體類型。 這是 TYMED 枚舉類型中一個或多個值的位組合。

*nFormatID*<br/>
識別此格式的字串的識別碼。 此字串的格式是兩個單獨的字串,由"\n"字元分隔。 第一個字串與*lpstrFormat*參數中傳遞的字串相同,第二個字串與*lpstrResult*參數相同。

*bEnableIcon*<br/>
在清單框中選擇此格式時確定是否啟用「顯示為圖示」複選框的標誌。

*眨眼*<br/>
在清單框中選擇此格式時確定是否啟用「貼上連結」單選按鈕的標誌。

### <a name="remarks"></a>備註

可以調用此功能來添加標準格式,如CF_TEXT或CF_TIFF或自定義格式,應用程式已在系統中註冊。 有關將資料物件粘貼到應用程式中的詳細資訊,請參閱文章[「數據物件和數據源:操作](../../mfc/data-objects-and-data-sources-manipulation.md)」。。

有關詳細資訊,請參閱 Windows SDK 中的[TYMED](/windows/win32/api/objidl/ne-objidl-tymed)枚舉類型和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)枚舉類型。

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a>COlePaste 特殊對話::添加連結輸入

向受支援的剪貼簿格式清單添加新條目。

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
要添加的剪貼簿格式。

### <a name="return-value"></a>傳回值

包含新連結項目資訊的[OLEUIPASTEFLAG 結構](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)。

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a>COlePaste 特別對話::添加標準格式

呼叫此函數會將剪貼簿格式加入應用程式在貼上特殊操作中可以支援的格式清單中:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用連結*<br/>
確定是否將CF_LINKSOURCE添加到應用程式可以貼上的格式清單中的標誌。

### <a name="remarks"></a>備註

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"嵌入物件"**

- ( 選擇性的 )**連結源"**

這些格式用於支援嵌入和連結。

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a>COlePaste 特殊對話::COlePaste 特殊對話

建構 `COlePasteSpecialDialog` 物件。

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
建立標誌,包含使用位-OR 運算子組合的以下標誌的任意數量的:

- PSF_SELECTPASTE 指定在調用對話方塊時,最初將選中「貼貼單選」按鈕。 不能與PSF_SELECTPASTELINK結合使用。 這是預設值。

- PSF_SELECTPASTELINK 指定在調用對話方塊時,最初將選中"粘貼連結"單選按鈕。 不能與PSF_SELECTPASTE結合使用。

- PSF_CHECKDISPLAYASICON 指定在調用對話方塊時,將首先選中"顯示為圖示"複選框。

- PSF_SHOWHELP 指定在調用對話框時將顯示"説明"按鈕。

*pDataObject*<br/>
指向用於貼上的[COleData 物件](../../mfc/reference/coledataobject-class.md)。 如果這個值為 NULL,則從`COleDataObject`剪 貼簿抓取 。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件`CWnd`(類型)。 如果為 NULL,則對話方塊的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

此函數只建構物件`COlePasteSpecialDialog`。 要顯示對話框,請調用[DoModal](#domodal)函數。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag)枚舉類型。

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a>COlePaste 特殊對話::創建專案

建立在「貼貼特殊」對話框中選擇的新項。

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>參數

*p 新專案*<br/>
指向實體`COleClientItem`。 不能是 NULL。

### <a name="return-value"></a>傳回值

如果專案已成功創建,則非零;否則 0。

### <a name="remarks"></a>備註

只有在[DoModal](#domodal)傳回 IDOK 後才能呼叫此功能。

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a>COlePaste特殊對話::Do模態

顯示"OLE 貼貼特殊"對話框。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

對話框的完成狀態。 下列其中一個值：

- 如果對話框已成功顯示,則 IDOK。

- 如果使用者取消了對話框,則進行 IDCANCEL。

- 如果發生錯誤,則 IDABORT。 如果返回 IDABORT,請調`COleDialog::GetLastError`用 成員函數以獲取有關所發生錯誤類型的詳細資訊。 有關可能錯誤的清單,請參閱 Windows SDK 中的[OleUIPaste 特別](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw)功能。

### <a name="remarks"></a>備註

如果要通過設置[m_ps](#m_ps)結構的成員來初始化各種對話框控件,則應在`DoModal`調用 之前執行此操作,但在構造對話框物件之後。

如果`DoModal`返回 IDOK,則可以調用其他成員函數來檢索使用者輸入到對話方塊中的設置或資訊。

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COlePaste 特別對話::獲取繪製Aspect

確定使用者是否選擇將所選項目顯示為圖示。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>傳回值

呈現物件所需的方法。

- DVASPECT_CONTENT如果對話框已取消時未選中「顯示為圖示」複選框,則返回。

- DVASPECT_ICON在對話方塊取消時選中"顯示為圖示"複選框時返回。

### <a name="remarks"></a>備註

僅在[DoModal](#domodal)傳回 IDOK 後呼叫此函數。

有關繪圖方面的詳細資訊,請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構。

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COlePaste 特別對話::獲取圖示Meta檔

獲取與使用者選擇的專案關聯的元檔。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>傳回值

包含選定項目標誌性方面的元檔的句柄,如果選擇「顯示為圖示」複選框,則對話框通過選擇 **「確定**」而取消;否則 NULL。

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a>COlePaste 特別對話::獲取粘貼索引

獲取與使用者所選條目關聯的索引值。

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>傳回值

用戶選擇的結構陣列中的`OLEUIPASTEENTRY`索引。 執行粘貼操作時,應使用對應於所選索引的格式。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIPASTEENTRY 結構](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw)。

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a>COlePaste 特殊對話::獲取選擇類型

確定使用者所做的選擇類型。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>傳回值

返回所做的選擇類型。

### <a name="remarks"></a>備註

返回類型值由類中聲明的`Selection``COlePasteSpecialDialog`枚舉類型指定。

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

這些值的簡短去功能如下:

- `COlePasteSpecialDialog::pasteLink`已選中「貼上」 選單選按鈕,選取格式為標準 OLE 格式。

- `COlePasteSpecialDialog::pasteNormal`已選擇「貼單選」按鈕,選取格式為標準 OLE 格式。

- `COlePasteSpecialDialog::pasteOther`所選格式不是標準 OLE 格式。

- `COlePasteSpecialDialog::pasteStatic`所選格式為元檔。

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a>COlePaste 特別對話::m_ps

用於控制粘貼特殊對話框的行為的 OLEUIPASTE 特別類型的結構。

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>備註

此結構的成員可以直接或通過成員函數進行修改。

有關詳細資訊,請參閱 Windows SDK 中的[OLEUIPASTE 特別](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw)結構。

## <a name="see-also"></a>另請參閱

[MFC 樣品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDialog 類別](../../mfc/reference/coledialog-class.md)
