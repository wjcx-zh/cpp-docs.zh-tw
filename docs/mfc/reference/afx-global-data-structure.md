---
title: "AFX_GLOBAL_DATA 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GLOBAL_DATA
dev_langs:
- C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
caps.latest.revision: 30
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 1427efddf9271d273e94c4f62d6d104e7f1c2b48
ms.lasthandoff: 03/31/2017

---
# <a name="afxglobaldata-structure"></a>AFX_GLOBAL_DATA 結構
`AFX_GLOBAL_DATA` 結構包含的欄位和方法，用於管理架構，或自訂應用程式外觀和行為。  
  
## <a name="syntax"></a>語法  
  
```  
struct AFX_GLOBAL_DATA  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|建構 `AFX_GLOBAL_DATA` 結構。|  
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|釋出架構配置的資源，例如筆刷、字型和 DLL。|  
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|建立環繞指定點依特定角度旋轉的旋轉轉換。|  
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|在指定的區域中繪製控制項父代的背景。|  
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|以指定佈景主題的視覺化樣式繪製指定文字。|  
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|從指定的緩衝區中移除指定的 XML 標記組。|  
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|擷取指定的使用者介面項目目前的色彩。|  
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|傳回儲存在全域資料中的 `ID2D1Factory` 介面指標。 介面若未初始化，就會建立介面並設定預設參數。|  
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|擷取預先定義的資料指標，它有類似手掌的形狀，且識別項是 `IDC_HAND`。|  
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|在全域資料中建立和儲存 ITaskBarList 介面的指標。|  
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|在全域資料中建立和儲存 ITaskBarList3 介面的指標。|  
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|擷取與非最小化視窗之非工作區相關聯的度量。|  
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|決定殼層自動隱藏軸的位置。|  
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|擷取目前字型的文字字元高度。|  
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|傳回儲存在全域資料中的 `IWICImagingFactory` 介面指標。 介面若未初始化，就會建立介面並設定預設參數。|  
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|傳回儲存在全域資料中的 `IDWriteFactory` 介面指標。 介面若未初始化，就會建立介面並設定預設參數。|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|初始化 `D2D`、 `DirectWrite`和 `WIC` Factory。 初始化主視窗之前先呼叫這個方法。|  
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|指出是否支援預先定義的 32 位元圖示。|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|判斷是否已初始化 `D2D` 。|  
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|提供呼叫 Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) 方法的簡單方式。|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|指出目前是否以高對比顯示圖像。|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|偵測到桌面功能表動畫和工作列自動隱藏功能的目前狀態。|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|註冊指定的 MFC 視窗類別。|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|釋出透過 GetITaskbarList 和 GetITaskbarList3 方法取得的介面。|  
|[AFX_GLOBAL_DATA::Resume](#resume)|重新初始化內部函式指標，存取支援 Windows [Themes and Visual Styles](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)(佈景主題和視覺化樣式) 的方法。|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|提供呼叫 Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) 方法的簡單方法。|  
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|建立指定的邏輯字型。|  
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|從剖析名稱建立並初始化殼層項目物件。|  
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|重新初始化架構使用的邏輯字型。|  
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|初始化架構使用的色彩、色彩深度、筆刷、畫筆與圖像。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|啟用或停用 Microsoft Active Accessibility 支援。 Active Accessibility 提供可靠的方法以公開使用者介面項目的相關資訊。|  
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|指出是否已啟用 Microsoft Active Accessibility 支援。|  
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|指出作業系統是否支援層疊的視窗。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|指出目前的作業系統是否支援 Alpha 混色。|  
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|指出應用程式是在 Windows 7 作業系統或更高版本中執行。|  
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|指定現用標題的漸層色彩。 通常用於停駐窗格。|  
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|指定非作用中現用標題的漸層色彩。 通常用於停駐窗格。|  
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|指出架構使用預先定義的 32 位元色彩圖示或較低解析度的圖示。|  
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|指出功能表、工具列和功能區是否使用系統字型。|  
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|儲存手型游標的控制代碼。|  
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|儲存水平延展游標的控制代碼。|  
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|儲存垂直延展游標的控制代碼。|  
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|儲存工具圖示的控制代碼。|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|指定從最左邊的自動隱藏工具列到停駐列左邊的位移。|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|指定自動隱藏工具列之間的間距。|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|指定溝通停駐狀態所使用的拖曳框架粗細。|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|指定溝通浮動狀態所使用的拖曳框架粗細。|  
  
### <a name="remarks"></a>備註  
 `AFX_GLOBAL_DATA` 結構的大部分資料是在應用程式啟動時初始化。  
  
### <a name="inheritance-hierarchy"></a>繼承階層  
 `AFX_GLOBAL_DATA`   
  
### <a name="requirements"></a>需求  
 **Header:** afxglobals.h  
  
### <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
指出作業系統是否支援 alpha 混色。  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE`指出 alpha 混色支援;否則， `FALSE`。  
  

