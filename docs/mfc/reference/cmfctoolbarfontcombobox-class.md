---
title: CMFCToolBarFontComboBox 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 7b31f4b725a6983171162d9805d08224ad787808
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360457"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 類別

包含組合框控制項的工具列按鈕,使用戶能夠從系統字型清單中選擇字型。

## <a name="syntax"></a>語法

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarFontBox:CMFCToolBarFontCombox](#cmfctoolbarfontcombobox)|建構 `CMFCToolBarFontComboBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarFontComboBox::獲取豐得斯克](#getfontdesc)|返回指向組合框中指定`CMFCFontInfo`索引對象的指標。|
|[CMFCToolBarFontBox::SetFont](#setfont)|根據字型的名稱或字型的首碼和字元集在字體組合框中選擇字型。|

### <a name="data-members"></a>資料成員

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
字型組合框中字元的高度。

## <a name="remarks"></a>備註

要向工具列添加字型組合框按鈕,請按照以下步驟操作:

1. 為父工具列資源的按鈕保留假的資源 ID。

1. 構造`CMFCToolBarFontComboBox`物件。

1. 在處理AFX_WM_RESETTOOLBAR消息的消息處理程式中,使用[CMFCToolBar:::替換Button,](../../mfc/reference/cmfctoolbar-class.md#replacebutton)將原始按鈕替換為新的組合框按鈕。

1. 使用[CMFCToolBarFontCombox::setFont](#setfont)方法,將組合框中選擇的字體與文檔中的字體同步。

若要將文件的字體與組合框中選擇的字體同步,請使用[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)方法檢索所選字體的屬性,並使用這些屬性創建[CFont 類](../../mfc/reference/cfont-class.md)物件。

字體組合框按鈕調用 Win32 功能[EnumFontSeEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw)以確定系統可用的螢幕和印表機字型。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComBox按鈕](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>需求

**標題:** afxtoolbarfontcombox.h

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontBox:CMFCToolBarFontCombox

建構[CMFCToolBarFontCombox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)物件。

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]組合框的命令 ID。

*i 影像*<br/>
[在]工具欄圖像的零基索引。 圖像位於[CMFCToolBar 類](../../mfc/reference/cmfctoolbar-class.md)維護的[CMFCToolBar 圖像類](../../mfc/reference/cmfctoolbarimages-class.md)物件中。

*n 字型型別*<br/>
[在]組合框包含的字體類型。 這裡可以是以下值的組合 (布林或):

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[在]如果設置為DEFAULT_CHARSET,組合框包含所有字元集中的所有唯一命名字體。 (如果有兩個具有相同名稱的字體,則組合框包含其中一種字體。如果設置為有效的字元集值,組合框僅包含指定字元集中的字體。 有關可能的字元集的清單,請參閱[LOGFONT。](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*dwStyle*<br/>
[在]組合框的樣式。 ( 請參考[組合盒樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
[在]編輯控制項的寬度(以像素為單位)。

*n 皮奇和家庭*<br/>
[在]如果設置為DEFAULT_PITCH,組合框包含字體,而不考慮間距。 如果設置為FIXED_PITCH或VARIABLE_PITCH,組合框僅包含具有該間距類型的字體。 當前不支援基於字體系列進行篩選。

*pLstFonts 外部*<br/>
[出]指向存儲可用字體的[CObList 類](../../mfc/reference/coblist-class.md)物件的指標。

### <a name="remarks"></a>備註

通常,`CMFCToolBarFontComboBox`物件將可用字型清單存儲在單個`CObList`共用 物件中。 如果使用建構函數的第二個重載並提供指向*pLstFonts 外部*的有效指標,則`CMFCToolBarFontComboBox`該 物件將改為用可用`CObList`字體 填充該*pLstFonts 外部*點。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCToolBarFontComboBox`物件。 此程式碼片段是 [WordPad 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox::獲取豐得斯克

返回指向組合框中指定`CMFCFontInfo`索引對象的指標。

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]指定組合框項的零基索引。

### <a name="return-value"></a>傳回值

`CMFCFontInfo` 物件的指標。 如果*iIndex*未指定有效的物料索引,則返回值為 NULL。

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

如果組合框具有擁有者繪製樣式,則指定字體組合框中字元的高度(以像素為單位)。

```
static int m_nFontHeight
```

### <a name="remarks"></a>備註

如果`m_nFontHeight`變數為 0,則根據組合框的預設字體自動計算高度。 高度包括基線上方的字元上升和基線下方字元的下降。

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontBox::SetFont

根據參數中指定的字型名稱和字元集選擇字體組合框中的字型。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
[在]指定字型名稱或前置字串。

*nCharSet*<br/>
[在]指定字元集。

*b精確*<br/>
[在]指定*lpszName*是否包含字型名稱還是字型前置碼。

### <a name="return-value"></a>傳回值

如果已成功選擇字體,則非零;否則 0。

### <a name="remarks"></a>備註

如果*bExact*為 TRUE,則此方法將選擇與您指定為*lpszName*的名稱完全符合的字型。 如果*bExact*是 FALSE,則此方法選擇以指定為*lpszName*的文字開頭並使用指定為*nCharSet*的字元集的字型。 如果*nCharSet*設定為DEFAULT_CHARSET,則字元集將被忽略,並且將僅使用*lpszName*來選擇字型。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFC工具列:更換按鈕](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
