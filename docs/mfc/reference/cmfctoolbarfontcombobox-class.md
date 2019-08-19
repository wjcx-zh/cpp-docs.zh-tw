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
ms.openlocfilehash: 7e19fc9257c1fe986ff09a8bbc86bf2fb55af7ee
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504737"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 類別

包含下拉式方塊控制項的工具列按鈕, 可讓使用者從系統字型清單中選取字型。

## <a name="syntax"></a>語法

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|建構 `CMFCToolBarFontComboBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|傳回下拉式方塊中指定`CMFCFontInfo`索引之物件的指標。|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|根據字型的名稱或字型的前置詞和字元集, 在 [字型] 下拉式方塊中選取字型。|

### <a name="data-members"></a>資料成員

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
字型下拉式方塊中的字元高度。

## <a name="remarks"></a>備註

若要將字型下拉式方塊按鈕新增至工具列, 請依照下列步驟執行:

1. 為父工具列資源的按鈕保留假的資源 ID。

1. `CMFCToolBarFontComboBox`建立物件。

1. 在處理 AFX_WM_RESETTOOLBAR 訊息的訊息處理常式中, 使用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton), 將原始按鈕取代為新的下拉式方塊按鈕。

1. 使用[CMFCToolBarFontComboBox:: SetFont](#setfont)方法, 將下拉式方塊中所選取的字型與檔中的字型同步。

若要將檔的字型與下拉式方塊中選取的字型同步, 請使用[CMFCToolBarFontComboBox:: GetFontDesc](#getfontdesc)方法來抓取所選字型的屬性, 並使用這些屬性來建立[CFont 類別](../../mfc/reference/cfont-class.md)物件。

[字型] 下拉式方塊按鈕會呼叫 Win32 函數[EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) , 以判斷可供系統使用的螢幕和印表機字型。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>需求

**標頭:** afxtoolbarfontcombobox。h

##  <a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

結構[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)物件。

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
在下拉式方塊的命令識別碼。

*iImage*<br/>
在工具列影像之以零為起始的索引。 影像位於[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別所維護的[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件中。

*nFontType*<br/>
在下拉式方塊包含的字型類型。 這個參數可以是下列值的組合 (布林值或):

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
在如果設定為 DEFAULT_CHARSET, 下拉式方塊就會包含所有字元集中所有唯一命名的字型。 (如果有兩個具有相同名稱的字型, 則下拉式方塊會包含其中一個字型)。如果設定為有效的字元集值, 下拉式方塊只會包含指定字元集中的字型。 如需可能的字元集清單, 請參閱[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 。

*dwStyle*<br/>
在下拉式方塊的樣式。 (請參閱[下拉式方塊樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
在編輯控制項的寬度 (以圖元為單位)。

*nPitchAndFamily*<br/>
在如果設定為 DEFAULT_PITCH, 下拉式方塊就會包含字型, 而不論音調為何。 如果設定為 FIXED_PITCH 或 VARIABLE_PITCH, 下拉式方塊只會包含具有該音調類型的字型。 目前不支援根據字型系列進行篩選。

*pLstFontsExternal*<br/>
脫銷[CObList 類別](../../mfc/reference/coblist-class.md)物件的指標, 它會儲存可用的字型。

### <a name="remarks"></a>備註

通常, `CMFCToolBarFontComboBox`物件會將可用的字型清單儲存在單一共用`CObList`物件中。 如果您使用此函式的第二個多載, 並提供有效的指標`CMFCToolBarFontComboBox`給 pLstFontsExternal, 該物件`CObList`將會改為填滿*pLstFontsExternal*指向具有可用字型的。

### <a name="example"></a>範例

下列範例示範如何建立`CMFCToolBarFontComboBox`物件。 此程式碼片段是 [WordPad 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

傳回下拉式方塊中指定`CMFCFontInfo`索引之物件的指標。

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在指定下拉式方塊專案以零為基底的索引。

### <a name="return-value"></a>傳回值

          `CMFCFontInfo` 物件的指標。 如果*iIndex*未指定有效的專案索引, 則傳回值會是 Null。

##  <a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

指定如果下拉式方塊具有擁有者繪製樣式, 則字型下拉式方塊中的字元高度 (以圖元為單位)。

```
static int m_nFontHeight
```

### <a name="remarks"></a>備註

`m_nFontHeight`如果變數為 0, 則高度會根據下拉式方塊的預設字型自動計算。 高度包括高於基準的字元上升, 以及基準底下的字元下降。

##  <a name="setfont"></a>CMFCToolBarFontComboBox::SetFont

根據參數中指定的字型名稱和字元集, 選取 [字型] 下拉式方塊中的字型。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
在指定字型名稱或前置詞。

*nCharSet*<br/>
在指定字元集。

*bExact*<br/>
在指定*lpszName*是否包含字型名稱或字型前置詞。

### <a name="return-value"></a>傳回值

如果已成功選取字型, 則為非零;否則為0。

### <a name="remarks"></a>備註

如果*bExact*為 TRUE, 則這個方法會選取與您指定為*lpszName*的名稱完全相符的字型。 如果*bExact*為 FALSE, 這個方法會選取以指定為*lpszName*的文字開頭的字型, 並使用您指定為*nCharSet*的字元集。 如果*nCharSet*設定為 DEFAULT_CHARSET, 則會忽略字元集, 而且只會使用*lpszName*來選取字型。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 類別](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
