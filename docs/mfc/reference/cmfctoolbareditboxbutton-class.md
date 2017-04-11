---
title: "CMFCToolBarEditBoxButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarEditBoxButton class
- SetACCData method
- OnCalculateSize method
- OnDraw method
- OnDrawOnCustomizeList method
- Serialize method
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
caps.latest.revision: 28
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 4334dfc7074cd55173af15cc1fab59882c9e8e6c
ms.lasthandoff: 04/04/2017

---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton 類別
包含編輯控制項的工具列按鈕 ( [CEdit 類別](../../mfc/reference/cedit-class.md))。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarEditBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|建構 `CMFCToolBarEditBoxButton` 物件。|  
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|指定使用者是否可以在自訂期間延伸按鈕。 (覆寫[CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|  
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|將另一個工具列按鈕的內容複製到目前的按鈕。 (覆寫[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::CreateEdit](#createedit)|建立新的編輯控制項中的按鈕。|  
|`CMFCToolBarEditBoxButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|擷取第一個`CMFCToolBarEditBoxButton`中具有指定之命令識別碼的應用程式物件|  
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|擷取控制項文字的第一個編輯方塊工具列具有指定的命令識別碼。|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|擷取與按鈕相關聯的捷徑功能表的資源識別碼。|  
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|擷取週框的編輯方塊按鈕的編輯部分。|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|傳回的指標按鈕中內嵌之編輯控制項。|  
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|擷取工具列按鈕與相關聯的視窗控制代碼。 (覆寫[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|擷取用戶端必須重繪按鈕區域的區域。 (覆寫[CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)。)|  
|`CMFCToolBarEditBoxButton::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|決定是否要在使用者按一下按鈕時，顯示按鈕的框線。 (覆寫[CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|  
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|判斷編輯方塊按鈕是否有平面的樣式。|  
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|指定是否要處理按鈕[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息。 (覆寫[CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|加入按鈕時由架構呼叫**自訂** 對話方塊。 (覆寫[CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|由架構呼叫以計算指定之裝置內容和停駐狀態的按鈕的大小。 (覆寫[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|插入新的工具列按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|  
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|當使用者按一下滑鼠按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|  
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|為父工具列處理時，由架構呼叫`WM_CTLCOLOR`訊息。 (覆寫[CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|  
|`CMFCToolBarEditBoxButton::OnDraw`|由架構呼叫以繪製按鈕，使用指定的樣式和選項。 (覆寫[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|由架構呼叫以繪製按鈕**命令**窗格**自訂** 對話方塊。 (覆寫[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|當全域字型變更時由架構呼叫。 (覆寫[CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|  
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|為父工具列移動時由架構呼叫。 (覆寫[CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|  
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|由架構呼叫時，按鈕會變成可見或不可見。 (覆寫[CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|  
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|為父工具列變更它的大小或位置，這項變更會使按鈕將大小變更時由架構呼叫。 (覆寫[CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|為父工具列更新其工具提示文字時，由架構呼叫。 (覆寫[CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|  
|`CMFCToolBarEditBoxButton::Serialize`|從封存讀取此物件，或將它寫入至封存。 (覆寫[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|  
|`CMFCToolBarEditBoxButton::SetACCData`|填入提供`CAccessibilityData`物件從工具列按鈕的協助工具資料。 (覆寫[CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)。)|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|設定中的文字編輯控制項的按鈕。|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|尋找具有指定的命令 ID，並設定按鈕的編輯控制項中的文字編輯控制項按鈕。|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|指定的資源識別碼與按鈕相關聯的快顯功能表。|  
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|應用程式中指定編輯方塊按鈕的平面樣式的外觀。|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|指定按鈕的樣式。 (覆寫[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|  
  
## <a name="remarks"></a>備註  
 若要編輯方塊按鈕加入工具列，請遵循下列步驟︰  
  
 1. 為父工具列資源的按鈕保留假的資源 ID。  
  
 2. 建構`CMFCToolBarEditBoxButton`物件。  
  
 3. 在訊息處理常式來處理`AFX_WM_RESETTOOLBAR`訊息，請使用新的下拉式方塊按鈕取代 dummy 按鈕[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
 如需詳細資訊，請參閱[逐步解說︰ 將工具列控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCToolBarEditBoxButton`類別。 此範例示範如何指定使用者可以延伸按鈕進行自訂時，指定當使用者按一下按鈕時，會顯示按鈕的框線、 設定文字方塊控制項中的文字、 在應用程式中指定的編輯方塊按鈕的平面樣式外觀，而且指定工具列編輯方塊控制項的樣式。  
  
 [!code-cpp[NVC_MFC_RibbonApp # 40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 `CMFCToolBarEditBoxButton` 
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbareditboxbutton.h  
  
##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched  
 指定使用者是否可以在自訂期間延伸按鈕。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此方法會傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 根據預設，架構不允許使用者在自訂期間 stretch 工具列按鈕。 此方法擴充的基底類別實作 ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) 允許使用者以進行自訂時延伸編輯方塊 工具列按鈕。  
  
##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton  
 建構[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)物件。  
  
```  
CMFCToolBarEditBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=ES_AUTOHSCROLL,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 指定控制項 id。  
  
 [in] `iImage`  
 指定工具列影像的以零為起始的索引。 映像位於[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別會維護。  
  
 [in] `dwStyle`  
 指定的編輯控制項的樣式。  
  
 [in] `iWidth`  
 編輯控制項的像素為單位指定寬度。  
  
### <a name="remarks"></a>備註  
 預設建構函式會將編輯控制項樣式設定為下列組合︰  
  
 `WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL`  
  
 控制項的預設寬度是 150 個像素。  
  
##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom  
 將另一個工具列按鈕的內容複製到目前的按鈕。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
 要從中複製來源 按鈕參考。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，將另一個工具列按鈕複製到此工具列按鈕。 `src`必須是型別`CMFCToolBarEditBoxButton`。  
  
##  <a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit  
 建立新的編輯控制項中的按鈕。  
  
```  
virtual CEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `[in] pWndParent`  
 指定編輯控制項的父視窗。 它不得為 NULL。  
  
 `[in] rect`  
 指定編輯控制項的大小和位置。  
  
### <a name="return-value"></a>傳回值  
 變數的指標，新建的編輯控制項。它是`NULL`如果控制項的建立和附加檔案失敗。  
  
### <a name="remarks"></a>備註  
 您建構`CMFCToolBarEditBoxButton`兩個步驟中的物件。 第一次呼叫建構函式，然後再呼叫`CreateEdit`，建立 Windows 編輯控制項，並將它附加至`CMFCToolBarEditBoxButton`物件。  
  
##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd  
 擷取第一個`CMFCToolBarEditBoxButton`中具有指定之命令識別碼的應用程式物件  
  
```  
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 要擷取按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 第一個`CMFCToolBarEditBoxButton`具有指定的命令 ID，在應用程式中的物件或`NULL`如果物件不存在。  
  
### <a name="remarks"></a>備註  
 這類的方法使用這個共用公用程式方法是[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)和[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)設定或取得具有指定的命令識別碼。 第一個編輯方塊工具列控制項的文字  
  
##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll  
 擷取控制項文字的第一個編輯方塊工具列具有指定的命令識別碼。  
  
```  
static CString __stdcall GetContentsAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 要從中擷取內容 按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含具有指定的命令識別碼。 第一個編輯方塊工具列控制項的文字  
  
### <a name="remarks"></a>備註  
 這個方法會傳回空字串，如果沒有`CMFCToolBarEditBoxButton`物件具有指定的命令識別碼。  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID  
 擷取與按鈕相關聯的捷徑功能表的資源識別碼。  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>傳回值  
 當按鈕沒有相關聯的捷徑功能表時，按鈕或 0 相關聯的捷徑功能表資源識別碼。  
  
### <a name="remarks"></a>備註  
 架構會使用的資源 ID。 當使用者以滑鼠右鍵按一下按鈕建立快顯功能表。  
  
##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder  
 擷取週框的編輯方塊按鈕的編輯部分。  
  
```  
virtual void GetEditBorder(CRect& rectBorder);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectBorder`  
 若要參考`CRect`接收的週框物件。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取用戶端座標中的編輯控制項的週框矩形。 其中一個像素詳述每個方向矩形的大小。  
  
 [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder)方法會呼叫這個方法，當它繪製周圍的框線時`CMFCToolBarEditBoxButton`物件。  
  
##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox  
 將指標傳回至[CEdit 類別](../../mfc/reference/cedit-class.md)按鈕中內嵌的控制項。  
  
```  
CEdit* GetEditBox() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CEdit 類別](../../mfc/reference/cedit-class.md)包含按鈕控制項。 它是`NULL`如果`CEdit`控制項尚未建立。  
  
### <a name="remarks"></a>備註  
 您建立`CEdit`藉由呼叫控制項[CMFCToolBarEditBoxButton::CreateEdit](#createedit)。  
  
##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd  
 擷取工具列按鈕與相關聯的視窗控制代碼。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>傳回值  
 視窗控制代碼與按鈕相關聯。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法藉由傳回編輯控制項組件的編輯方塊按鈕的視窗控制代碼。  
  
##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect  
 擷取用戶端必須重繪按鈕區域的區域。  
  
```  
virtual const CRect GetInvalidateRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`CRect`物件，指定必須重新繪製的區域。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作， [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)，藉由在區域中的文字標籤的區域。  
  
##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder  
 決定是否要在使用者按一下按鈕時，顯示按鈕的框線。  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按鈕會顯示其框線時選取; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作， [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)，藉由傳回非零值，如果控制項為可見。  
  
##  <a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode  
 判斷編輯方塊按鈕是否有平面的樣式。  
  
```  
static BOOL __stdcall IsFlatMode();
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕具有一般的樣式，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，編輯方塊按鈕有平面的樣式。 使用[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)方法，以變更您的應用程式的平面樣式外觀。  
  
##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand  
 指定是否要處理按鈕[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>參數  
 [in] `iNotifyCode`  
 與命令相關聯的通知訊息。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕處理`WM_COMMAND`訊息，或`FALSE`表示為父工具列必須處理訊息。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，當它是傳送[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)父視窗的訊息。  
  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) 藉由處理[EN_UPDATE](http://msdn.microsoft.com/library/windows/desktop/bb761687)通知。 每個具有相同的命令 ID，與此物件的 [編輯] 方塊中，它會設定其文字標籤到此物件的文字標籤。  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage  
 加入按鈕時由架構呼叫**自訂** 對話方塊。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) 複製任何具有相同的命令識別碼與此物件的工具列中的編輯方塊控制項的屬性。 如果沒有工具列有具有相同的命令識別碼與此物件的編輯方塊控制項，這個方法任何作用。  
  
 如需有關**自訂**對話方塊中，請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd  
 插入新的工具列按鈕時由架構呼叫。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 新的父視窗的指標。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 重新建立內部`CEdit`物件。  
  
##  <a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick  
 當使用者按一下滑鼠按鈕時由架構呼叫。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 未使用。  
  
 [in] `bDelay`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 如果按鈕處理按一下的訊息; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) 藉由傳回非零值，如果內部`CEdit`物件為可見。  
  
##  <a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor  
 為父工具列處理時，由架構呼叫`WM_CTLCOLOR`訊息。  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容顯示的按鈕。  
  
 [in] `nCtlColor`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 全域視窗的筆刷控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) 透過分別將提供的裝置內容的文字和背景色彩設定為全域的文字和背景色彩。  
  
 如需全域選項，可用於您的應用程式的詳細資訊，請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged  
 當全域字型變更時由架構呼叫。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) 的全域字型變更控制項的字型。  
  
 如需全域選項，可用於您的應用程式的詳細資訊，請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。  
  
##  <a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove  
 為父工具列移動時由架構呼叫。  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫預設類別實作 ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) 藉由更新內部的位置`CEdit`物件  
  
##  <a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow  
 由架構呼叫時，按鈕會變成可見或不可見。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
 指定按鈕是否可見。 如果這個參數是`TRUE`，按鈕會顯示。 否則，按鈕看不到。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) 來顯示按鈕`bShow`是`TRUE`。 否則，這個方法會隱藏按鈕。  
  
##  <a name="onsize"></a>CMFCToolBarEditBoxButton::OnSize  
 為父工具列變更它的大小或位置，這項變更會使按鈕將大小變更時由架構呼叫。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>參數  
 [in] `iSize`  
 新按鈕，像素為單位的寬度。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫預設類別實作、 [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)，藉由更新的大小和位置的內部`CEdit`物件。  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip  
 為父工具列更新其工具提示文字時，由架構呼叫。  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 未使用。  
  
 [in] `iButtonIndex`  
 未使用。  
  
 [in] `wndToolTip`  
 在顯示工具提示文字的控制項。  
  
 [輸出] `str`  
 A`CString`接收更新的工具提示文字的物件。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果此方法來更新的工具提示文字。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) 藉由顯示按鈕的編輯部分相關聯的工具提示文字。 如果內部`CEdit`物件是`NULL`視窗控制代碼或`CEdit`物件無法識別現有的視窗，這個方法不做任何動作，並傳回`FALSE`。  
  
##  <a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents  
 設定文字方塊控制項的文字。  
  
```  
virtual void SetContents(const CString& sContents);
```  
  
### <a name="parameters"></a>參數  
 `[in] sContents`  
 指定要設定的新文字。  
  
##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll  
 尋找[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)有指定的命令 ID，而且指定的文字設定其文字方塊內的物件。  
  
```  
static BOOL SetContentsAll(
    UINT uiCmd,  
    const CString& strContents);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 指定控制項變更文字的命令的識別碼。  
  
 [in] `strContents`  
 指定要設定的新文字。  
  
### <a name="return-value"></a>傳回值  
 設定文字; 如果為非零0 代表`CMFCToolBarEditBoxButton`與指定的命令 ID 的控制項不存在。  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID  
 指定的資源識別碼與按鈕相關聯的快顯功能表。  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 快顯功能表資源識別碼。  
  
### <a name="remarks"></a>備註  
 架構會使用的資源 ID。 當使用者以滑鼠右鍵按一下工具列按鈕建立快顯功能表。  
  
##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode  
 應用程式中指定編輯方塊按鈕的平面樣式的外觀。  
  
```  
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bFlat`  
 編輯方塊按鈕平面樣式。 如果這個參數是`TRUE`的平面樣式外觀會啟用，否則停用的平面樣式外觀。  
  
### <a name="remarks"></a>備註  
 編輯方塊按鈕的預設一般樣式是`TRUE`。 使用[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)方法來擷取您的應用程式的平面樣式外觀。  
  
##  <a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle  
 指定編輯方塊控制項的工具列的樣式。  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `nStyle`  
 若要設定新的樣式。  
  
### <a name="remarks"></a>備註  
 這個方法會設定[CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)至`nStyle`它也會停用在文字方塊中，當應用程式為自訂模式，並讓它無法自訂模式應用程式時 (請參閱[CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode)和[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))。 請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)如需有效的樣式旗標的清單。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)




