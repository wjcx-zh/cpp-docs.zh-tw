---
title: CMFCFontComboBox 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: 60b4b7cdfdace2332de35dd93c43eacf592e99e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367496"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox 類別

類別`CMFCFontComboBox`建立一個包含字型清單的組合框控制項。

## <a name="syntax"></a>語法

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC方康博盒:CMFC方康博盒](#cmfcfontcombobox)|建構 `CMFCFontComboBox` 物件。|
|`CMFCFontComboBox::~CMFCFontComboBox`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|由框架調用以確定當前字體組合框控制項的排序表框中新項目的相對位置。 (覆蓋[CComboBox:比較專案](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|由框架呼叫以在當前字型組合框控制項中繪製指定項。 (覆蓋[CComboBox::D原始專案](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFC方康博盒::獲取塞爾方特](#getselfont)|檢索有關當前所選字體的資訊。|
|`CMFCFontComboBox::MeasureItem`|由框架呼叫,以通知 Windows 當前字型組合框控制項中列表框的尺寸。 (覆寫[CComboBox:測量項目](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|在視窗訊息發送到[翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗功能之前進行翻譯。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFC方博博信箱::選擇字體](#selectfont)|從字體組合框中選擇與指定條件匹配的字體。|
|[CMFCFontCombox:設定](#setup)|初始化字型組合框中的項目清單。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCFontComboBox:m_bDrawUsingFont](#m_bdrawusingfont)|指示框架在當前字體組合框中用於繪製項目標籤的字體。|

## <a name="remarks"></a>備註

要在`CMFCFontComboBox`對話方塊中使用物件,向對話方塊`CMFCFontComboBox`類添加變數。 然後在對話方塊`OnInitDialog`類的方法中,調用[CMFCFontCombox::設定](#setup)方法以初始化組合框控制項中的項清單。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>需求

**標題:** afxfontcombox.h

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a>CMFC方康博盒:CMFC方康博盒

建構 `CMFCFontComboBox` 物件。

```
CMFCFontComboBox();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a>CMFC方康博盒::獲取塞爾方特

檢索有關當前所選字體的資訊。

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>傳回值

指向[CMFCFontInfo 類](../../mfc/reference/cmfcfontinfo-class.md)物件的指標,用於描述字型。 如果在組合框中未選擇字型,則可以為 NULL。

### <a name="remarks"></a>備註

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a>CMFCFontComboBox:m_bDrawUsingFont

指示框架在當前字體組合框中用於繪製項目標籤的字體。

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>備註

將此成員設置為 TRUE 以指示框架使用相同的字體繪製每個項目標籤。 將此成員設置為 FALSE,以指示框架使用名稱與標籤相同的字體繪製每個項目標籤。 此成員的預設值為 FALSE。

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a>CMFC方博博信箱::選擇字體

從字體組合框中選擇與指定條件匹配的字體。

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>參數

*pDesc*<br/>
[在]指向字體描述物件。

*lpsz名稱*<br/>
[在]指定字型名稱。

*nCharSet*<br/>
[在]指定字元集。 默認值為DEFAULT_CHARSET。 有關詳細資訊,請參閱`lfCharSet`[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的成員。

### <a name="return-value"></a>傳回值

如果字體組合框中的項目與指定的字體描述物件或字體名稱和字元集匹配,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

使用此方法可以選擇並滾動到字體組合框中對應於指定字體的專案。

### <a name="example"></a>範例

下面的示例演示如何在`SelectFont``CMFCFontComboBox`類中使用 方法。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a>CMFCFontCombox:設定

初始化字型組合框中的項目清單。

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>參數

*n 字型型別*<br/>
[在]指定字型類型。 默認值是DEVICE_FONTTYPE、RASTER_FONTTYPE和TRUETYPE_FONTTYPE的位組合 (OR)。

*nCharSet*<br/>
[在]指定字型字元集。 默認值為DEFAULT_CHARSET。

*n 皮奇和家庭*<br/>
[在]指定字體間距和族。 默認值為DEFAULT_PITCH。

### <a name="return-value"></a>傳回值

如果字體組合框已成功初始化,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法通過枚舉目前安裝的與指定參數匹配的字體並在字體組合框中插入這些字體名稱來初始化字體組合框。

### <a name="example"></a>範例

下面的示例演示如何在`Setup``CMFCFontComboBox`類中使用 方法。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo 類別](../../mfc/reference/cmfcfontinfo-class.md)
