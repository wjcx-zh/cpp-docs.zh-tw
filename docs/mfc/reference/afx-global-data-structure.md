---
title: AFX_GLOBAL_DATA 結構
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: dda3056cbed18ef93e09b52cd9d0a6b00e1db177
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420586"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA 結構

`AFX_GLOBAL_DATA` 結構包含的欄位和方法，用於管理架構，或自訂應用程式外觀和行為。

## <a name="syntax"></a>語法

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|建構 `AFX_GLOBAL_DATA` 結構。|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[AFX_GLOBAL_DATA：：清除](#cleanup)|釋出架構配置的資源，例如筆刷、字型和 DLL。|
|[AFX_GLOBAL_DATA：:D 2D1MakeRotateMatrix](#d2d1makerotatematrix)|建立環繞指定點依特定角度旋轉的旋轉轉換。|
|[AFX_GLOBAL_DATA：:D rawParentBackground](#drawparentbackground)|在指定的區域中繪製控制項父代的背景。|
|[AFX_GLOBAL_DATA：:D rawTextOnGlass](#drawtextonglass)|以指定佈景主題的視覺化樣式繪製指定文字。|
|[AFX_GLOBAL_DATA：： ExcludeTag](#excludetag)|從指定的緩衝區中移除指定的 XML 標記組。|
|[AFX_GLOBAL_DATA：： GetColor](#getcolor)|擷取指定的使用者介面項目目前的色彩。|
|[AFX_GLOBAL_DATA：： GetDirect2dFactory](#getdirect2dfactory)|傳回儲存在全域資料中的 `ID2D1Factory` 介面指標。 介面若未初始化，就會建立介面並設定預設參數。|
|[AFX_GLOBAL_DATA：： GetHandCursor](#gethandcursor)|擷取預先定義的資料指標，它有類似手掌的形狀，且識別項是 `IDC_HAND`。|
|[AFX_GLOBAL_DATA：： GetITaskbarList](#getitaskbarlist)|在全域資料中建立和儲存 ITaskBarList 介面的指標。|
|[AFX_GLOBAL_DATA：： GetITaskbarList3](#getitaskbarlist3)|在全域資料中建立和儲存 ITaskBarList3 介面的指標。|
|[AFX_GLOBAL_DATA：： GetNonClientMetrics](#getnonclientmetrics)|擷取與非最小化視窗之非工作區相關聯的度量。|
|[AFX_GLOBAL_DATA：： GetShellAutohideBars](#getshellautohidebars)|決定殼層自動隱藏軸的位置。|
|[AFX_GLOBAL_DATA：： GetTextHeight](#gettextheight)|擷取目前字型的文字字元高度。|
|[AFX_GLOBAL_DATA：： GetWICFactory](#getwicfactory)|傳回儲存在全域資料中的 `IWICImagingFactory` 介面指標。 介面若未初始化，就會建立介面並設定預設參數。|
|[AFX_GLOBAL_DATA：： GetWriteFactory](#getwritefactory)|傳回儲存在全域資料中的 `IDWriteFactory` 介面指標。 介面若未初始化，就會建立介面並設定預設參數。|
|[AFX_GLOBAL_DATA：： IsD2DInitialized](#isd2dinitialized)|初始化 `D2D`、 `DirectWrite`和 `WIC` Factory。 初始化主視窗之前先呼叫這個方法。|
|[AFX_GLOBAL_DATA：： Is32BitIcons](#is32biticons)|指出是否支援預先定義的 32 位元圖示。|
|[AFX_GLOBAL_DATA：： IsD2DInitialized](#isd2dinitialized)|判斷是否已初始化 `D2D` 。|
|[AFX_GLOBAL_DATA：： IsDwmCompositionEnabled](#isdwmcompositionenabled)|提供呼叫 Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) 方法的簡單方式。|
|[AFX_GLOBAL_DATA：： IsHighContrastMode](#ishighcontrastmode)|指出目前是否以高對比顯示圖像。|
|[AFX_GLOBAL_DATA：： OnSettingChange](#onsettingchange)|偵測到桌面功能表動畫和工作列自動隱藏功能的目前狀態。|
|[AFX_GLOBAL_DATA：： RegisterWindowClass](#registerwindowclass)|註冊指定的 MFC 視窗類別。|
|[AFX_GLOBAL_DATA：： ReleaseTaskBarRefs](#releasetaskbarrefs)|釋出透過 GetITaskbarList 和 GetITaskbarList3 方法取得的介面。|
|[AFX_GLOBAL_DATA：： Resume](#resume)|重新初始化內部函式指標，存取支援 Windows [Themes and Visual Styles](/windows/win32/Controls/visual-styles-overview)(佈景主題和視覺化樣式) 的方法。|
|[AFX_GLOBAL_DATA：： SetLayeredAttrib](#setlayeredattrib)|提供呼叫 Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) 方法的簡單方法。|
|[AFX_GLOBAL_DATA：： SetMenuFont](#setmenufont)|建立指定的邏輯字型。|
|[AFX_GLOBAL_DATA：： ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|從剖析名稱建立並初始化殼層項目物件。|
|[AFX_GLOBAL_DATA：： UpdateFonts](#updatefonts)|重新初始化架構使用的邏輯字型。|
|[AFX_GLOBAL_DATA：： UpdateSysColors](#updatesyscolors)|初始化架構使用的色彩、色彩深度、筆刷、畫筆與圖像。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[AFX_GLOBAL_DATA：： EnableAccessibilitySupport](#enableaccessibilitysupport)|啟用或停用 Microsoft Active Accessibility 支援。 Active Accessibility 提供可靠的方法以公開使用者介面項目的相關資訊。|
|[AFX_GLOBAL_DATA：： IsAccessibilitySupport](#isaccessibilitysupport)|指出是否已啟用 Microsoft Active Accessibility 支援。|
|[AFX_GLOBAL_DATA：： IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|指出作業系統是否支援層疊的視窗。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[AFX_GLOBAL_DATA：： bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|指出目前的作業系統是否支援 Alpha 混色。|
|[AFX_GLOBAL_DATA：： bIsWindows7](#biswindows7)|指出應用程式是在 Windows 7 作業系統或更高版本中執行。|
|[AFX_GLOBAL_DATA：： clrActiveCaptionGradient](#clractivecaptiongradient)|指定現用標題的漸層色彩。 通常用於停駐窗格。|
|[AFX_GLOBAL_DATA：： clrInactiveCaptionGradient](#clrinactivecaptiongradient)|指定非作用中現用標題的漸層色彩。 通常用於停駐窗格。|
|[AFX_GLOBAL_DATA：： m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|指出架構使用預先定義的 32 位元色彩圖示或較低解析度的圖示。|
|[AFX_GLOBAL_DATA：： m_bUseSystemFont](#m_busesystemfont)|指出功能表、工具列和功能區是否使用系統字型。|
|[AFX_GLOBAL_DATA：： m_hcurHand](#m_hcurhand)|儲存手型游標的控制代碼。|
|[AFX_GLOBAL_DATA：： m_hcurStretch](#m_hcurstretch)|儲存水平延展游標的控制代碼。|
|[AFX_GLOBAL_DATA：： m_hcurStretchVert](#m_hcurstretchvert)|儲存垂直延展游標的控制代碼。|
|[AFX_GLOBAL_DATA：： m_hiconTool](#m_hicontool)|儲存工具圖示的控制代碼。|
|[AFX_GLOBAL_DATA：： m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|指定從最左邊的自動隱藏工具列到停駐列左邊的位移。|
|[AFX_GLOBAL_DATA：： m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|指定自動隱藏工具列之間的間距。|
|[AFX_GLOBAL_DATA：： m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|指定溝通停駐狀態所使用的拖曳框架粗細。|
|[AFX_GLOBAL_DATA：： m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|指定溝通浮動狀態所使用的拖曳框架粗細。|

### <a name="remarks"></a>備註

`AFX_GLOBAL_DATA` 結構的大部分資料是在應用程式啟動時初始化。

### <a name="inheritance-hierarchy"></a>繼承階層

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>需求

**Header:** afxglobals.h

## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA：： bIsOSAlphaBlendingSupport

指出作業系統是否支援 Alpha 混色。

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>備註

TRUE 表示支援 Alpha 混色;否則為 FALSE。

## <a name="cleanup"></a>AFX_GLOBAL_DATA：：清除

釋出架構配置的資源，例如筆刷、字型和 DLL。

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA：:D 2D1MakeRotateMatrix

建立環繞指定點依特定角度旋轉的旋轉轉換。

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>參數

*正切*<br/>
順時針旋轉角度 (以度數為單位)。

*核心*<br/>
要旋轉的點。

*核准*<br/>
當這個方法傳回時，會包含新的旋轉轉換。 您必須配置此參數的儲存體。

### <a name="return-value"></a>傳回值

如果成功，則會傳回 S_OK，否則會傳回錯誤值。

## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA：:D rawParentBackground

在指定的區域中繪製控制項父代的背景。

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
在控制項視窗的指標。

*pDC*<br/>
在裝置內容的指標。

*lpRect*<br/>
在矩形的指標，範圍為要繪製的區域。 預設值為 NULL。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA：:D rawTextOnGlass

以指定佈景主題的視覺化樣式繪製指定文字。

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>參數

*hTheme*<br/>
在視窗主題資料的控制碼，或為 Null。 如果此參數不是 Null，而且支援主題，則此架構會使用指定的主題來繪製文字。 否則，此架構不會使用佈景主題來繪製文字。

使用[OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata)方法來建立 HTHEME。

*pDC*<br/>
在裝置內容的指標。

*iPartId*<br/>
在具有所需文字外觀的控制群組件。 如需詳細資訊，請參閱 [Parts and States](/windows/win32/controls/parts-and-states)(組件和狀態) 表格中的 Parts 資料行。 如果此值為 0，則會使用預設字型來繪製文字；否則會使用裝置內容中所選取的字型。

*iStateId*<br/>
在具有所需文字外觀的控制項狀態。 如需詳細資訊，請參閱 [Parts and States](/windows/win32/controls/parts-and-states)(組件和狀態) 表格中的 States 資料行。

*strText*<br/>
在要繪製的文字。

*各種*<br/>
在要在其中繪製指定文字之區域的界限。

*dwFlags*<br/>
在旗標的位元組合（OR），指定如何繪製指定的文字。

如果 `NULL` *hTheme*參數，或如果不支援和啟用主題， [CDC：:D Rawtext](../../mfc/reference/cdc-class.md#drawtext)方法的*nFormat*參數會描述有效的旗標。 如果支援主題， [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)方法的*dwFlags*參數會描述有效的旗標。

*nGlowSize*<br/>
在在繪製指定文字之前繪製于背景上的光暈效果大小。 預設值為 0。

*clrText*<br/>
在繪製指定文字的色彩。 預設值為預設色彩。

### <a name="return-value"></a>傳回值

如果使用主題來繪製指定的文字，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

佈景主題會定義應用程式的視覺化樣式。 如果*hTheme*參數為 Null，或如果不支援[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)方法，或[桌面視窗管理員](/windows/win32/dwm/dwm-overview)（DWM）組合已停用，則不會使用主題來繪製文字。

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA：： EnableAccessibilitySupport

啟用或停用 Microsoft Active Accessibility 支援。

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示啟用協助工具支援;FALSE 表示停用協助工具支援。 預設值為 TRUE。

### <a name="remarks"></a>備註

Active Accessibility 是一種 COM 技術，可改善程式與 Windows 作業系統一起與輔助技術產品合作的方式。 它提供用於公開使用者介面項目資訊的可靠方法。 然而，現在已有稱為 Microsoft UI 自動化之較新協助工具模型可供使用。 如需這兩種技術的比較，請參閱[UI 自動化和 Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)。

使用[AFX_GLOBAL_DATA：： IsAccessibilitySupport](#isaccessibilitysupport)方法來判斷是否已啟用 Microsoft Active Accessibility 支援。

## <a name="excludetag"></a>AFX_GLOBAL_DATA：： ExcludeTag

從指定的緩衝區中移除指定的 XML 標記組。

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>參數

*strBuffer*<br/>
在文字的緩衝區。

*lpszTag*<br/>
在一對開頭和結尾 XML 標記的名稱。

*strTag*<br/>
脫銷當這個方法傳回時， *strTag*參數會包含在*lpszTag*參數所命名的開頭和結尾 XML 標記之間的文字。 任何開頭或尾端空白字元都會從結果中修剪。

*bIsCharsList*<br/>
在TRUE 會將*strTag*參數中的逸出字元符號轉換成實際的逸出字元;FALSE 表示不執行轉換。預設值為 FALSE。 如需詳細資訊，請參閱備註。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

XML 標記組是由命名的開頭和結束記號所組成，表示指定之緩衝區中的文字執行開始和結束。 *StrBuffer*參數會指定緩衝區，而*lpszTag*參數會指定 XML 標記的名稱。

使用下表中的符號，將指定之緩衝區中的一組逸出字元編碼。 針對*bIsCharsList*參數指定 TRUE，將*strTag*參數中的符號轉換成實際的逸出字元。 下表使用[_T （）](../../c-runtime-library/data-type-mappings.md)宏來指定符號和 escape 字元字串。

|符號|逸出字元|
|------------|----------------------|
|_T （"\\\t"）|_T （"\t"）|
|_T （"\\\n"）|_T （"\n"）|
|_T （"\\\r"）|_T （"\r"）|
|_T （"\\\b"）|_T （"\b"）|
|_T （"LT"）|_T （"\<"）|
|_T （"GT"）|_T （">"）|
|_T （"AMP"）|_T （"&"）|

## <a name="getcolor"></a>AFX_GLOBAL_DATA：： GetColor

擷取指定的使用者介面項目目前的色彩。

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>參數

*nColor*<br/>
在值，指定要取得其色彩的使用者介面專案。 如需有效值的清單，請參閱[GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)方法的*nIndex*參數。

### <a name="return-value"></a>傳回值

指定之使用者介面項目的 RGB 色彩值。 如需詳細資訊，請參閱備註。

### <a name="remarks"></a>備註

如果*nColor*參數超出範圍，則傳回值會是零。 由於零也是有效的 RGB 值，您無法使用這個方法來判斷目前的作業系統是否支援系統色彩。 相反地，請使用[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)方法，如果不支援色彩，則會傳回 Null。

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA：： GetDirect2dFactory

傳回儲存在全域資料中的 ID2D1Factory 介面指標。 介面若未初始化，就會建立介面並設定預設參數。

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>傳回值

如果建立 factory 成功，則為 ID2D1Factory 介面的指標，如果建立失敗或目前的作業系統沒有 D2D 支援，則為 Null。

## <a name="gethandcursor"></a>AFX_GLOBAL_DATA：： GetHandCursor

抓取與手類似的預先定義資料指標，且其識別碼為 IDC_HAND。

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>傳回值

手狀游標的控制代碼。

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA：： GetNonClientMetrics

擷取與非最小化視窗之非工作區相關聯的度量。

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>參數

*info*<br/>
[in、out][NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)結構，其中包含與非最小化視窗之非工作區相關聯的可擴充計量。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

## <a name="gettextheight"></a>AFX_GLOBAL_DATA：： GetTextHeight

擷取目前字型的文字字元高度。

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>參數

*bHorz*<br/>
在TRUE 表示水準執行文字時，取得字元的高度;FALSE 表示垂直執行文字時，取得字元的高度。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

目前字型的高度，從其 ascender 到下行的測量。

## <a name="getwicfactory"></a>AFX_GLOBAL_DATA：： GetWICFactory

傳回儲存在全域資料中的 IWICImagingFactory 介面指標。 介面若未初始化，就會建立介面並設定預設參數。

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>傳回值

如果建立 factory 成功，則為 IWICImagingFactory 介面的指標，如果建立失敗或目前的作業系統沒有 WIC 支援，則為 Null。

## <a name="getwritefactory"></a>AFX_GLOBAL_DATA：： GetWriteFactory

傳回儲存在全域資料中的 IDWriteFactory 介面指標。 介面若未初始化，就會建立介面並設定預設參數。

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>傳回值

如果建立 factory 成功，則為 IDWriteFactory 介面的指標，如果建立失敗或目前的作業系統沒有 DirectWrite 支援，則為 Null。

## <a name="initd2d"></a>AFX_GLOBAL_DATA：： InitD2D

初始化 D2D、DirectWrite 和 WIC factory。 初始化主視窗之前先呼叫這個方法。

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>參數

*d2dFactoryType*<br/>
D2D factory 的執行緒模型和它所建立的資源。

*writeFactoryType*<br/>
值，指定是否要共用或隔離寫入 factory 物件

### <a name="return-value"></a>傳回值

如果處理站已 intilalizrd，則傳回 TRUE，否則傳回 FALSE。

## <a name="is32biticons"></a>AFX_GLOBAL_DATA：： Is32BitIcons

指出是否支援預先定義的 32 位元圖示。

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>傳回值

如果支援預先定義的32點陣圖標，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果架構支援32位內建圖示，而且作業系統支援每圖元16位或以上，而且影像未以高對比顯示，則此方法會傳回 TRUE。

## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA：： IsAccessibilitySupport

指出是否已啟用 Microsoft Active Accessibility 支援。

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>傳回值

如果已啟用協助工具支援，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

Microsoft Active Accessibility 是過去用來讓應用程式成為可存取的方法。 Microsoft UI 自動化是 Microsoft Windows 的一種新的協助工具模型，能滿足輔助科技產品及自動化測試工具的需求。

使用[AFX_GLOBAL_DATA：： EnableAccessibilitySupport](#enableaccessibilitysupport)方法來啟用或停用 Active Accessibility 支援。

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA：： IsD2DInitialized

判斷 D2D 是否已初始化

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>傳回值

如果 D2D 已初始化，則為 TRUE;否則為 FALSE。

## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA：： IsDwmCompositionEnabled

提供呼叫 Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) 方法的簡單方式。

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>傳回值

如果已啟用[桌面視窗管理員](/windows/win32/dwm/dwm-overview)（DWM）組合，則為 TRUE;否則為 FALSE。

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA：： IsHighContrastMode

指出目前是否以高對比顯示圖像。
```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>傳回值

如果影像目前以黑色或白色高對比模式顯示，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

在黑色高對比模式中，朝光線的邊緣為白色，而背景為黑色。 在白色高對比模式中，朝光線的邊緣是黑色，而背景是白色。

## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA：： IsWindowsLayerSupportAvailable

指出作業系統是否支援層疊的視窗。

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>傳回值

如果支援分層視窗，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果支援分層視窗，*智慧型銜接*標記會使用分層視窗。

## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA：： m_bUseBuiltIn32BitIcons

指出架構使用預先定義的 32 位元色彩圖示或較低解析度的圖示。

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>備註

TRUE 指定架構使用32位色彩圖示;FALSE 指定較低解析度的圖示。 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 的構造函式會將此成員初始化為 TRUE。

這個成員必須在應用程式啟動時設定。

## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA：： m_bUseSystemFont

指出功能表、工具列和功能區是否使用系統字型。

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>備註

TRUE 指定使用系統字型;否則為 FALSE。 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 的構造函式會將此成員初始化為 FALSE。

測試這個成員不是架構判斷要使用之字型的唯一方法。 `AFX_GLOBAL_DATA::UpdateFonts` 方法也會測試預設和替代字型，以判斷哪些視覺化樣式可套用至功能表、工具列和功能區。

## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA：： m_hcurHand

儲存手型游標的控制代碼。

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA：： m_hcurStretch

儲存水平延展游標的控制代碼。

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA：： m_hcurStretchVert

儲存垂直延展游標的控制代碼。

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a>AFX_GLOBAL_DATA：： m_hiconTool

儲存工具圖示的控制代碼。

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA：： m_nAutoHideToolBarMargin

指定從最左邊的自動隱藏工具列到停駐列左邊的位移。

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>備註

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 建構函式會初始化這個成員為 4 個像素。

## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA：： m_nAutoHideToolBarSpacing

指定自動隱藏工具列之間的間距。

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>備註

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 的函式會將此成員初始化為14個圖元。

## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA：： m_nDragFrameThicknessDock

指定用來表示停駐狀態之拖曳框架的粗細。

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>備註

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 的函式會將此成員初始化為3個圖元。

## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA：： m_nDragFrameThicknessFloat

指定用來表示浮動狀態的拖曳框架粗細。

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>備註

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 建構函式會初始化這個成員為 4 個像素。

## <a name="onsettingchange"></a>AFX_GLOBAL_DATA：： OnSettingChange

偵測到桌面功能表動畫和工作列自動隱藏功能的目前狀態。

```
void OnSettingChange();
```

### <a name="remarks"></a>備註

這個方法會將架構變數設定為使用者桌面上某些屬性的狀態。 這個方法會偵測功能表動畫、功能表淡化和工作列自動隱藏功能的目前狀態。

## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA：： RegisterWindowClass

註冊指定的 MFC 視窗類別。

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>參數

*lpszClassNamePrefix*<br/>
在要註冊的視窗類別名稱。

### <a name="return-value"></a>傳回值

如果此方法成功，則為註冊之類別的限定名稱;否則，[資源例外](exception-processing.md#afxthrowresourceexception)狀況。

### <a name="remarks"></a>備註

傳回值是以冒號分隔的*lpszClassNamePrefix*參數字串清單，以及目前應用程式實例之控制碼的十六進位文字標記法。應用程式游標，這是其識別碼 IDC_ARROW 的箭號游標;和背景筆刷。 如需註冊 MFC 視窗類別的詳細資訊，請參閱[AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)。

## <a name="resume"></a>AFX_GLOBAL_DATA：： Resume

重新初始化內部函式指標，存取支援 Windows Themes and Visual Styles (佈景主題和視覺化樣式) 的方法。

```
BOOL Resume();
```

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。 在 [debug] 模式中，如果這個方法不成功，這個方法會判斷提示。

### <a name="remarks"></a>備註

當架構收到[WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast)訊息時，會呼叫這個方法。

## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA：： SetLayeredAttrib

提供呼叫 Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) 方法的簡單方法。

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>參數

*hwnd*<br/>
在分層視窗的控制碼。

*crKey*<br/>
在[桌面視窗管理員](/windows/win32/dwm/dwm-overview)用來撰寫分層視窗的透明色彩索引鍵。

*bAlpha*<br/>
在用來描述分層視窗之不透明度的 Alpha 值。

*dwFlags*<br/>
在旗標的位元組合（OR），指定要使用的方法參數。 指定 LWA_COLORKEY，以使用*crKey*參數作為透明度色彩。 指定 LWA_ALPHA，以使用*bAlpha*參數來判斷分層視窗的不透明度。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

## <a name="setmenufont"></a>AFX_GLOBAL_DATA：： SetMenuFont

建立指定的邏輯字型。

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*lpLogFont*<br/>
在結構的指標，其中包含字型的屬性。

*bHorz*<br/>
在TRUE 表示要以水準方式執行文字;FALSE 表示要垂直執行文字。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。 在 [debug] 模式中，如果這個方法不成功，這個方法會判斷提示。

### <a name="remarks"></a>備註

這個方法會建立水準的一般字型、加底線的字型，以及用於預設功能表項目的粗體字型。 這個方法會選擇性地建立一般的垂直字型。 如需邏輯字型的詳細資訊，請參閱[CFont：： CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect)。

## <a name="updatefonts"></a>AFX_GLOBAL_DATA：： UpdateFonts

重新初始化架構使用的邏輯字型。

```
void UpdateFonts();
```

### <a name="remarks"></a>備註

如需邏輯字型的詳細資訊，請參閱 `CFont::CreateFontIndirect`。

## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA：： UpdateSysColors

初始化架構使用的色彩、色彩深度、筆刷、畫筆與圖像。

```
void UpdateSysColors();
```

## <a name="biswindows7"></a>AFX_GLOBAL_DATA：： bIsWindows7

表示應用程式是否在 Windows 7 或以上版本執行。

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA：： clrActiveCaptionGradient

指定現用標題的漸層色彩。 通常用於停駐窗格。

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA：： clrInactiveCaptionGradient

指定非使用中標號的漸層色彩。 通常用於停駐窗格。

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA：： GetITaskbarList

在全域資料中建立和儲存指標至 `ITaskBarList` 介面。

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>傳回值

如果工作列清單物件建立成功，則為 `ITaskbarList` 介面的指標;如果建立失敗，或目前的作業系統小於 Windows 7，則為 Null。

## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA：： GetITaskbarList3

在全域資料中建立和儲存指標至 `ITaskBarList3` 介面。

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>傳回值

如果工作列清單物件建立成功，則為 `ITaskbarList3` 介面的指標;如果建立失敗，或目前的作業系統小於 Windows 7，則為 Null。

## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA：： GetShellAutohideBars

決定殼層自動隱藏軸的位置。

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>傳回值

包含編碼旗標的整數值，可指定自動隱藏列的位置。 它可能會合並下列值： AFX_AUTOHIDE_BOTTOM、AFX_AUTOHIDE_TOP、AFX_AUTOHIDE_LEFT、AFX_AUTOHIDE_RIGHT。

## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA：： ReleaseTaskBarRefs

釋放透過 `GetITaskbarList` 和 `GetITaskbarList3` 方法取得的介面。

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA：： ShellCreateItemFromParsingName

從剖析名稱建立並初始化殼層項目物件。

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>參數

*pszPath*<br/>
在顯示名稱的指標。

*pbc*<br/>
控制剖析作業之系結內容的指標。

*riid*<br/>
介面識別碼的參考。

*ppv*<br/>
脫銷當此函式傳回時，會包含在*riid*中要求的介面指標。 這通常會 `IShellItem` 或 `IShellItem2`。

### <a name="return-value"></a>傳回值

如果成功，則傳回 S_OK;否則為錯誤值。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../hierarchy-chart.md)<br/>
[結構、樣式、回呼和訊息對應](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[元件和狀態](/windows/win32/controls/parts-and-states)<br/>
[CDC：:D rawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[桌面視窗管理員](/windows/win32/dwm/dwm-overview)<br/>
[啟用和控制 DWM 組合](/windows/win32/dwm/composition-ovw)<br/>
[UI 自動化和 Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor 函式](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[NONCLIENTMETRICS 結構](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
