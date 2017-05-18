---
title: "CMFCCaptionBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionBar class
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c9be93449392de9d04e4869db8dcd73e08125c88
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar 類別
A`CMFCCaptionBar`物件是一種控制列，可以顯示三個項目︰ 按鈕、 文字標籤和點陣圖。 它一次只能每個類型各顯示一個項目。 您可以將每個項目對齊控制項的左緣或右緣，或對齊中央。 您也可以將平面或 3D 樣式套用至標題列的上框線和下框線。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCCaptionBar::Create](#create)|建立標題列控制項並將它附加`CMFCCaptionBar`物件。|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|指出是否可以在標題列和其父框架之間動態插入另一個窗格。 (覆寫[CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|  
|[CMFCCaptionBar::EnableButton](#enablebutton)|啟用或停用在標題列按鈕。|  
|[CMFCCaptionBar::GetAlignment](#getalignment)|傳回指定之項目的對齊方式。|  
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|傳回的標題列的框線大小。|  
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|擷取週框的標題列上的按鈕。|  
|[CMFCCaptionBar::GetMargin](#getmargin)|傳回的標題列項目邊緣和標題列控制項的邊緣之間的距離。|  
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|指定是否在訊息列模式中的標題列。|  
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|移除標題列中的點陣圖影像。|  
|[CMFCCaptionBar::RemoveButton](#removebutton)|移除標題列按鈕。|  
|[CMFCCaptionBar::RemoveIcon](#removeicon)|移除標題列中的圖示。|  
|[CMFCCaptionBar::RemoveText](#removetext)|移除標題列中的文字標籤。|  
|[CMFCCaptionBar::SetBitmap](#setbitmap)|設定標題列的點陣圖影像。|  
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|設定標題列的框線大小。|  
|[CMFCCaptionBar::SetButton](#setbutton)|設定標題列按鈕。|  
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|指定是否處於已按下按鈕。|  
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|設定按鈕的工具提示。|  
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|設定標題列的框線樣式。|  
|[CMFCCaptionBar::SetIcon](#seticon)|設定標題列的圖示。|  
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|設定標題列的映像的工具提示。|  
|[CMFCCaptionBar::SetMargin](#setmargin)|設定標題列項目的邊緣和標題列控制項的邊緣之間的距離。|  
|[CMFCCaptionBar::SetText](#settext)|設定標題列的文字標籤。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|標題列的背景填滿架構呼叫。|  
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|若要繪製的標題列的框線架構呼叫。|  
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|若要繪製的標題列按鈕架構呼叫。|  
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|若要繪製的標題列映像架構呼叫。|  
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|若要繪製的標題列文字架構呼叫。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|標題列的背景色彩。|  
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|標題列的框線色彩。|  
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|標題列文字的色彩。|  
  
## <a name="remarks"></a>備註  
 若要建立的標題列，請依照下列步驟執行︰  
  
1.  建構 `CMFCCaptionBar` 物件。 一般而言，您會將標題列加入框架視窗類別。  
  
2.  呼叫[CMFCCaptionBar::Create](#create)方法來建立標題列控制項並將其附加至`CMFCCaptionBar`物件。  
  
3.  呼叫[CMFCCaptionBar::SetButton](#setbutton)， [CMFCCaptionBar::SetText](#settext)， [CMFCCaptionBar::SetIcon](#seticon)，和[CMFCCaptionBar::SetBitmap](#setbitmap)設定標題列項目。  
  
 當您設定的 button 元素時，您必須指派至按鈕的命令 ID。 當使用者按一下按鈕，標題列路由`WM_COMMAND`這個識別碼對父框架視窗的訊息。  
  
 標題列也可以在訊息列模式，可模擬 Microsoft Office 2007 應用程式中出現的訊息列。 訊息列模式，在標題列會顯示點陣圖、 訊息和一個按鈕 （通常會開啟對話方塊）。您可以指定工具提示為點陣圖。  
  
 若要啟用訊息列模式，請呼叫[CMFCCaptionBar::Create](#create)和第四個參數 (bIsMessageBarMode) 設定為`TRUE`。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCCaptionBar`類別。 此範例示範如何建立標題列控制項、 設定標題列的 3D 框線、 設定單位為像素的標題列項目的邊緣和標題列控制項的邊緣之間的距離，、 設定標題列按鈕，設定按鈕的工具提示、 標題列的文字標籤設定、 設定標題列的點陣圖影像並將映像的工具提示的標題列中。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&1;](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]  
[!code-cpp[NVC_MFC_MSOffice2007Demo #&2;](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcaptionbar.h  
  
##  <a name="create"></a>CMFCCaptionBar::Create  
 建立標題列控制項並將它附加`CMFCCaptionBar`物件。  
  
```  
BOOL Create(
    DWORD dwStyle,  
    CWnd* pParentWnd,  
    UINT uID,  
    int nHeight=-1,  
    BOOL bIsMessageBarMode=FALSE);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 邏輯 OR 運算子組合的標題列樣式。  
  
 `pParentWnd`  
 標題列控制項的父視窗。  
  
 `uID`  
 標題列控制項的 ID。  
  
 `nHeight`  
 高度，單位為像素的標題列控制項。 如果是-1，就會根據圖示、 文字和標題列控制項顯示的按鈕的高度計算高度。  
  
 `bIsMessageBarMode`  
 `TRUE`如果訊息列模式中，標題列`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功，建立標題控制項`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 您建構`CMFCCaptionBar`兩個步驟中的物件。 您第一次呼叫建構函式，然後再呼叫`Create`方法，它會建立 Windows 控制項，並將它附加`CMFCCaptionBar`物件。  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCCaptionBar::DoesAllowDynInsertBefore  
 指出是否可以在標題列和其父框架之間動態插入另一個窗格。  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`FALSE`除非覆寫。  
  
### <a name="remarks"></a>備註  
  
##  <a name="enablebutton"></a>CMFCCaptionBar::EnableButton  
 啟用或停用在標題列按鈕。  
  
```  
void EnableButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用按鈕，`FALSE`來停用按鈕。  
  
##  <a name="getalignment"></a>CMFCCaptionBar::GetAlignment  
 傳回指定之項目的對齊方式。  
  
```  
BarElementAlignment GetAlignment(BarElement elem);
```  
  
### <a name="parameters"></a>參數  
 [in] `elem`  
 要擷取對齊標題列項目。  
  
### <a name="return-value"></a>傳回值  
 項目，例如按鈕、 點陣圖、 文字或圖示的對齊方式。  
  
### <a name="remarks"></a>備註  
 項目的對齊方式可以是下列值之一︰  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="getbordersize"></a>CMFCCaptionBar::GetBorderSize  
 傳回的標題列的框線大小。  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 單位為像素框線的大小。  
  
##  <a name="getbuttonrect"></a>CMFCCaptionBar::GetButtonRect  
 擷取週框的標題列上的按鈕。  
  
```  
CRect GetButtonRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`CRect`物件，其中包含在標題列按鈕的週框的座標。  
  
##  <a name="getmargin"></a>CMFCCaptionBar::GetMargin  
 傳回的標題列項目邊緣和標題列控制項的邊緣之間的距離。  
  
```  
int GetMargin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 距離，單位為像素的標題列項目邊緣和標題列控制項的邊緣之間。  
  
##  <a name="ismessagebarmode"></a>CMFCCaptionBar::IsMessageBarMode  
 指定是否在訊息列模式中的標題列。  
  
```  
BOOL IsMessageBarMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果訊息列模式中，標題列`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 在訊息列模式中，標題列會顯示工具提示、 訊息文字與按鈕的影像。  
  
##  <a name="m_clrbarbackground"></a>CMFCCaptionBar::m_clrBarBackground  
 標題列的背景色彩。  
  
```  
COLORREF m_clrBarBackground  
```  
  
##  <a name="m_clrbarborder"></a>CMFCCaptionBar::m_clrBarBorder  
 標題列的框線色彩。  
  
```  
COLORREF m_clrBarBorder  
```  
  
##  <a name="m_clrbartext"></a>CMFCCaptionBar::m_clrBarText  
 標題列文字的色彩。  
  
```  
COLORREF m_clrBarText  
```  
  
##  <a name="ondrawbackground"></a>CMFCCaptionBar::OnDrawBackground  
 標題列的背景填滿架構呼叫。  
  
```  
virtual void OnDrawBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的標題列的指標。  
  
 [in] `rect`  
 要填滿的週框矩形。  
  
### <a name="remarks"></a>備註  
 `OnDrawBackground`標題列的背景填滿時，呼叫方法。 預設實作會藉由使用填入背景[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)色彩。  
  
 覆寫這個方法在`CMFCCaptionBar`衍生類別，即可自訂標題列的外觀。  
  
##  <a name="ondrawborder"></a>CMFCCaptionBar::OnDrawBorder  
 若要繪製的標題列的框線架構呼叫。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容，用於顯示框線。  
  
 [in] `rect`  
 週框。  
  
### <a name="remarks"></a>備註  
 根據預設，框線會有一般的樣式。  
  
 覆寫這個方法在`CMFCCaptionBar`衍生類別，即可自訂標題列框線的外觀。  
  
##  <a name="ondrawbutton"></a>CMFCCaptionBar::OnDrawButton  
 若要繪製的標題列按鈕架構呼叫。  
  
```  
virtual void OnDrawButton(
    CDC* pDC,  
    CRect rect,  
    const CString& strButton,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 用來顯示按鈕的裝置內容指標。  
  
 [in] `rect`  
 [] 按鈕，這個周框。  
  
 [in] `strButton`  
 按鈕的文字標籤。  
  
 [in] `bEnabled`  
 `TRUE`如果已啟用 按鈕。`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在`CMFCCaptionBar`衍生類別，即可自訂標題列按鈕的外觀。  
  
##  <a name="ondrawimage"></a>CMFCCaptionBar::OnDrawImage  
 若要繪製的標題列映像架構呼叫。  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 用來顯示影像的裝置內容指標。  
  
 [in] `rect`  
 指定影像的周框矩形。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在`CMFCCaptionBar`衍生類別，即可自訂影像的外觀。  
  
##  <a name="ondrawtext"></a>CMFCCaptionBar::OnDrawText  
 若要繪製的標題列文字架構呼叫。  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 用來顯示按鈕的裝置內容指標。  
  
 [in] `rect`  
 文字的週框。  
  
 [in] `strText`  
 要顯示的文字字串。  
  
### <a name="remarks"></a>備註  
 預設實作會使用來顯示文字`CDC::DrawText`和[CMFCCaptionBar::m_clrBarText](#m_clrbartext)色彩。  
  
 覆寫這個方法在`CMFCCaptionBar`衍生類別，即可自訂標題列文字的外觀。  
  
##  <a name="removebitmap"></a>CMFCCaptionBar::RemoveBitmap  
 移除標題列中的點陣圖影像。  
  
```  
void RemoveBitmap();
```  
  
##  <a name="removebutton"></a>CMFCCaptionBar::RemoveButton  
 移除標題列按鈕。  
  
```  
void RemoveButton();
```  
  
### <a name="remarks"></a>備註  
 標題列項目的配置會自動調整。  
  
##  <a name="removeicon"></a>CMFCCaptionBar::RemoveIcon  
 移除標題列中的圖示。  
  
```  
void RemoveIcon();
```  
  
##  <a name="removetext"></a>CMFCCaptionBar::RemoveText  
 移除標題列中的文字標籤。  
  
```  
void RemoveText();
```  
  
##  <a name="setbitmap"></a>CMFCCaptionBar::SetBitmap  
 設定標題列的點陣圖影像。  
  
```  
void SetBitmap(
    HBITMAP hBitmap,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

 
void SetBitmap(
    UINT uiBmpResID,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>參數  
 [in] `hBitmap`  
 若要設定點陣圖控制代碼。  
  
 [in] `clrTransparent`  
 指定點陣圖的透明色彩的 RGB 值。  
  
 [in] `bStretch`  
 如果`TRUE`，點陣圖會自動縮放，如果不符合週框的影像。 否則不會自動縮放點陣圖。  
  
 [in] `bmpAlignment`  
 點陣圖的對齊方式。  
  
### <a name="remarks"></a>備註  
 使用這個方法來設定標題列上的點陣圖。  
  
 先前的點陣圖就會自動終結。 如果標題列顯示的圖示，因為您呼叫[CMFCCaptionBar::SetIcon](#seticon)方法，將不會顯示點陣圖，除非您移除此圖示，藉由呼叫[CMFCCaptionBar::RemoveIcon](#removeicon)。  
  
 對齊點陣圖所指定`bmpAlignment`參數。  這個參數可以是下列其中一個 `BarElementAlignment` 值：  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setbordersize"></a>CMFCCaptionBar::SetBorderSize  
 設定標題列的框線大小。  
  
```  
void SetBorderSize(int nSize);
```  
  
### <a name="parameters"></a>參數  
 [in] `nSize`  
 新的大小，單位為像素的標題列框線。  
  
##  <a name="setbutton"></a>CMFCCaptionBar::SetButton  
 設定標題列按鈕。  
  
```  
void SetButton(
    LPCTSTR lpszLabel,  
    UINT uiCmdUI,  
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,  
    BOOL bHasDropDownArrow=TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpszLabel`  
 按鈕的命令標籤。  
  
 `uiCmdUI`  
 按鈕的命令 id。  
  
 `btnAlignmnet`  
 按鈕的對齊方式。  
  
 `bHasDropDownArrow`  
 `TRUE`如果按鈕顯示的下拉箭號，`FALSE`否則。  
  
##  <a name="setbuttonpressed"></a>CMFCCaptionBar::SetButtonPressed  
 指定是否處於已按下按鈕。  
  
```  
void SetButtonPressed(BOOL bPresed=TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bPresed`  
 `TRUE`如果按鈕按下的狀態，`FALSE`否則。  
  
##  <a name="setbuttontooltip"></a>CMFCCaptionBar::SetButtonToolTip  
 設定按鈕的工具提示。  
  
```  
void SetButtonToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszToolTip`  
 工具提示的標題。  
  
 [in] `lpszDescription`  
 工具提示描述。  
  
##  <a name="setflatborder"></a>CMFCCaptionBar::SetFlatBorder  
 設定標題列的框線樣式。  
  
```  
void SetFlatBorder(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bFlat`  
 `TRUE`如果是平面的標題列的框線。 `FALSE`如果框線呈現為 3D。  
  
##  <a name="seticon"></a>CMFCCaptionBar::SetIcon  
 設定標題列的圖示。  
  
```  
void SetIcon(
    HICON hIcon,  
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>參數  
 [in] `hIcon`  
 若要設定圖示的控制代碼。  
  
 [in] `iconAlignment`  
 圖示的對齊方式。  
  
### <a name="remarks"></a>備註  
 標題列可以顯示圖示或點陣圖。 請參閱[CMFCCaptionBar::SetBitmap](#setbitmap)來了解如何顯示點陣圖。 如果您設定圖示和點陣圖，一律會顯示圖示。 呼叫[CMFCCaptionBar::RemoveIcon](#removeicon)移除標題列中的圖示。  
  
 圖示對齊根據`iconAlignment`參數。 它可以是下列其中一種`BarElementAlignment`值︰  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setimagetooltip"></a>CMFCCaptionBar::SetImageToolTip  
 設定映像的工具提示的標題列中。  
  
```  
void SetImageToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszToolTip`  
 工具提示的文字。  
  
 [in] `lpszDescription`  
 工具提示描述。  
  
##  <a name="setmargin"></a>CMFCCaptionBar::SetMargin  
 設定標題列項目的邊緣和標題列控制項的邊緣之間的距離。  
  
```  
void SetMargin(int nMargin);
```  
  
### <a name="parameters"></a>參數  
 [in] `nMargin`  
 距離，單位為像素的標題列項目邊緣和標題列控制項的邊緣之間。  
  
##  <a name="settext"></a>CMFCCaptionBar::SetText  
 設定標題列的文字標籤。  
  
```  
void SetText(
    const CString& strText,  
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>參數  
 [in] `strText`  
 若要設定文字字串。  
  
 [in] `textAlignment`  
 文字對齊方式。  
  
### <a name="remarks"></a>備註  
 對齊的文字標籤所指定`textAlignment`參數。 它可以是下列其中一種`BarElementAlignment`值︰  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

