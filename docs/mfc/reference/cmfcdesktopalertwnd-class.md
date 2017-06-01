---
title: "CMFCDesktopAlertWnd 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWnd class
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
caps.latest.revision: 33
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: be9d81ffff003119aa7ff9e0cd100c575bd82d36
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class
`CMFCDesktopAlertWnd`類別實作來通知使用者有關的事件在螢幕上會出現非強制回應對話方塊的功能。  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>語法  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCDesktopAlertWnd::Create](#create)|建立並初始化桌面警示視窗。|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|傳回的動畫速度。|  
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|傳回的動畫類型。|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|傳回自動關閉逾時。|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|傳回標題的高度。|  
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||  
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|傳回在螢幕上的桌面警示視窗的最後一個有效位置。|  
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|傳回的透明度。|  
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|決定是否要將桌面警示視窗顯示小型的標題。|  
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|當使用者按一下位於桌面的警示 功能表上的連結按鈕，由架構呼叫。|  
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|當使用者會選取功能表上，從項目或快速鍵按鍵會轉譯子控制項來傳送通知訊息時，架構會呼叫此成員函式。 (覆寫[CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand)。)|  
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||  
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|設定新的動畫速度。|  
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|設定動畫類型。|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|設定自動關閉逾時。|  
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|小型和一般標題之間切換。|  
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|設定透明度層級。|  
  
## <a name="remarks"></a>備註  
 桌面警示視窗可以穿透可以出現的動畫效果，就會消失 （指定的延遲之後或在使用者按一下 [關閉] 按鈕結束後）。  
  
 桌面警示視窗也可以包含預設值 對話方塊，依序包含圖示、 訊息文字 （標籤） 和連結。 另外，桌面警示視窗可以包含從應用程式資源的自訂對話方塊。  
  
 您可以建立桌面警示視窗分成兩個步驟。 首先，呼叫建構函式來建構`CMFCDesktopAlertWnd`物件。 其次，呼叫[CMFCDesktopAlertWnd::Create](#create)成員函式來建立視窗，並將其附加至`CMFCDesktopAlertWnd`物件。  
  
 `CMFCDesktopAlertWnd`物件會建立特殊子對話方塊用來填滿的桌面警示視窗工作區。 對話方塊擁有會放置在其的所有控制項。  
  
 若要顯示自訂對話方塊上的快顯視窗，請遵循下列步驟︰  
  
1.  從 `CMFCDesktopAlertDialog` 衍生類別。  
  
2.  建立子對話方塊範本資源中。  
  
3.  呼叫[CMFCDesktopAlertWnd::Create](#create)使用對話方塊範本和衍生類別的執行階段類別資訊的指標的資源識別碼。  
  
4.  程式可直接處理這些通知的裝載的控制項或程式可處理來自裝載控制項的所有通知的自訂對話方塊。  
  
 您可以使用下列函式來控制桌面警示視窗的行為︰  
  
-   藉由呼叫設定動畫類型[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)。 有效選項包括展開、 投影片，及淡出。  
  
-   藉由呼叫設定動畫畫面格速度[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)。  
  
-   透過呼叫所設定的透明度[CMFCDesktopAlertWnd::SetTransparency](#settransparency)。  
  
-   變更標題的大小太小，藉由呼叫[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)。 小標題是 7 個像素高。  
  
## <a name="example"></a>範例  
 下列範例說明如何使用各種方法的`CMFCDesktopAlertWnd`類別來設定`CMFCDesktopAlertWnd`物件。 此範例示範如何設定動畫類型、 設定快顯視窗的透明度，指定 警示 視窗會顯示小型的標題，以及設定警示 視窗會自動關閉之前經過的時間。 此範例也示範如何建立和初始化桌面警示視窗。 此程式碼片段是一部分[桌面警示示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo #&1;](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxDesktopAlertWnd.h  
  
##  <a name="create"></a>CMFCDesktopAlertWnd::Create  
 建立並初始化桌面警示視窗。  
  
```  
virtual BOOL Create(
    CWnd* pWndOwner,  
    UINT uiDlgResID,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1),  
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

 
virtual BOOL Create(
    CWnd* pWndOwner,  
    CMFCDesktopAlertWndInfo& params,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1));
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pWndOwner`  
 指定 [警示] 視窗的擁有者。 該擁有者將收到桌面警示視窗的所有通知。 這個值不能是 `NULL`。  
  
 [in] `uiDlgResID`  
 指定 [警示] 視窗中的資源識別碼。  
  
 [in] `hMenu`  
 指定當使用者按一下 [功能表] 按鈕會顯示的功能表。 如果`NULL`，不會顯示功能表按鈕。  
  
 [in] `ptPos`  
 指定的初始位置，其中會顯示 [警示] 視窗中，使用螢幕座標。 如果此參數為 （-1，-1），[警示] 視窗會顯示在螢幕的右下角。  
  
 [in] `pRTIDlgBar`  
 [警示] 視窗工作區包含自訂的對話方塊類別的執行階段類別資訊。  
  
 [in] `params`  
 指定用來建立警示 視窗中的參數。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 [警示] 視窗建立可順利啟動。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來建立警示的視窗。 [警示] 視窗的工作區包含子對話方塊顯示給使用者的所有控制項的裝載。  
  
 第一個方法多載會建立警示視窗，其中包含從應用程式的資源載入子對話方塊。 第一個方法多載也可以指定自訂的對話方塊類別的執行階段類別資訊。  
  
 第二個方法多載會建立警示視窗，其中包含預設控制項。 您可以指定要修改顯示哪些控制項[CMFCDesktopAlertWndInfo 類別](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)。  
  
##  <a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed  
 傳回的動畫速度。  
  
```  
UINT GetAnimationSpeed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [警示] 視窗中，以毫秒為單位的動畫的速度。  
  
### <a name="remarks"></a>備註  
 動畫速度描述 [警示] 視窗中開啟和關閉的速度。  
  
##  <a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType  
 傳回的動畫類型。  
  
```  
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```  
  
### <a name="return-value"></a>傳回值  
 下列的動畫類型其中一項︰  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime  
 傳回自動關閉逾時。  
  
```  
int GetAutoCloseTime() const;  
```  
  
### <a name="return-value"></a>傳回值  
 時間 （毫秒） 之後，[警示] 視窗會自動關閉。  
  
### <a name="remarks"></a>備註  
 使用這個方法來判斷 [警示] 視窗會自動關閉之前，應該經過多少時間。  
  
##  <a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight  
 傳回標題的高度。  
  
```  
virtual int GetCaptionHeight();
```  
  
### <a name="return-value"></a>傳回值  
 高度，單位為像素的標題。  
  
### <a name="remarks"></a>備註  
 可以在衍生類別中覆寫這個方法。 預設實作其中一個︰ 如果小標題或從 Windows API 函式取得的值顯示快顯視窗，則會傳回小標題的高度值 （7 個像素） `GetSystemMetrics(SM_CYSMCAPTION)`。  
  
##  <a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos  
 傳回最後一個位置的桌面警示視窗在螢幕上。  
  
```  
CPoint GetLastPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 螢幕座標中的點。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回在螢幕上的 [警示] 視窗中的最後一個有效位置。  
  
##  <a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency  
 傳回的透明度。  
  
```  
BYTE GetTransparency() const;  
```  
  
### <a name="return-value"></a>傳回值  
 介於 0 和 255 之間的透明度。 值愈大、 更多的不透明視窗。  
  
### <a name="remarks"></a>備註  
 使用這個方法來擷取目前的 [警示] 視窗的透明度等級。  
  
##  <a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption  
 決定桌面警示視窗有小型的標題或一般大小標題。  
  
```  
BOOL HasSmallCaption() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果快顯視窗會顯示小型的標題。`FALSE`如果一般大小的標題以顯示快顯視窗。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法來判斷快顯視窗是否有小型的標題或一般大小標題。 根據預設，小標題是 7 個像素高。 您可以藉由呼叫 Windows API 函式來取得一般大小標題的高度`GetSystemMetrics(SM_CYCAPTION)`。  
  
##  <a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow  

  
```  
virtual BOOL OnBeforeShow(CPoint&);
```  
  
### <a name="parameters"></a>參數  
 [in] `CPoint&`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton  
 當使用者按一下位於桌面的警示 功能表上的連結按鈕，由架構呼叫。  
  
```  
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 一定是 `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果您想要在使用者按一下 [警示] 視窗中的連結時收到通知，請覆寫這個方法在衍生類別中。  
  
##  <a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand  

  
```  
virtual BOOL OnCommand(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in] `wParam`  
 [in] `lParam`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand  

  
```  
BOOL ProcessCommand(HWND hwnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `hwnd`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed  
 設定新的動畫速度。  
  
```  
void SetAnimationSpeed(UINT nSpeed);
```  
  
### <a name="parameters"></a>參數  
 [in] `nSpeed`  
 指定新動畫的速度，以毫秒為單位。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來設定警示的視窗動畫速度。 預設的動畫速度為 30 毫秒。  
  
##  <a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType  
 設定動畫類型。  
  
```  
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```  
  
### <a name="parameters"></a>參數  
 [in] `type`  
 指定的動畫類型。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來設定動畫類型。 您可以指定下列其中一個值：  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime  
 設定自動關閉逾時。  
  
```  
void SetAutoCloseTime(int nTime);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTime`  
 時間 （毫秒），經過之前會自動關閉警示 視窗。  
  
### <a name="remarks"></a>備註  
 如果使用者不會與視窗互動，[警示] 視窗會自動關閉指定的時間之後。  
  
##  <a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption  
 小型和一般大小標題之間切換。  
  
```  
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSmallCaption`  
 `TRUE`若要指定 [警示] 視窗會顯示小型的標題。否則，`FALSE`指定 [警示] 視窗會顯示一般大小的標題。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以顯示小型或一般大小的標題。 根據預設，小標題是 7 個像素高。 您可以藉由呼叫 Windows API 函式來取得一般標題大小`GetSystemMetrics(SM_CYCAPTION)`。  
  
##  <a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency  
 設定快顯視窗的透明度。  
  
```  
void SetTransparency(BYTE nTransparency);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTransparency`  
 指定透明度層級。 此值必須介於 0 和 255 之間。 值愈大、 更多的不透明視窗。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可設定的快顯視窗的透明度。  
  
##  <a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize  

  
```  
virtual CSize GetDialogSize();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWndInfo 類別](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)

