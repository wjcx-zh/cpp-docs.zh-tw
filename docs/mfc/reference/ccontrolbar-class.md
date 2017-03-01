---
title: "CControlBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CControlBar
dev_langs:
- C++
helpviewer_keywords:
- CControlBar class
- OLE resize bars
- OLE resize bars, base class
- dialog bars, base class
- toolbars [C++], base class
- control bars [C++], base class
- status bars, base class
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
caps.latest.revision: 22
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
ms.openlocfilehash: 9720c4c11656834923c0e42a2017d51543c08f53
ms.lasthandoff: 02/24/2017

---
# <a name="ccontrolbar-class"></a>CControlBar Class
控制列類別的基底類別[CStatusBar](../../mfc/reference/cstatusbar-class.md)， [CToolBar](../../mfc/reference/ctoolbar-class.md)， [CDialogBar](../../mfc/reference/cdialogbar-class.md)， [CReBar](../../mfc/reference/crebar-class.md)，和[Coleipframewnd](../../mfc/reference/coleresizebar-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class CControlBar : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CControlBar::CControlBar](#ccontrolbar)|建構 `CControlBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|傳回做為動態的控制列的大小[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。|  
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|傳回做為控制列的大小[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。|  
|[CControlBar::CalcInsideRect](#calcinsiderect)|傳回目前的控制列區域中維度包括的框線。|  
|[CControlBar::DoPaint](#dopaint)|轉譯的框線和移駐夾的控制列。|  
|[CControlBar::DrawBorders](#drawborders)|轉譯控制項列的框線。|  
|[CControlBar::DrawGripper](#drawgripper)|呈現移駐夾的控制列。|  
|[CControlBar::EnableDocking](#enabledocking)|可讓一種控制列是停駐或浮動。|  
|[CControlBar::GetBarStyle](#getbarstyle)|擷取控制項列的樣式設定。|  
|[CControlBar::GetBorders](#getborders)|擷取控制列的邊界的值。|  
|[CControlBar::GetCount](#getcount)|傳回的非數字`HWND`控制列中的項目。|  
|[CControlBar::GetDockingFrame](#getdockingframe)|傳回的控制列停駐在框架的指標。|  
|[CControlBar::IsFloating](#isfloating)|如果有問題的控制列是浮動控制列，則傳回非零值。|  
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|呼叫命令 UI 處理常式。|  
|[CControlBar::SetBarStyle](#setbarstyle)|修改控制項的列樣式設定。|  
|[CControlBar::SetBorders](#setborders)|設定框線的值控制列。|  
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|就地變更擁有者的控制列。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CControlBar::m_bAutoDelete](#m_bautodelete)|如果是非零值，`CControlBar`終結視窗控制列時刪除物件。|  
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|控制列就地擁有者。|  
  
## <a name="remarks"></a>備註  
 控制列是通常會對齊框架視窗左邊或右邊的視窗。 它可能包含子項目，不是`HWND`為基礎的控制項，這是產生及回應 Windows 訊息或非 windows-`HWND`為基礎，這些不是視窗，並由應用程式程式碼或架構程式碼項目。 清單方塊及編輯控制項是`HWND`-根據的控制項; 狀態列窗格和點陣圖按鈕都屬於非- `HWND`-基礎控制項。  
  
 控制列 windows 通常是父框架視窗的子視窗，而通常是用戶端檢視或 MDI 框架視窗的用戶端的同層級。 A`CControlBar`物件使用父視窗的用戶端矩形的相關資訊來決定本身的位置。 接著，它會通知父視窗，並在父視窗工作區中維持未配置多少空間。  
  
 如需有關`CControlBar`，請參閱︰  
  
- [控制列](../../mfc/control-bars.md)  
  
- [技術提示 31︰ 控制列](../../mfc/tn031-control-bars.md)。  
  
-   知識庫文件 Q242577: PRB︰ 更新命令 UI 處理常式執行不工作的功能表附加至對話方塊  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="a-namecalcdynamiclayouta--ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout  
 架構會呼叫此成員函式，來計算動態工具列的維度。  
  
```  
virtual CSize CalcDynamicLayout(
    int nLength,  
    DWORD nMode);
```  
  
### <a name="parameters"></a>參數  
 `nLength`  
 所要求的控制列，以水平或垂直，取決於維度`dwMode`。  
  
 `nMode`  
 下列預先定義的旗標用來決定動態控制列的寬度與高度。 您可以使用位元 OR (|) 運算子來結合旗標。  
  
|版面配置模式旗標|其意義|  
|-----------------------|-------------------|  
|`LM_STRETCH`|指示控制列是否應該自動縮放成框架的大小。 如果無法列 （不適用於停駐） 的停駐列，集。 未設定停駐或浮動列時 （適用於停駐）。 如果設定，`LM_STRETCH`忽略`nLength`，並傳回根據維度`LM_HORZ`狀態。 `LM_STRETCH`運作方式類似`bStretch`參數中使用[CalcFixedLayout](#calcfixedlayout); 請參閱該成員函式，如需有關之間自動縮放和方向的關聯性。|  
|`LM_HORZ`|指出軸是水平或垂直方向。 設定如果橫條圖是水平方向，而且它是垂直方向，如果未設定。 `LM_HORZ`運作方式類似`bHorz`參數中使用[CalcFixedLayout](#calcfixedlayout); 請參閱該成員函式，如需有關之間自動縮放和方向的關聯性。|  
|**LM_MRUWIDTH**|最近使用的動態的寬度。 會忽略`nLength`參數，然後使用記住最近使用的寬度。|  
|`LM_HORZDOCK`|水平停駐的維度。 會忽略`nLength`參數並傳回具有最大寬度動態的大小。|  
|`LM_VERTDOCK`|垂直停駐的維度。 會忽略`nLength`參數並傳回具有最大高度動態的大小。|  
|`LM_LENGTHY`|如果設定`nLength`表示高度 （Y 方向），而不是寬度。|  
|`LM_COMMIT`|重設**LM_MRUWIDTH**浮動控制列的目前寬度。|  
  
### <a name="return-value"></a>傳回值  
 控制列的大小，單位為像素的[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以提供您自己的衍生的類別中的動態配置`CControlBar`。 MFC 類別衍生自`CControlBar`，例如[CToolbar](../../mfc/reference/ctoolbar-class.md)、 覆寫此成員函式，並提供它們自己的實作。  
  
##  <a name="a-namecalcfixedlayouta--ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout  
 呼叫此成員函式，來計算的控制列的水平大小。  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 `bStretch`  
 指出軸是否應該自動縮放成框架的大小。 `bStretch`列 （不適用於停駐） 的停駐列並不是 0 停駐或浮動時 （適用於停駐） 時，參數為非零值。  
  
 `bHorz`  
 指出軸是水平或垂直方向。 `bHorz`參數為非零，如果列是水平方向，而是 0，如果它是垂直方向。  
  
### <a name="return-value"></a>傳回值  
 控制列的大小，單位為像素的`CSize`物件。  
  
### <a name="remarks"></a>備註  
 控制列，例如工具列可以延伸水平或垂直容納按鈕包含在控制列。  
  
 如果`bStretch`是**TRUE**，延伸所提供的方向沿著維度`bHorz`。 換句話說，如果`bHorz`是**FALSE**，垂直縮放控制列。 如果`bStretch`是**FALSE**，就會發生任何自動縮放。 下表顯示可能的排列方式，以及產生的控制列樣式的`bStretch`和`bHorz`。  
  
|bStretch|bHorz|自動縮放|方向|停駐/未停駐|  
|--------------|-----------|----------------|-----------------|--------------------------|  
|**TRUE**|**TRUE**|水平縮放|水平方向|未停駐|  
|**TRUE**|**FALSE**|垂直縮放|垂直方向|未停駐|  
|**FALSE**|**TRUE**|提供沒有自動縮放|水平方向|停駐|  
|**FALSE**|**FALSE**|提供沒有自動縮放|垂直方向|停駐|  
  
##  <a name="a-namecalcinsiderecta--ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>CControlBar::CalcInsideRect  
 架構會呼叫此函式來計算工作區的控制列。  
  
```  
virtual void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 包含目前的控制列中維度包括的框線。  
  
 `bHorz`  
 指出軸是水平或垂直方向。 `bHorz`參數為非零，如果列是水平方向，而是 0，如果它是垂直方向。  
  
### <a name="remarks"></a>備註  
 繪製控制項列之前呼叫此函式。  
  
 覆寫此函式以自訂轉譯的框線和控制列的移駐夾列。  
  
##  <a name="a-nameccontrolbara--ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>CControlBar::CControlBar  
 建構 `CControlBar` 物件。  
  
```  
CControlBar();
```  
  
##  <a name="a-namedopainta--ccontrolbardopaint"></a><a name="dopaint"></a>CControlBar::DoPaint  
 要轉譯的框線和控制列的移駐夾列架構呼叫。  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 要用於轉譯的框線和控制列的移駐夾的裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 覆寫此函式以自訂繪製行為的控制列。  
  
 另一個自訂方法是覆寫`DrawBorders`和`DrawGripper`函式和加入自訂框線的移駐夾的繪圖程式碼。 因為根據預設，會呼叫這些方法`DoPaint`方法中，覆寫`DoPaint`不需要。  
  
##  <a name="a-namedrawbordersa--ccontrolbardrawborders"></a><a name="drawborders"></a>CControlBar::DrawBorders  
 要呈現控制項列的框線架構呼叫。  
  
```  
virtual void DrawBorders(
    CDC* pDC,  
    CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容，以便用來呈現的控制列框線的指標。  
  
 `rect`  
 A`CRect`物件，其中包含維度的控制列。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來自訂控制項列框線的外觀。  
  
##  <a name="a-namedrawgrippera--ccontrolbardrawgripper"></a><a name="drawgripper"></a>CControlBar::DrawGripper  
 要呈現控制項列的移駐夾架構呼叫。  
  
```  
virtual void DrawGripper(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容，以便用來呈現控制項列的移駐夾的指標。  
  
 `rect`  
 A`CRect`物件，其中包含控制列移駐夾的維度。  
  
### <a name="remarks"></a>備註  
 覆寫此函式以自訂控制項列的移駐夾的外觀。  
  
##  <a name="a-nameenabledockinga--ccontrolbarenabledocking"></a><a name="enabledocking"></a>CControlBar::EnableDocking  
 呼叫此函式會啟用停駐控制列。  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwDockStyle`  
 如果支援，請指定控制列是否支援停駐和側邊，可以停駐控制列，其父視窗。 可以是下列一或多項動作︰  
  
- `CBRS_ALIGN_TOP`可讓停駐在工作區頂端。  
  
- `CBRS_ALIGN_BOTTOM`可讓用戶端區域底部停駐。  
  
- `CBRS_ALIGN_LEFT`可讓工作區左邊停駐。  
  
- `CBRS_ALIGN_RIGHT`可讓用戶端區域右邊停駐。  
  
- `CBRS_ALIGN_ANY`可讓用戶端區域的任一邊停駐。  
  
- `CBRS_FLOAT_MULTI`可讓多個要在單一的迷你框架視窗中浮動的控制列。  
  
 如果為 0 （亦即表示沒有旗標），將不會停駐控制列。  
  
### <a name="remarks"></a>備註  
 指定的側邊必須符合其中一個已啟用在目的地框架視窗中，停駐的邊或無法至該框架視窗停駐控制列。  
  
##  <a name="a-namegetbarstylea--ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>CControlBar::GetBarStyle  
 呼叫此函式來判斷哪些**CBRS_** （控制列樣式） 目前設定的控制列。  
  
```  
DWORD GetBarStyle();
```  
  
### <a name="return-value"></a>傳回值  
 目前**CBRS_**控制列 （控制列樣式） 設定。 請參閱[CControlBar::SetBarStyle](#setbarstyle)如完整的可用樣式清單。  
  
### <a name="remarks"></a>備註  
 不會處理**WS_** （視窗樣式） 樣式。  
  
##  <a name="a-namegetbordersa--ccontrolbargetborders"></a><a name="getborders"></a>CControlBar::GetBorders  
 傳回目前的控制列的框線值。  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`CRect`物件，其中包含每一面控制列物件的目前寬度 （以像素為單位）。 例如，值`left`成員的[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，是左框線的寬度。  
  
##  <a name="a-namegetcounta--ccontrolbargetcount"></a><a name="getcount"></a>CControlBar::GetCount  
 傳回的非數字`HWND`項`CControlBar`物件。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非數字`HWND`項`CControlBar`物件。 此函數會傳回 0，表示[CDialogBar](../../mfc/reference/cdialogbar-class.md)物件。  
  
### <a name="remarks"></a>備註  
 項目的類型取決於衍生的物件︰ 窗格[CStatusBar](../../mfc/reference/cstatusbar-class.md)物件和按鈕和分隔符號為[CToolBar](../../mfc/reference/ctoolbar-class.md)物件。  
  
##  <a name="a-namegetdockingframea--ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>CControlBar::GetDockingFrame  
 呼叫此成員函式可取得目前的框架視窗的停駐控制列的指標。  
  
```  
CFrameWnd* GetDockingFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，框架視窗的指標否則**NULL**。  
  
 如果控制列未停駐在框架視窗 （也就是如果控制列浮動窗格），此函式會將指標傳回給其父代[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)。  
  
### <a name="remarks"></a>備註  
 如需可停駐控制列的詳細資訊，請參閱[CControlBar::EnableDocking](#enabledocking)和[CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。  
  
##  <a name="a-nameisfloatinga--ccontrolbarisfloating"></a><a name="isfloating"></a>CControlBar::IsFloating  
 呼叫此成員函式，以判斷是否浮動或停駐控制列。  
  
```  
BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制列浮點數; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 若要變更的狀態從一種控制列的停駐到浮點數，呼叫[CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)。  
  
##  <a name="a-namembautodeletea--ccontrolbarmbautodelete"></a><a name="m_bautodelete"></a>CControlBar::m_bAutoDelete  
 如果是非零值，`CControlBar`終結視窗控制列時刪除物件。  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>備註  
 `m_bAutoDelete`類型的公用變數**BOOL**。  
  
 控制列物件通常被內嵌於框架視窗物件。 在此情況下，`m_bAutoDelete`為 0，因為內嵌的控制列物件終結時終結框架視窗。  
  
 將此變數設為非零值，如果您配置`CControlBar`物件在堆積和您不打算呼叫**刪除**。  
  
##  <a name="a-namempinplaceownera--ccontrolbarmpinplaceowner"></a><a name="m_pinplaceowner"></a>CControlBar::m_pInPlaceOwner  
 控制列就地擁有者。  
  
```  
CWnd* m_pInPlaceOwner;  
```  
  
##  <a name="a-nameonupdatecmduia--ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI  
 此成員函式會呼叫架構，以便更新工具列或狀態列的狀態。  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pTarget`  
 應用程式的主框架視窗指標。 此指標會使用傳送更新訊息。  
  
 `bDisableIfNoHndler`  
 旗標，指出是否不有任何更新處理常式的控制項應該自動顯示為已停用。  
  
### <a name="remarks"></a>備註  
 若要更新的個別按鈕或窗格中，使用`ON_UPDATE_COMMAND_UI`中適當地設定更新處理常式的訊息對應巨集。 請參閱[ON_UPDATE_COMMAND_UI](http://msdn.microsoft.com/library/c4de3c21-2d2e-4b89-a4ce-d0c0e2d9edc4)如需有關使用這個巨集。  
  
 `OnUpdateCmdUI`是由架構呼叫，當應用程式處於閒置狀態。 框架視窗更新必須是子視窗，至少間接可見的框架視窗。 `OnUpdateCmdUI`進階可覆寫。  
  
##  <a name="a-namesetbarstylea--ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>CControlBar::SetBarStyle  
 呼叫此函式可設定需要**CBRS_**控制列的樣式。  
  
```  
void SetBarStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 控制列所需的樣式。 可以是下列一或多項動作︰  
  
- `CBRS_ALIGN_TOP`可讓框架視窗的工作區頂端停駐控制列。  
  
- `CBRS_ALIGN_BOTTOM`可讓工作區框架視窗的底部停駐控制列。  
  
- `CBRS_ALIGN_LEFT`可讓框架視窗的工作區左邊算起停駐控制列。  
  
- `CBRS_ALIGN_RIGHT`可讓框架視窗的工作區右側停駐控制列。  
  
- `CBRS_ALIGN_ANY`可讓任何一側，框架視窗的工作區的停駐控制列。  
  
- `CBRS_BORDER_TOP`會導致繪製上邊緣的控制列，就會顯示框線。  
  
- `CBRS_BORDER_BOTTOM`會導致就會顯示要繪製的控制列的下邊緣的框線。  
  
- `CBRS_BORDER_LEFT`會導致要繪製的控制列的左邊緣，就會顯示框線。  
  
- `CBRS_BORDER_RIGHT`會導致就會顯示要繪製的控制列右邊緣的框線。  
  
- `CBRS_FLOAT_MULTI`可讓多個要在單一的迷你框架視窗中浮動的控制列。  
  
- `CBRS_TOOLTIPS`會控制列所顯示的工具提示。  
  
- `CBRS_FLYBY`會更新一次以工具提示的訊息文字。  
  
- **CBRS_GRIPPER**造成移駐夾，類似於使用中的寬線的**CReBar**物件，用來繪製任何`CControlBar`-衍生的類別。  
  
### <a name="remarks"></a>備註  
 不會影響**WS_** （視窗樣式） 設定。  
  
##  <a name="a-namesetbordersa--ccontrolbarsetborders"></a><a name="setborders"></a>CControlBar::SetBorders  
 呼叫此函式可設定的控制列的框線大小。  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 *cxLeft*  
 控制列左框線的寬度 （以像素為單位）。  
  
 *cyTop*  
 控制列上框線的高度 （以像素為單位）。  
  
 *cxRight*  
 控制列右框線的寬度 （以像素為單位）。  
  
 *cyBottom*  
 控制列下框線的高度 （以像素為單位）。  
  
 `lpRect`  
 指標[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，其中包含每一種控制列物件的框線的目前寬度 （以像素為單位）。  
  
### <a name="example"></a>範例  
 下列程式碼範例會將 5 像素為單位，控制列的框線和下框線和左和右框線設定為 2 個像素︰  
  
 [!code-cpp[NVC_MFCControlLadenDialog #&61;](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]  
  
##  <a name="a-namesetinplaceownera--ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>CControlBar::SetInPlaceOwner  
 就地變更擁有者的控制列。  
  
```  
void SetInPlaceOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指標`CWnd`物件。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLBARS](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBar 類別](../../mfc/reference/ctoolbar-class.md)   
 [CDialogBar 類別](../../mfc/reference/cdialogbar-class.md)   
 [CStatusBar 類別](../../mfc/reference/cstatusbar-class.md)   
 [CReBar 類別](../../mfc/reference/crebar-class.md)

