---
title: CMFCDropDownToolbarButton 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c65cf3070f199b013a0e85c1ae56764174fdc33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372530"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 類別
按一下時其行為像一般按鈕的工具列按鈕類型。 不過，它會開啟下拉式工具列 ( [CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)如果使用者按住工具列按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|建構 `CMFCDropDownToolbarButton` 物件。|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|將另一個工具列按鈕的內容複製到目前的按鈕。 (覆寫[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|  
|`CMFCDropDownToolbarButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|會開啟下拉式工具列。|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|複製文字從工具列按鈕加入的功能表。 (覆寫[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)。)|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|擷取與按鈕相關聯的下拉式清單工具列。|  
|`CMFCDropDownToolbarButton::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|判斷是否為目前開啟下拉式工具列。|  
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|決定是否可以使用擴充的框線顯示按鈕。 (覆寫[CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。)|  
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|由架構呼叫以計算指定之裝置內容和停駐狀態的按鈕的大小。 (覆寫[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|  
|`CMFCDropDownToolbarButton::OnCancelMode`|由架構呼叫以處理[WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615)訊息。 (覆寫 `CMCToolBarButton::OnCancelMode`。)|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|插入新的工具列按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|  
|[CMFCDropDownToolbarButton::OnClick](#onclick)|當使用者按一下滑鼠按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|  
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|當使用者放開滑鼠按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)。)|  
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|為父工具列處理時，由架構呼叫`WM_HELPHITTEST`訊息。 (覆寫[CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)。)|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|當應用程式為父工具列上顯示捷徑功能表，請修改提供的功能表。 (覆寫[CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)。)|  
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|由架構呼叫以繪製按鈕，使用指定的樣式和選項。 (覆寫[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由架構呼叫以繪製按鈕**命令**窗格**自訂** 對話方塊。 (覆寫[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|  
|[CMFCDropDownToolbarButton::Serialize](#serialize)|從封存讀取此物件，或將它寫入至封存。 (覆寫[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|設定當使用者按一下按鈕時，架構會使用的預設命令。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|指定使用者必須按住滑鼠按鈕才會出現下拉式工具列的時間的長度。|  
  
## <a name="remarks"></a>備註  
 A`CMFCDropDownToolBarButton`不同於一般的按鈕，它有按鈕右下角的小箭號。 在使用者從下拉式清單工具列選取按鈕之後，架構會顯示它的圖示上最上層工具列按鈕 （在右下角的小箭號按鈕）。  
  
 如需如何實作下拉式工具列的資訊，請參閱[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)。  
  
 `CMFCDropDownToolBarButton`物件可以匯出到[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件，並顯示為快顯功能表的功能表按鈕。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdropdowntoolbar.h  
  
##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom  
 將另一個工具列按鈕的內容複製到目前的按鈕。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `src`  
 要從中複製來源 按鈕參考。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，將另一個工具列按鈕複製到此工具列按鈕。 `src` 必須是型別`CMFCDropDownToolbarButton`。  
  
##  <a name="cmfcdropdowntoolbarbutton"></a>  CMFCDropDownToolbarButton::CMFCDropDownToolbarButton  
 建構 `CMFCDropDownToolbarButton` 物件。  
  
```  
CMFCDropDownToolbarButton();

 
CMFCDropDownToolbarButton(
    LPCTSTR lpszName,  
    CMFCDropDownToolBar* pToolBar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszName`  
 按鈕的預設文字。  
  
 [輸入] `pToolBar`  
 指標`CMFCDropDownToolBar`使用者按下按鈕時顯示的物件。  
  
### <a name="remarks"></a>備註  
 建構函式的第二個多載將複製到下拉式按鈕的第一個按鈕從工具列的`pToolBar`指定。  
  
 一般而言，下拉式清單工具列按鈕會從最近使用過的按鈕文字使用工具列中，`pToolBar`指定。 它會使用所指定的文字`lpszName`按鈕時轉換成功能表按鈕或顯示在**命令** 索引標籤**自訂** 對話方塊。 如需有關**自訂**對話方塊中，請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCDropDownToolbarButton`類別。 此程式碼片段是部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]  
  
##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar  
 會開啟下拉式工具列。  
  
```  
BOOL DropDownToolbar(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 父視窗的下拉式清單畫面格，或`NULL`使用下拉式工具列按鈕的父視窗。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果方法成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
 [CMFCDropDownToolbarButton::OnClick](#onclick)方法會呼叫這個方法，以開啟下拉式工具列，當使用者按住工具列按鈕。  
  
 這個方法會使用建立下拉式工具列[CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create)方法。 如果父工具列停駐垂直，這個方法會將下拉式工具列到為父工具列，根據調整大小的左手或右手邊端。 否則，這個方法會將為父工具列下方的下拉式清單工具列。  
  
 如果這個方法會失敗`pWnd`是`NULL`而下拉式工具列按鈕並沒有父視窗。  
  
##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton  
 複製文字從工具列按鈕加入的功能表。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `menuButton`  
 目標功能表按鈕的參考。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫基底類別實作 ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton))，然後附加目標功能表按鈕的快顯功能表包含此按鈕中的每個工具列功能表項目。 這個方法不會將子功能表附加至快顯功能表。  
  
 這個方法會失敗，如果父工具列`m_pToolBar`，是`NULL`或基底類別實作會傳回`FALSE`。  
  
##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar  
 擷取與按鈕相關聯的下拉式清單工具列。  
  
```  
CMFCToolBar* GetDropDownToolBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式清單工具列按鈕與相關聯。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`m_pToolBar`資料成員。  
  
##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown  
 判斷是否為目前開啟下拉式工具列。  
  
```  
BOOL IsDropDown() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果下拉式清單工具列目前已開啟; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 架構會藉由開啟下拉式工具列[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)方法。 當使用者按下下拉式工具列的非工作區左邊滑鼠按鈕時，架構就會關閉下拉式工具列。  
  
##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize  
 決定是否可以使用擴充的框線顯示按鈕。  
  
```  
virtual BOOL IsExtraSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果工具列按鈕可以顯示擴充的框線; 具有非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 如需擴充框線的詳細資訊，請參閱[CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。  
  
##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay  
 指定使用者必須按住滑鼠按鈕才會出現下拉式工具列的時間的長度。  
  
```  
static UINT m_uiShowBarDelay;  
```  
  
### <a name="remarks"></a>備註  
 以毫秒為單位的延遲時間。 預設值為 500。 您可以藉由變更這個共用的資料成員的值設定另一個的延遲。  
  
##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize  
 由架構呼叫以計算指定之裝置內容和停駐狀態的按鈕的大小。  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容顯示的按鈕。  
  
 [輸入] `sizeDefault`  
 按鈕的預設大小。  
  
 [輸入] `bHorz`  
 為父工具列停駐狀態。 這個參數是`TRUE`工具列水平停駐或浮動，如果或`FALSE`若垂直停駐工具列。  
  
### <a name="return-value"></a>傳回值  
 A`SIZE`結構，其中包含按鈕，像素為單位的維度。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) 所加入按鈕大小的水平維度中的下拉箭號的寬度。  
  
##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd  
 插入新的工具列按鈕時由架構呼叫。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndParent`  
 新的父視窗。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 藉由清除文字標籤 ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) 和設定[CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext)和[CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton)資料成員`FALSE`。  
  
##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick  
 當使用者按一下滑鼠按鈕時由架構呼叫。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 父視窗的工具列按鈕。  
  
 [輸入] `bDelay`  
 `TRUE` 如果應該處理訊息，且延遲時間。  
  
### <a name="return-value"></a>傳回值  
 如果按鈕處理按一下的訊息; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作， [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)，藉由更新下拉式工具列的狀態。  
  
 當使用者按一下工具列按鈕時，這個方法會建立一個計時器會等候指定的時間長度， [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)資料成員，然後再使用開啟下拉式工具列[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)方法。 這個方法會關閉下拉式工具列第二次使用者按一下工具列按鈕。  
  
##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp  
 當使用者放開滑鼠按鈕時由架構呼叫。  
  
```  
virtual BOOL OnClickUp();
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕處理按一下的訊息; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作， [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)，藉由更新下拉式工具列的狀態。  
  
 這個方法會停止下拉式工具列計時器是否在作用中。 如果它已開啟，它就會關閉下拉式工具列。  
  
 下拉式工具列和下拉式工具列計時器相關的詳細資訊，請參閱[CMFCDropDownToolbarButton::OnClick](#onclick)。  
  
##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp  
 為父工具列處理時，由架構呼叫`WM_HELPHITTEST`訊息。  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWnd`  
 父視窗的工具列按鈕。  
  
### <a name="return-value"></a>傳回值  
 如果按鈕處理說明訊息，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) 藉由呼叫[CMFCDropDownToolbarButton::OnClick](#onclick)方法`bDelay`設`FALSE`. 這個方法會傳回所傳回的值[CMFCDropDownToolbarButton::OnClick](#onclick)。  
  
 如需有關`WM_HELPHITTEST message, see` [TN028： 即時線上說明支援](../../mfc/tn028-context-sensitive-help-support.md)。  
  
##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu  
 當應用程式為父工具列上顯示捷徑功能表，請修改提供的功能表。  
  
```  
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pMenu`  
 若要自訂功能表。  
  
### <a name="return-value"></a>傳回值  
 此方法會傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) 停用下列的功能表項目：  
  
- **複製按鈕影像**  
  
- **按鈕的外觀**  
  
- **影像**  
  
- **Text**  
  
- **影像和文字**  
  
 覆寫這個方法來修改架構的自訂模式中顯示的捷徑功能表。  
  
##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw  
 由架構呼叫以繪製按鈕，使用指定的樣式和選項。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容顯示的按鈕。  
  
 [輸入] `rect`  
 按鈕的週框。  
  
 [輸入] `pImages`  
 與按鈕相關聯的工具列影像集合。  
  
 [輸入] `bHorz`  
 為父工具列停駐狀態。 這個參數是`TRUE`當按鈕會停駐水平及`FALSE`當按鈕會停駐垂直。  
  
 [輸入] `bCustomizeMode`  
 指定工具列是否為自訂模式。 這個參數是`TRUE`工具列時自訂模式和`FALSE`當工具列不是以自訂模式。  
  
 [輸入] `bHighlight`  
 指定按鈕會反白顯示。 這個參數是`TRUE`按鈕反白顯示和`FALSE`時的按鈕不強調顯示。  
  
 [輸入] `bDrawBorder`  
 指定按鈕是否應顯示框線。 這個參數是`TRUE`按鈕時應該顯示框線和`FALSE`當按鈕不應該顯示框線。  
  
 [輸入] `bGrayDisabledButtons`  
 指定是否要加上陰影停用的按鈕，或使用已停用的影像集合。 這個參數是`TRUE`已停用的按鈕時應該會有陰影和`FALSE`當這個方法應該使用已停用的影像集合。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法可自訂工具列按鈕繪圖。  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList  
 由架構呼叫以繪製按鈕**命令**窗格**自訂** 對話方塊。  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容顯示的按鈕。  
  
 [輸入] `rect`  
 按鈕的週框。  
  
 [輸入] `bSelected`  
 是否已選取 [] 按鈕。 如果這個參數是`TRUE`，選取 [] 按鈕。 如果這個參數是`FALSE`，請勿選取按鈕。  
  
### <a name="return-value"></a>傳回值  
 寬度 （像素為單位指定的裝置內容上的按鈕）。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫的自訂對話方塊 (**命令** 索引標籤)  按鈕時才能顯示在主控描繪清單方塊。  
  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) 藉由為按鈕的名稱變更 按鈕的文字標籤 (也就是值`lpszName`您傳遞的參數建構函式）。  
  
##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize  
 從封存讀取此物件，或將它寫入至封存。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `ar`  
 `CArchive`從中或要序列化的物件。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) 序列化為父工具列資源識別碼。 當載入封存 ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)傳回非零值)，這個方法會設定`m_pToolBar`至工具列，包含序列化的資源識別碼的資料成員  
  
##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand  
 設定當使用者按一下按鈕時，架構會使用的預設命令。  
  
```  
void SetDefaultCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmd`  
 預設命令的識別碼。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，指定當使用者按一下按鈕時，會執行架構的預設命令。 具有所指定的命令識別碼的項目`uiCmd`必須位於父下拉式工具列。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



