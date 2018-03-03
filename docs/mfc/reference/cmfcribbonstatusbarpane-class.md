---
title: "CMFCRibbonStatusBarPane 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3d5059adf0ebbd1ed651d57354ae73beadb919f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane 類別
`CMFCRibbonStatusBarPane`類別實作可以加入功能區狀態列的功能區項目。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|建構並初始化 `CMFCRibbonStatusBarPane` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|傳回定義而不會截斷 窗格中可顯示的最長的文字字串的字串。|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|傳回目前的文字對齊方式的設定。|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|判斷動畫是否正在進行中。|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|決定是否要將窗格位於功能區狀態列擴充區域中。|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(覆寫[CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder)。)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(覆寫[CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)。)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|定義可以而不會截斷窗格中顯示的最長的文字字串。|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|指派給 窗格可用於動畫的影像清單。|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|設定文字對齊方式。|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|開始指派給 [] 窗格中的動畫。|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|停止動畫指派給 窗格。 。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|指派給 [] 窗格中的動畫停止時由架構呼叫。|  
  
## <a name="example"></a>範例  
 下列範例示範如何在 `CMFCRibbonStatusBarPane` 類別中使用各種方法。 此範例示範如何建構`CMFCRibbonStatusBarPane`物件，設定狀態列窗格的標籤的文字對齊方式，定義可顯示在 [狀態] 列窗格，而不會截斷、 附加到狀態列窗格可用於影像清單的最長文字nimation，並啟動動畫。  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
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
 [輸入] `nCmdID`  
 指定命令 ID 的窗格。  
  
 [輸入] `lpszText`  
 指定要在窗格中顯示的文字字串。  
  
 [輸入] `bIsStatic`  
 如果`TRUE`，無法反白顯示或按一下選取 [狀態] 窗格。  
  
 [輸入] `hIcon`  
 指定要在窗格中顯示的圖示的控制代碼。  
  
 [輸入] `lpszAlmostLargeText`  
 指定的最長的文字字串，可顯示的窗格。  
  
 [輸入] `hBmpAnimationList`  
 指定將用於動畫的影像清單控制代碼。  
  
 [輸入] `cxAnimation`  
 指定的寬度，單位為像素用於動畫的影像清單中的圖示。  
  
 [輸入] `clrTrnsp`  
 指定用於動畫的影像清單中的影像的透明色彩。  
  
 [輸入] `uiAnimationListResID`  
 指定用於動畫的影像清單的資源識別碼。  
  
##  <a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText  
 取得狀態列窗格可以顯示的最長的文字字串。  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 狀態列窗格可以顯示的最長文字字串。  
  
##  <a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign  
 取得目前狀態列窗格的標籤的文字對齊方式的設定。  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的文字對齊方式可以是下列其中之一：  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT。  
  
##  <a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation  
 判斷動畫是否正在進行中。  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果動畫正在進行中，`FALSE`否則。  
  
##  <a name="isextended"></a>CMFCRibbonStatusBarPane::IsExtended  
 決定是否要將窗格位於功能區狀態列擴充區域中。  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格上狀態列擴充區域中。 否則為 `FALSE`。  
  
##  <a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `CDC*`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation  
 指派給 [] 窗格中的動畫結束時，架構會呼叫這個方法。  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>備註  
 `StopAnimation`方法會呼叫`OnFinishAnimation`方法，您可以使用來清理資料，當動畫的結束。  
  
##  <a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText  
 定義可顯示在 [狀態] 列窗格，而不會截斷的最長文字。  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszAlmostLargeText`  
 指定的最長的字串，而不會截斷狀態列窗格可以顯示。  
  
### <a name="remarks"></a>備註  
 程式庫會計算文字的大小，`lpszAlmostLargeText`指定並據以調整窗格的大小。 如果仍然無法容納在窗格中，文字會被截斷。  
  
##  <a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList  
 附加到狀態列窗格可用於動畫的影像清單。  
  
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
 [輸入] `hBmpAnimationList`  
 指定影像清單控制代碼。  
  
 [輸入] `cxAnimation`  
 指定的寬度，單位為像素的影像清單中的框架。  
  
 [輸入] `clrTransp`  
 指定的影像清單的透明色彩。  
  
 [輸入] `uiAnimationListResID`  
 指定的影像清單的資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果影像清單已成功附加至狀態列窗格;`FALSE`否則。  
  
##  <a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign  
 設定狀態列窗格的標籤的文字對齊方式。  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nAlign`  
 指定的文字對齊方式。  
  
### <a name="remarks"></a>備註  
 `nAlign`可以有下列值之一：  
  
- `TA_LEFT`： 靠左對齊  
  
- `TA_CENTER:`置中對齊  
  
- `TA_RIGHT:`靠右對齊  
  
##  <a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation  
 開始您指派給 [] 窗格中的動畫。  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nFrameDelay`  
 指定動畫畫面播放速率，以毫秒為單位。  
  
 [輸入] `nDuration`  
 指定要播放動畫，以毫秒為單位的時間長度。 使用-1 為無限迴圈。  
  
### <a name="remarks"></a>備註  
 您必須先呼叫指定的影像清單控制代碼`StartAnimation`使用`SetAnimationList`。  
  
##  <a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation  
 停止您指派給狀態列窗格的動畫。  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar 類別](../../mfc/reference/cmfcribbonstatusbar-class.md)
