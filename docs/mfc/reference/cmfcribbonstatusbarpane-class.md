---
title: "CMFCRibbonStatusBarPane 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBarPane
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane class
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: 31
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a101e50f55efab44e4cb66d314b2426228dbc5c0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane 類別
`CMFCRibbonStatusBarPane`類別實作，您可以加入至功能區狀態列的功能區項目。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|建構並初始化 `CMFCRibbonStatusBarPane` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|傳回定義可顯示在窗格中，而不會截斷的最長的文字字串的字串。|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|傳回目前的文字對齊方式的設定。|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|決定動畫是否正在進行中。|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|決定是否要將窗格位於功能區狀態列擴充區域中。|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(覆寫[CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder)。)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(覆寫[CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)。)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|定義可顯示在窗格中，而不會截斷的最長的文字字串。|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|指派給 窗格可用於動畫的影像清單。|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|設定文字對齊方式。|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|開始指派給 窗格的動畫。|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|指派給 窗格的動畫就會停止。 .|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|指派給 窗格的動畫停止時，由架構呼叫。|  
  
## <a name="example"></a>範例  
 下列範例示範如何在 `CMFCRibbonStatusBarPane` 類別中使用各種方法。 此範例示範如何建構`CMFCRibbonStatusBarPane`物件，設定狀態列窗格的標籤的文字對齊方式，定義可顯示在 [狀態] 列窗格，而不會截斷、 附加至狀態列窗格，可用於動畫，並開始動畫影像清單的最長文字。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&2;](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxribbonstatusbarpane.h  
  
##  <a name="a-namecmfcribbonstatusbarpanea--cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 建構在狀態列中的窗格物件。  
  
```  
CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    BOOL bIsStatic=FALSE,  
    HICON hIcon=NULL,  
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nCmdID`  
 指定 [] 窗格中的命令 ID。  
  
 [in] `lpszText`  
 指定要在窗格中顯示的文字字串。  
  
 [in] `bIsStatic`  
 如果`TRUE`，[狀態] 窗格無法反白顯示，或可以按一下它選取。  
  
 [in] `hIcon`  
 指定要在窗格中顯示圖示的控制代碼。  
  
 [in] `lpszAlmostLargeText`  
 指定可顯示的窗格中的最長文字字串。  
  
 [in] `hBmpAnimationList`  
 指定將用於動畫的影像清單控制代碼。  
  
 [in] `cxAnimation`  
 指定寬度，單位為像素用於動畫的影像清單中的圖示。  
  
 [in] `clrTrnsp`  
 指定用於動畫的影像清單內的影像的透明色彩。  
  
 [in] `uiAnimationListResID`  
 指定用於動畫的影像清單的資源識別碼。  
  
##  <a name="a-namegetalmostlargetexta--cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText  
 取得狀態列窗格可以顯示的最長的文字字串。  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 狀態列窗格可以顯示最長文字字串。  
  
##  <a name="a-namegettextaligna--cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign  
 取得目前狀態列窗格的標籤的文字對齊方式的設定。  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的文字對齊方式可以是下列其中之一︰  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT。  
  
##  <a name="a-nameisanimationa--cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation  
 決定動畫是否正在進行中。  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已進行; 中的動畫`FALSE`否則。  
  
##  <a name="a-nameisextendeda--cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a>CMFCRibbonStatusBarPane::IsExtended  
 決定是否要將窗格位於功能區狀態列擴充區域中。  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格上狀態列擴充區域。 否則為 `FALSE`。  
  
##  <a name="a-nameondrawbordera--cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>參數  
 [in] `CDC*`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonfillbackgrounda--cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonfinishanimationa--cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation  
 指派給 窗格的動畫結束時，架構會呼叫這個方法。  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>備註  
 `StopAnimation`方法會呼叫`OnFinishAnimation`方法，您可以使用動畫結束時清除資料。  
  
##  <a name="a-namesetalmostlargetexta--cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText  
 定義可顯示在 [狀態] 列窗格，而不會截斷的最長文字。  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszAlmostLargeText`  
 指定的最長的字串，而不會截斷狀態列窗格可以顯示。  
  
### <a name="remarks"></a>備註  
 程式庫會計算文字的大小，`lpszAlmostLargeText`指定，並據以調整窗格的大小。 如果仍然無法容納在窗格中，文字會被截斷。  
  
##  <a name="a-namesetanimationlista--cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList  
 附加至狀態列窗格可用於動畫的影像清單。  
  
```  
void SetAnimationList(
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```  
  
### <a name="parameters"></a>參數  
 [in] `hBmpAnimationList`  
 指定影像清單控制代碼。  
  
 [in] `cxAnimation`  
 指定寬度，單位為像素的影像清單中的框架。  
  
 [in] `clrTransp`  
 指定映像清單中的透明色彩。  
  
 [in] `uiAnimationListResID`  
 指定映像清單中的資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果影像清單已成功連接至狀態列窗格。`FALSE`否則。  
  
##  <a name="a-namesettextaligna--cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign  
 設定狀態列窗格的標籤文字對齊方式。  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>參數  
 [in] `nAlign`  
 指定的文字對齊方式。  
  
### <a name="remarks"></a>備註  
 `nAlign`可以有下列值之一︰  
  
- `TA_LEFT`︰ 靠左對齊  
  
- `TA_CENTER:`置中對齊  
  
- `TA_RIGHT:`靠右對齊  
  
##  <a name="a-namestartanimationa--cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation  
 開始您指派給 窗格的動畫。  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFrameDelay`  
 指定動畫畫面播放速率，以毫秒為單位。  
  
 [in] `nDuration`  
 指定要播放動畫，以毫秒為單位的時間。 使用-1 為無限迴圈。  
  
### <a name="remarks"></a>備註  
 您必須指定影像清單的控制代碼，才能呼叫`StartAnimation`使用`SetAnimationList`。  
  
##  <a name="a-namestopanimationa--cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation  
 停止您指派給狀態列窗格的動畫。  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar 類別](../../mfc/reference/cmfcribbonstatusbar-class.md)