## <a name="cleanup"></a>AFX_GLOBAL_DATA::CleanUp
釋出架構配置的資源，例如筆刷、字型和 DLL。  
  
  
```  
void CleanUp();
```  
## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
建立環繞指定點依特定角度旋轉的旋轉轉換。  
  
  
```  
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,  
    D2D1_POINT_2F center,  
    D2D1_MATRIX_3X2_F *matrix);
```  
  
### <a name="parameters"></a>參數   
 `angle`  
 順時針旋轉的角度，以度為單位。  
  
 `center`  
 旋轉中心點。  
  
 `matrix`  
 這個方法傳回時，包含新的旋轉轉換。 您必須為此參數來配置儲存空間。  
  
### <a name="return-value"></a>傳回值  
 否則會傳回 S_OK，如果成功或錯誤值。  
  
## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA::DrawParentBackground
在指定的區域中繪製控制項父代的背景。  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>參數   
 [in] `pWnd`  
 指向控制項視窗的指標。  
  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `lpRect`  
 指向限定要繪製區域的矩形的指標。 預設值是 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA::DrawTextOnGlass
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
 [in] `hTheme`  
 視窗佈景主題資料的控制代碼，或 `NULL`。 如果此參數不是 `NULL` ，且支援佈景主題，則此架構會使用指定的佈景主題來繪製文字。 否則，此架構不會使用佈景主題來繪製文字。  
  
 請使用 [OpenThemeData](http://msdn.microsoft.com/library/windows/desktop/bb759821) 方法建立 `HTHEME`。  
  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `iPartId`  
 具有想要的文字外觀之控制項組件。 如需詳細資訊，請參閱 [Parts and States](http://msdn.microsoft.com/library/windows/desktop/bb773210)(組件和狀態) 表格中的 Parts 資料行。 如果此值為 0，則會使用預設字型來繪製文字；否則會使用裝置內容中所選取的字型。  
  
 [in] `iStateId`  
 具有想要的文字外觀的控制項狀態。 如需詳細資訊，請參閱 [Parts and States](http://msdn.microsoft.com/library/windows/desktop/bb773210)(組件和狀態) 表格中的 States 資料行。  
  
 [in] `strText`  
 要繪製的文字。  
  
 [in] `rect`  
 在其中繪製指定文字的區域界限。  
  
 [in] `dwFlags`  
 旗標的位元組合 (OR)，指定如何繪製指定文字。  
  
 如果`hTheme`參數是`NULL`或如果您沒有支援並啟用，主題`nFormat`參數[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)方法會描述有效的旗標。 如果支援佈景主題， `dwFlags` DrawThemeTextEx [方法的](http://msdn.microsoft.com/library/windows/desktop/bb773317) 參數會描述有效的旗標。  
  
 [in] `nGlowSize`  
 繪製指定文字前已繪製在背景上的光暈效果大小。 預設值為 0。  
  
 [in] `clrText`  
 用來繪製指定文字的色彩。 預設值為預設色彩。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果使用佈景主題來繪製指定的文字;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 佈景主題會定義應用程式的視覺化樣式。 如果 `hTheme` 參數為 `NULL`、不支援 [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) 方法，或 [桌面視窗管理員](http://msdn.microsoft.com/library/windows/desktop/aa969540) (DWM) 組合已停用，就不會使用佈景主題來繪製文字。  
  
### <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [組件和狀態](http://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317)   
 [桌面視窗管理員](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [啟用和控制 DWM 組合](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport
啟用或停用 Microsoft Active Accessibility 支援。  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數   
 [in] `bEnable`  
 `TRUE` 表示啟用協助工具支援，`FALSE` 則表示停用協助工具支援。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 Active Accessibility 是一種 COM 技術，可改善程式與 Windows 作業系統一起與輔助技術產品合作的方式。 它提供用於公開使用者介面項目資訊的可靠方法。 然而，現在已有稱為 Microsoft UI 自動化之較新協助工具模型可供使用。 如需這兩項技術的比較，請參閱[UI 自動化和 Microsoft Active Accessibility](http://msdn.microsoft.com/library/87bee662-0a3e-4232-a421-20e7a5968321)。  
  
 使用[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)方法，以判斷是否已啟用 Microsoft Active Accessibility 支援。  
  
 
### <a name="see-also"></a>另請參閱  
 [UI 自動化和 Microsoft Active Accessibility](http://msdn.microsoft.com/library/87bee662-0a3e-4232-a421-20e7a5968321)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag
從指定的緩衝區中移除指定的 XML 標記組。  
  
  
```  
BOOL ExcludeTag(
    CString& strBuffer,  
    LPCTSTR lpszTag,  
    CString& strTag,  
    BOOL bIsCharsList = FALSE);
```  
  
### <a name="parameters"></a>參數   
 [in] `strBuffer`  
 文字的緩衝區。  
  
 [in] `lpszTag`  
 一組的開頭和結尾 XML 標記名稱。  
  
 [輸出] `strTag`  
 此方法傳回時，`strTag`參數包含文字的開頭和結尾 XML 之間的命名方式的標記`lpszTag`參數。 修剪任何開頭或尾端空白字元的結果。  
  
 [in] `bIsCharsList`  
 `TRUE`要轉換中的逸出字元的符號`strTag`參數插入實際逸出字元。`FALSE`不是用來執行轉換。預設值是`FALSE`。 如需詳細資訊，請參閱＜備註＞。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 XML 標記組包含名為開頭和結尾標記的開始和結束的指定緩衝區中的文字執行中的指示。 `strBuffer`參數指定的緩衝區中，而`lpszTag`參數指定的 XML 標記名稱。  
  
 使用下表中的符號，編碼一組指定的緩衝區中的逸出字元。 指定`TRUE`如`bIsCharsList`參數轉換中的符號`strTag`成實際的逸出字元的參數。 下表會使用[_T()](../../c-runtime-library/data-type-mappings.md)巨集，以指定的符號和逸出字元字串。  
  
|符號|逸出字元|  
|------------|----------------------|  
|_T("\\\t")|_T("\t")|  
|_T("\\\n")|_T("\n")|  
|_T("\\\r")|_T("\r")|  
|_T("\\\b")|_T("\b")|  
|_T("LT")|_T("\<")|  
|_T("GT")|_T(">")|  
|_T("AMP")|_T("&")|  
  
## <a name="getcolor"></a>AFX_GLOBAL_DATA::GetColor
擷取指定的使用者介面項目目前的色彩。  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>參數   
 [in] `nColor`  
 指定將擷取其色彩之使用者介面項目的值。 如需有效值的清單，請參閱`nIndex`參數[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)方法。  
  
### <a name="return-value"></a>傳回值  
 指定之使用者介面項目的 RGB 色彩值。 如需詳細資訊，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 如果 `nColor` 參數超出範圍，則傳回值為零。 由於零也是有效的 RGB 值，您無法使用這個方法來判斷目前的作業系統是否支援系統色彩。 請改用[GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927)方法，這個方法會傳回`NULL`若色彩不支援。  
  
### <a name="see-also"></a>另請參閱  

 [GetSysColor 函式](http://msdn.microsoft.com/library/windows/desktop/ms724371)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927)

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory
 傳回儲存在全域資料的 ID2D1Factory 介面的指標。 介面若未初始化，就會建立介面並設定預設參數。  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>傳回值  
 指向 ID2D1Factory 介面 factory 建立成功，則如果建立失敗，則為 NULL 或目前的作業系統不需要 D2D 支援。  
  
## <a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor
擷取預先定義的資料指標，它有類似手掌的形狀，且識別項是 `IDC_HAND`。  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>傳回值  
 手狀游標的控制代碼。  

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics
擷取與非最小化視窗之非工作區相關聯的度量。  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>參數   
 [in、out] `info`  
 A [NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175)結構，其中包含與非最小化視窗中非工作區相關聯的可擴充的度量資訊。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則， `FALSE`。  
 
  
### <a name="see-also"></a>另請參閱   
 [NONCLIENTMETRICS 結構](http://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight
 擷取目前字型的文字字元高度。  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>參數   
 [in] `bHorz`  
 `TRUE`擷取字元的高度時執行文字水平空間。`FALSE`文字以垂直方式執行時擷取字元的高度。 預設值是 `TRUE`。  
  
### <a name="return-value"></a>傳回值  
 目前的字型，其下半部從其遞增元量的高度。  
  
## <a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory
傳回儲存在全域資料的 IWICImagingFactory 介面的指標。 介面若未初始化，就會建立介面並設定預設參數。  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>傳回值  
 指向 IWICImagingFactory 介面 factory 建立成功，則如果建立失敗，則為 NULL 或目前的作業系統不需要 WIC 支援。  
  
## <a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory
傳回儲存在全域資料的 IDWriteFactory 介面的指標。 介面若未初始化，就會建立介面並設定預設參數。  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>傳回值  
 指向 IDWriteFactory 介面 factory 建立成功，則如果建立失敗，則為 NULL 或目前的作業系統不需要 DirectWrite 支援。  
 
## <a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D
初始化 D2D、 DirectWrite 和 WIC 處理站。 初始化主視窗之前先呼叫這個方法。  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>參數   
 `d2dFactoryType`  
 D2D factory 和它所建立的資源的執行緒模型。  
  
 `writeFactoryType`  
 值，指定是否將共用或隔離寫入 factory 物件  
  
### <a name="return-value"></a>傳回值  
 如果 factory 所 intilalizrd，FALSE-否則為 true，則傳回  
  
## <a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons
指出是否支援預先定義的 32 位元圖示。  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果預先定義的 32 位元，支援圖示否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`TRUE`架構支援 32 位元的內建圖示，如果作業系統支援 16 位元 / 像素或更多，以及如果映像不會顯示在 高對比。  
  
## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport
指出是否已啟用 Microsoft Active Accessibility 支援。  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>傳回值  
 如果已啟用協助工具支援則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 Microsoft Active Accessibility 是過去用來讓應用程式成為可存取的方法。 Microsoft UI 自動化是 Microsoft Windows 的一種新的協助工具模型，能滿足輔助科技產品及自動化測試工具的需求。   
  
 使用[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)方法以啟用或停用 Active Accessibility 支援。  
  

### <a name="see-also"></a>另請參閱  
 [UI 自動化和 Microsoft Active Accessibility](http://msdn.microsoft.com/library/87bee662-0a3e-4232-a421-20e7a5968321)

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialized
 判斷是否已初始化 D2D  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>傳回值  
 初始化 D2D; 如果為 TRUE否則為 FALSE。  
  
## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled
提供呼叫 Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) 方法的簡單方式。  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果[桌面視窗管理員](http://msdn.microsoft.com/library/windows/desktop/aa969540)(DWM) 組合已啟用，否則`FALSE`。  
  
### <a name="see-also"></a>另請參閱    
 [桌面視窗管理員](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [啟用和控制 DWM 組合](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode
 指出目前是否以高對比顯示圖像。    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果目前顯示影像的黑色或白色高對比模式，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 在黑色的高對比模式背對光源為白色，背景是黑色。 在白色高對比模式背對光源是黑色，背景是白色。  
  
## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
指出作業系統是否支援層疊的視窗。  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>傳回值  
 如果支援層疊視窗則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果支援層疊的視窗，*智慧停駐*標記會使用層疊的視窗。  
  
## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
指出架構使用預先定義的 32 位元色彩圖示或較低解析度的圖示。  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE` 會指定架構使用 32 位元色彩圖示；`FALSE` 會指定較低解析度的圖示。 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 建構函式會將此成員初始化為 `TRUE`。  
  
 這個成員必須在應用程式啟動時設定。  
  
## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont
指出功能表、工具列和功能區是否使用系統字型。  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>備註  
 `TRUE`指定要使用系統字型。否則， `FALSE`。 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 建構函式會將此成員初始化為 `FALSE`。  
  
 測試這個成員是不使用的架構，以判斷字型的唯一方式。 `AFX_GLOBAL_DATA::UpdateFonts`方法也會測試預設及替代字型來決定哪些視覺化樣式套用至功能表、 工具列和功能區程式碼。  
  
## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand
儲存手型游標的控制代碼。  
  
  
```  
HCURSOR m_hcurHand;  
```  
  
## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch
儲存水平延展游標的控制代碼。  
  
  
```  
HCURSOR m_hcurStretch;  
```  

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert
儲存垂直延展游標的控制代碼。  
  
  
```  
HCURSOR m_hcurStretchVert;  
```  
  
## <a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool
儲存工具圖示的控制代碼。  
  
  
```  
HICON m_hiconTool;  
```  
## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
指定從最左邊的自動隱藏工具列到停駐列左邊的位移。  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>備註  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 建構函式會初始化這個成員為 4 個像素。  
  
## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
指定自動隱藏工具列之間的間距。  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>備註  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`建構函式會初始化這個成員為 14 像素為單位。  
  
## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

指定用來表示停駐的狀態拖曳框架的粗細。  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>備註  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`建構函式會初始化這個成員為 3 的像素。  
  
## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
指定用來指出浮動狀態拖曳框架的粗細。  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>備註  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` 建構函式會初始化這個成員為 4 個像素。  
  
## <a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange
偵測到桌面功能表動畫和工作列自動隱藏功能的目前狀態。  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>備註  
 這個方法會設定 framework 變數之使用者的桌面的某些屬性的狀態。 這個方法偵測功能表動畫，功能表淡出，並自動隱藏功能工作列的目前狀態。  
  
## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass
註冊指定的 MFC 視窗類別。  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>參數   
 [in] `lpszClassNamePrefix`  
 要註冊之視窗類別的名稱。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則已註冊類別的限定的名稱否則，[資源例外狀況](http://msdn.microsoft.com/library/ddd99292-819b-4fa4-8371-b1954ed5856d)。  
  
### <a name="remarks"></a>備註  
 傳回值是 `lpszClassNamePrefix` 參數字串的冒號分隔清單，並且是表示目前應用程式執行個體之控制代碼的十六進位文字；應用程式游標，即識別項為 IDC_ARROW 的箭號游標；以及背景筆刷。 如需註冊 MFC 視窗類別的詳細資訊，請參閱[AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)。  
  
### <a name="see-also"></a>另請參閱    
 [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [AfxThrowResourceException](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a>AFX_GLOBAL_DATA::Resume
 重新初始化存取方法，可支援 Windows 佈景主題和視覺化樣式的內部函式指標。 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則， `FALSE`。 在偵錯模式中，這個方法會判斷提示這個方法是否成功。  
  
### <a name="remarks"></a>備註  
 當收到架構會呼叫這個方法[WM_POWERBROADCAST](http://msdn.microsoft.com/library/windows/desktop/aa373247)訊息。  
  
## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib
提供呼叫 Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) 方法的簡單方法。  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>參數   
 [in] `hwnd`  
 層疊視窗的控制代碼。  
  
 [in] `crKey`  
 透明色彩索引鍵[桌面視窗管理員](http://msdn.microsoft.com/library/windows/desktop/aa969540)使用來構成層疊的視窗。  
  
 [in] `bAlpha`  
 Alpha 值，用來描述層疊視窗的不透明度。  
  
 [in] `dwFlags`  
 位元組合 (OR) 或旗標，指定要使用哪些方法參數。 指定 LWA_COLORKEY 以使用 `crKey` 參數做為透明色彩。 指定 LWA_ALPHA 使用 `bAlpha` 參數來判斷層疊視窗的不透明度。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則， `FALSE`。   
 
### <a name="see-also"></a>另請參閱   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540)

## <a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont
建立指定的邏輯字型。  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數   
 [in] `lpLogFont`  
 包含字型的屬性的結構指標。  
  
 [in] `bHorz`  
 `TRUE`若要指定的文字往返水平空間。`FALSE`來指定文字以垂直方式執行。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則， `FALSE`。 在偵錯模式中，這個方法會判斷提示這個方法是否成功。  
  
### <a name="remarks"></a>備註  
 這個方法會建立水平的一般字型，加上底線的字型，並會以粗體字用預設功能表項目。 這個方法會選擇性地建立一般的垂直字型。 如需邏輯字型的詳細資訊，請參閱[cfont:: Createfontindirect](../../mfc/reference/cfont-class.md#createfontindirect)。  
  
## <a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts
重新初始化架構使用的邏輯字型。  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>備註  
 如需邏輯字型的詳細資訊，請參閱 `CFont::CreateFontIndirect`。  
  
## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors
初始化架構使用的色彩、色彩深度、筆刷、畫筆與圖像。  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7
表示應用程式是否在 Windows 7 或以上版本執行。  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient
指定現用標題的漸層色彩。 通常用於停駐窗格。  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clrInactiveCaptionGradient
指定非使用中標號的漸層色彩。 通常用於停駐窗格。  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarList
在全域資料中建立和儲存指標至 `ITaskBarList` 介面。  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>傳回值  
 如果工作列清單物件建立成功則為 `ITaskbarList` 介面的指標中，如果建立失敗，或者如果目前的作業系統版本比 Windows 7 舊則為 `NULL`。  
  
## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3
在全域資料中建立和儲存指標至 `ITaskBarList3` 介面。  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>傳回值  
 如果工作列清單物件建立成功則為 `ITaskbarList3` 介面的指標中，如果建立失敗，或者如果目前的作業系統版本比 Windows 7 舊則為 `NULL`。  
  
## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars
決定殼層自動隱藏軸的位置。  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>傳回值  
 整數值與編碼的旗標，指定位置的自動隱藏列。 它可以結合下列的值︰ AFX_AUTOHIDE_BOTTOM、 AFX_AUTOHIDE_TOP、 AFX_AUTOHIDE_LEFT、 AFX_AUTOHIDE_RIGHT。  
  
## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs
釋放介面透過`GetITaskbarList`和`GetITaskbarList3`方法。  
  
  
```  
void ReleaseTaskBarRefs();
```  
  
## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
從剖析名稱建立並初始化殼層項目物件。  
  
  
```  
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,  
    IBindCtx *pbc,  
    REFIID riid,  
    void **ppv);
```  
  
### <a name="parameters"></a>參數   
 `pszPath`  
 [in]指標的顯示名稱。  
  
 `pbc`  
 控制在剖析作業繫結內容的指標。  
  
 `riid`  
 參考介面識別碼。  
  
 `ppv`  
 [out]此函式傳回時，包含所要求的介面指標`riid`。 這通常會是`IShellItem`或`IShellItem2`。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果登錄成功。否則為錯誤值。  


