---
title: "CMFCToolBarMenuButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CompareWith
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CopyFrom
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateFromMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::EnableQuickCustomize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetCommands
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetImageRect
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPaletteRows
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HasButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HaveHotBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsClickedOnMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsDroppedDown
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsEmptyMenuAllowed
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsExclusive
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsQuickMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsTearOffMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnAfterCreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnBeforeDrag
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCalculateSize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCancelMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnChangeParentWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClick
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClickMenuItem
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnContextHelp
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDraw
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDrawOnCustomizeList
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OpenPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::ResetImageToDefault
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SaveBarState
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::Serialize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetACCData
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuOnly
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMessageWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetRadio
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetTearOff
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::DrawDocumentIcon
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarMenuButton class
ms.assetid: cfa50176-7e4b-4527-9904-86a1b48fc1bc
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a06fd323862c6869463b4db0977816b5707c3e18
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarmenubutton-class"></a>CMFCToolBarMenuButton 類別
包含快顯功能表的工具列按鈕。  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarMenuButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CMFCToolBarMenuButton](#cmfctoolbarmenubutton)|建構 `CMFCToolBarMenuButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CompareWith](#comparewith)|比較這個執行個體，以提供`CMFCToolBarButton`物件。 (覆寫[CMFCToolBarButton::CompareWith](../../mfc/reference/cmfctoolbarbutton-class.md#comparewith)。)|  
|[CMFCToolBarMenuButton::CopyFrom](#copyfrom)|將另一個工具列按鈕的內容複製到目前的按鈕。 (覆寫[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|  
|[CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu)|初始化 [工具列] 功能表，從 Windows 功能表處理常式。|  
|[CMFCToolBarMenuButton::CreateMenu](#createmenu)|建立 [工具列] 功能表中的命令所組成的 Windows 功能表。 傳回的控制代碼的 Windows 功能表。|  
|[CMFCToolBarMenuButton::CreatePopupMenu](#createpopupmenu)|建立快顯功能表物件 ( [CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)) 以顯示 [工具列] 功能表。|  
|[CMFCToolBarMenuButton::EnableQuickCustomize](#enablequickcustomize)||  
|[CMFCToolBarMenuButton::GetCommands](#getcommands)|提供唯讀存取權 [工具列] 功能表中的命令清單。|  
|[CMFCToolBarMenuButton::GetImageRect](#getimagerect)|擷取週框的按鈕影像。|  
|[CMFCToolBarMenuButton::GetPaletteRows](#getpaletterows)|調色盤模式功能表時，傳回快顯功能表中的資料列數目。|  
|[CMFCToolBarMenuButton::GetPopupMenu](#getpopupmenu)|傳回與按鈕關聯的快顯功能表物件的指標。|  
|[CMFCToolBarMenuButton::HasButton](#hasbutton)||  
|[CMFCToolBarMenuButton::HaveHotBorder](#havehotborder)|決定當使用者選擇按鈕時，是否要顯示按鈕的框線。 (覆寫[CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|  
|[CMFCToolBarMenuButton::IsBorder](#isborder)||  
|[CMFCToolBarMenuButton::IsClickedOnMenu](#isclickedonmenu)||  
|[CMFCToolBarMenuButton::IsDroppedDown](#isdroppeddown)|決定是否要顯示的快顯功能表。|  
|[CMFCToolBarMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|若要判斷使用者是否可以從選取的功能表項目開啟子功能表架構呼叫。|  
|[CMFCToolBarMenuButton::IsExclusive](#isexclusive)|決定是否按鈕在獨佔模式中，也就是快顯功能表是否仍開啟即使使用者將指標移至另一個工具列或按鈕上方。|  
|[CMFCToolBarMenuButton::IsMenuPaletteMode](#ismenupalettemode)|判斷是否調色盤模式中的快顯功能表。|  
|[CMFCToolBarMenuButton::IsQuickMode](#isquickmode)||  
|[CMFCToolBarMenuButton::IsTearOffMenu](#istearoffmenu)|決定快顯功能表是否有撕列。|  
|[CMFCToolBarMenuButton::OnAfterCreatePopupMenu](#onaftercreatepopupmenu)||  
|[CMFCToolBarMenuButton::OnBeforeDrag](#onbeforedrag)|指定是否可以拖曳 [] 按鈕。 (覆寫[CMFCToolBarButton::OnBeforeDrag](../../mfc/reference/cmfctoolbarbutton-class.md#onbeforedrag)。)|  
|[CMFCToolBarMenuButton::OnCalculateSize](#oncalculatesize)|計算指定之的裝置內容和停駐狀態的按鈕大小的架構所呼叫。 (覆寫[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|  
|[CMFCToolBarMenuButton::OnCancelMode](#oncancelmode)|處理架構呼叫[WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615)訊息。 (覆寫[CMFCToolBarButton::OnCancelMode](../../mfc/reference/cmfctoolbarbutton-class.md#oncancelmode)。)|  
|[CMFCToolBarMenuButton::OnChangeParentWnd](#onchangeparentwnd)|插入新的工具列按鈕時，由架構呼叫。 (覆寫[CMFCToolBarButton::OnChangeParentWnd](cmfctoolbarbutton-class.md#onchangeparentwnd)。)|  
|[CMFCToolBarMenuButton::OnClick](#onclick)|使用者按下滑鼠按鈕時，由架構呼叫。 (覆寫[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|  
|[CMFCToolBarMenuButton::OnClickMenuItem](#onclickmenuitem)|當使用者選取快顯功能表中的項目，由架構呼叫。|  
|[CMFCToolBarMenuButton::OnContextHelp](#oncontexthelp)|為父工具列處理時，由框架呼叫`WM_HELPHITTEST`訊息。 (覆寫[CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)。)|  
|[CMFCToolBarMenuButton::OnDraw](#ondraw)|使用指定的樣式和選項繪製按鈕架構呼叫。 (覆寫[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|  
|[CMFCToolBarMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|繪製按鈕架構呼叫**命令**窗格**自訂**對話方塊。 (覆寫[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|  
|[CMFCToolBarMenuButton::OpenPopupMenu](#openpopupmenu)|當使用者開啟快顯功能表上，由架構呼叫。|  
|[CMFCToolBarMenuButton::ResetImageToDefault](#resetimagetodefault)|設定為預設值是與按鈕關聯的映像。 (覆寫[CMFCToolBarButton::ResetImageToDefault](../../mfc/reference/cmfctoolbarbutton-class.md#resetimagetodefault)。)|  
|[CMFCToolBarMenuButton::SaveBarState](#savebarstate)|儲存的工具列按鈕的狀態。 (覆寫[CMFCToolBarButton::SaveBarState](../../mfc/reference/cmfctoolbarbutton-class.md#savebarstate)。)|  
|[CMFCToolBarMenuButton::Serialize](#serialize)|從封存讀取此物件，或將它寫入至封存檔。 (覆寫[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|  
|[CMFCToolBarMenuButton::SetACCData](#setaccdata)|填入提供`CAccessibilityData`物件存取範圍資料，從工具列按鈕。 (覆寫[CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)。)|  
|[CMFCToolBarMenuButton::SetMenuOnly](#setmenuonly)|指定按鈕是否可以加入至工具列。|  
|[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)|指定調色盤模式是否為快顯功能表。|  
|[CMFCToolBarMenuButton::SetMessageWnd](#setmessagewnd)||  
|[CMFCToolBarMenuButton::SetRadio](#setradio)|強制工具列 功能表上的按鈕，顯示圖示，表示已選取。|  
|[CMFCToolBarMenuButton::SetTearOff](#settearoff)|撕下指定列的快顯功能表的識別碼。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::DrawDocumentIcon](#drawdocumenticon)|功能表按鈕上繪製一個圖示。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw](#m_balwayscallownerdraw)|如果`TRUE`，架構會一律呼叫[CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage)繪製按鈕時。|  
  
## <a name="remarks"></a>備註  
 A`CMFCToolBarMenuButton`可以顯示為功能表、 功能表項目具有子功能表、 按鈕，或者執行的命令會顯示功能表或顯示 功能表上的按鈕。 指定參數，例如影像、 文字、 功能表控制代碼，來判斷功能表按鈕的外觀與行為，以及命令建構函式中的按鈕相關聯的 ID `CMFCToolbarMenuButton::CMFCToolbarMenuButton`。  
  
 自訂類別衍生自`CMFCToolbarMenuButton`類別必須使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集。 [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)巨集會產生錯誤，應用程式關閉時。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定`CMFCToolBarMenuButton`物件。 程式碼說明如何指定下拉式選單中調色盤模式中，並指定撕列在使用者拖曳功能表列上的 [功能表] 按鈕時所建立的識別碼。 此程式碼片段是一部分[字板範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&10;](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtoolbarmenubutton.h  
  
##  <a name="cmfctoolbarmenubutton"></a>CMFCToolBarMenuButton::CMFCToolBarMenuButton  
 建構 `CMFCToolBarMenuButton` 物件。  
  
```  
CMFCToolBarMenuButton();
CMFCToolBarMenuButton(const CMFCToolBarMenuButton& src);

CMFCToolBarMenuButton(
    UINT uiID,  
    HMENU hMenu,  
    int iImage,  
    LPCTSTR lpszText=NULL,  
    BOOL bUserButton=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
 將現有`CMFCToolBarMenuButton`物件複製到這`CMFCToolBarMenuButton`物件。  
  
 [in] `uiID`  
 當使用者按一下按鈕，若要執行的命令識別碼或 ( `UINT`) 不會直接執行命令的功能表按鈕-1。  
  
 [in] `hMenu`  
 功能表; 的控點或`NULL`按鈕不具有功能表時。  
  
 [in] `iImage`  
 按鈕; 映像的索引則為-1，如果此按鈕沒有圖示，或針對所指定的命令會使用圖示`uiID`。 索引是相同的每個`CMFCToolBarImages`應用程式中的物件。  
  
 [in] `lpszText`  
 工具列功能表按鈕的文字。  
  
 [in] `bUserButton`  
 `TRUE`如果按鈕會顯示使用者定義的映像。`FALSE`如果按鈕會顯示與所指定的命令相關聯的預先定義的映像`uiID`。  
  
### <a name="remarks"></a>備註  
 如果`uiID`是有效的命令識別碼，當使用者按一下按鈕會執行該命令。 如果`hMenu`是無效的控制代碼，當它出現在功能表中子功能表或工具列出現時，按鈕會提供下拉式選單。 如果兩個`uiID`和`hMenu`是否有效，是在使用者按一下時，就會執行命令的一部分與部分與向下箭號將下拉式清單功能表，當使用者按一下分割按鈕。 不過，如果`hMenu`是有效的使用者不能按一下 插入 功能表按鈕時執行的指令 按鈕。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCToolBarMenuButton`類別。 此程式碼片段是一部分[字板範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&9;](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_2.cpp)]  
  
##  <a name="comparewith"></a>CMFCToolBarMenuButton::CompareWith  

  
```  
virtual BOOL CompareWith(const CMFCToolBarButton& other) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `other`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="copyfrom"></a>CMFCToolBarMenuButton::CopyFrom  

  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
  
### <a name="remarks"></a>備註  
  
##  <a name="createfrommenu"></a>CMFCToolBarMenuButton::CreateFromMenu  
 初始化 [工具列] 功能表，從 Windows 功能表處理常式。  
  
```  
virtual void CreateFromMenu(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenu`  
 功能表的控點。  
  
### <a name="remarks"></a>備註  
 工具列功能表按鈕可以顯示下拉式子功能表。  
  
 架構會呼叫這個方法來初始化子功能表，從功能表中的命令。  
  
##  <a name="createmenu"></a>CMFCToolBarMenuButton::CreateMenu  
 建立包含 [工具列] 功能表中的命令功能表。 傳回功能表的控制代碼。  
  
```  
virtual HMENU CreateMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果處理功能表的成功。 `NULL`如果工具列功能表按鈕相關聯的命令的清單是空的。  
  
### <a name="remarks"></a>備註  
 您可以覆寫這個方法在衍生的類別，即可自訂功能表的產生的方式。  
  
##  <a name="createpopupmenu"></a>CMFCToolBarMenuButton::CreatePopupMenu  
 建立`CMFCPopupMenu`物件，以顯示 [工具列] 功能表。  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCPopupMenu`顯示下拉式清單功能表與工具列功能表按鈕相關聯的物件。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是由架構準備與按鈕關聯的下拉式選單的顯示。  
  
 預設實作只會建構並傳回新`CMFCPopupMenu`物件。 覆寫這個方法，如果您想要使用的衍生的類型[CMFCPopupMenu 類別](cmfcpopupmenu-class.md)或執行其他的初始化。  
  
##  <a name="drawdocumenticon"></a>CMFCToolBarMenuButton::DrawDocumentIcon  
 功能表按鈕上繪製文件圖示。  
  
```  
void DrawDocumentIcon(
    CDC* pDC,  
    const CRect& rectImage,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectImage`  
 影像的週框的座標。  
  
 [in] `hIcon`  
 圖示的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法會採用文件圖示，並將它繪製功能表 按鈕，在所指定之區域的中央`rectImage`。  
  
##  <a name="enablequickcustomize"></a>CMFCToolBarMenuButton::EnableQuickCustomize  

  
```  
void EnableQuickCustomize();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="hasbutton"></a>CMFCToolBarMenuButton::HasButton  

  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="havehotborder"></a>CMFCToolBarMenuButton::HaveHotBorder  

  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isborder"></a>CMFCToolBarMenuButton::IsBorder  

  
```  
virtual BOOL IsBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isclickedonmenu"></a>CMFCToolBarMenuButton::IsClickedOnMenu  

  
```  
BOOL IsClickedOnMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isquickmode"></a>CMFCToolBarMenuButton::IsQuickMode  

  
```  
BOOL IsQuickMode();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcommands"></a>CMFCToolBarMenuButton::GetCommands  
 提供唯讀存取權 [工具列] 功能表中的命令清單。  
  
```  
const CObList& GetCommands() const;  
```  
  
### <a name="return-value"></a>傳回值  
 常數參考的[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中包含一系列[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件。  
  
### <a name="remarks"></a>備註  
 工具列功能表按鈕可以顯示子功能表。 您可以提供的建構函式中或在子功能表中的命令清單[CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu)為功能表的控制代碼 ( `HMENU`)。 功能表會轉換成一份物件衍生自[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)並儲存在內部`CObList`物件。 您可以藉由呼叫這個方法來存取這份清單。  
  
##  <a name="getimagerect"></a>CMFCToolBarMenuButton::GetImageRect  
 擷取週框的按鈕影像。  
  
```  
void GetImageRect(CRect& rectImage);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectImage`  
 參考`CRect`接收影像的週框的座標的物件。  
  
##  <a name="getpaletterows"></a>CMFCToolBarMenuButton::GetPaletteRows  
 調色盤模式功能表時，請在下拉式選單中傳回資料列數目。  
  
```  
int GetPaletteRows() const;  
```  
  
### <a name="return-value"></a>傳回值  
 調色盤中的資料列數目。  
  
### <a name="remarks"></a>備註  
 當功能表按鈕設定為調色盤模式時，功能表項目會出現在多個資料行具有有限數目的資料列。 呼叫此方法來取得資料列數目。 您可以啟用或停用調色盤模式，並指定使用的資料列數目[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)。  
  
##  <a name="getpopupmenu"></a>CMFCToolBarMenuButton::GetPopupMenu  
 傳回的指標[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)物件，表示下拉式選單中的按鈕。  
  
```  
CMFCPopupMenu* GetPopupMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)架構所繪製的工具列功能表按鈕，子功能表時所建立的物件`NULL`如果沒有子功能表會顯示。  
  
### <a name="remarks"></a>備註  
 當 [工具列] 功能表按鈕顯示下拉式選單時，按鈕會建立[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)物件以代表功能表。 呼叫這個方法來取得的指標`CMFCPopupMenu`物件。 您不應儲存傳回的指標，因為它是暫時的當使用者關閉下拉式選單會變成無效。  
  
##  <a name="isdroppeddown"></a>CMFCToolBarMenuButton::IsDroppedDown  
 指出目前是否顯示快顯功能表。  
  
```  
virtual BOOL IsDroppedDown() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列功能表按鈕顯示其子功能表。否則`FALSE`。  
  
##  <a name="isemptymenuallowed"></a>CMFCToolBarMenuButton::IsEmptyMenuAllowed  
 指定功能表項目是否顯示空的子功能表。  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果架構時，會開啟子功能表從目前選取的功能表項目即使子功能表是空的。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 當使用者嘗試開啟子功能表，從目前選取的功能表項目時，架構會呼叫這個方法。 如果是空的子功能表和`IsEmptyMenuAllowed`傳回`FALSE`，將不會開啟子功能表。  
  
 預設實作會傳回 `FALSE`。 覆寫這個方法，以自訂此行為。  
  
##  <a name="isexclusive"></a>CMFCToolBarMenuButton::IsExclusive  
 指出是否以獨佔模式 按鈕。  
  
```  
virtual BOOL IsExclusive() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕是以獨佔模式。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 當使用者開啟快顯功能表按鈕，然後將滑鼠指標移至另一個工具列或功能表按鈕上方時，除非按鈕是獨佔模式，也會關閉快顯功能表。  
  
 預設實作一定會傳回`FALSE`。 如果您想要獨佔模式開啟，請覆寫這個方法在衍生類別中。  
  
##  <a name="ismenupalettemode"></a>CMFCToolBarMenuButton::IsMenuPaletteMode  
 判斷是否在調色盤模式下拉式選單。  
  
```  
BOOL IsMenuPaletteMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果啟用的調色盤模式，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 當功能表按鈕設定為調色盤模式時，功能表項目出現在多個資料行具有有限數目的資料列。 呼叫此方法來取得資料列數目。 您可以啟用或停用調色盤模式藉由呼叫[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)。  
  
##  <a name="istearoffmenu"></a>CMFCToolBarMenuButton::IsTearOffMenu  
 表示下拉式選單中是否有撕列。  
  
```  
virtual BOOL IsTearOffMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列功能表按鈕具有撕列。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 啟用撕功能和設定撕列識別碼，呼叫[CMFCToolBarMenuButton::SetTearOff](#settearoff)。  
  
##  <a name="m_balwayscallownerdraw"></a>CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw  
 指定是否在 framework 一律會呼叫[CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage)繪製按鈕時。  
  
```  
static BOOL m_bAlwaysCallOwnerDraw;  
```  
  
### <a name="remarks"></a>備註  
 當這個成員變數設定為`TRUE`，按鈕會一律呼叫[CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage)方法，以在按鈕上顯示影像。 當`m_bAlwaysCallOwnerDraw`是`FALSE`，按鈕本身繪製影像，如果預先定義的映像。 否則，它會呼叫`OnDrawMenuImage`。  
  
##  <a name="onaftercreatepopupmenu"></a>CMFCToolBarMenuButton::OnAfterCreatePopupMenu  

  
```  
virtual void OnAfterCreatePopupMenu();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onbeforedrag"></a>CMFCToolBarMenuButton::OnBeforeDrag  

  
```  
virtual BOOL OnBeforeDrag() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="oncalculatesize"></a>CMFCToolBarMenuButton::OnCalculateSize  

  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 [in] `sizeDefault`  
 [in] `bHorz`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="oncancelmode"></a>CMFCToolBarMenuButton::OnCancelMode  

  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarMenuButton::OnChangeParentWnd  

  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onclick"></a>CMFCToolBarMenuButton::OnClick  

  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 [in] `bDelay`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onclickmenuitem"></a>CMFCToolBarMenuButton::OnClickMenuItem  
 當使用者選取下拉式選單中的項目時，由架構呼叫。  
  
```  
virtual BOOL OnClickMenuItem();
```  
  
### <a name="return-value"></a>傳回值  
 `FALSE`如果架構應該繼續預設功能表項目處理。否則`TRUE`。 預設實作一定會傳回`FALSE`。  
  
### <a name="remarks"></a>備註  
 當使用者按一下功能表項目時，架構就會執行與該項目相關聯的命令。  
  
 若要自訂功能表項目處理，覆寫`OnClickMenuItem`從衍生類別中`CMFCToolBarMenuButton`類別。 您也必須覆寫[CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)並將需要在衍生類別的執行個體的特殊處理的功能表按鈕。  
  
##  <a name="oncontexthelp"></a>CMFCToolBarMenuButton::OnContextHelp  

  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondraw"></a>CMFCToolBarMenuButton::OnDraw  

  
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
 [in] `pDC`  
 [in] `rect`  
 [in] `pImages`  
 [in] `bHorz`  
 [in] `bCustomizeMode`  
 [in] `bHighlight`  
 [in] `bDrawBorder`  
 [in] `bGrayDisabledButtons`  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarMenuButton::OnDrawOnCustomizeList  

  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 [in] `rect`  
 [in] `bSelected`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="openpopupmenu"></a>CMFCToolBarMenuButton::OpenPopupMenu  
 在使用者開啟下拉式選單中的工具列功能表按鈕時，由架構呼叫。  
  
```  
virtual BOOL OpenPopupMenu(CWnd* pWnd=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 指定接收下拉式選單命令視窗。 它可以是`NULL`工具列功能表按鈕有父視窗。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`當[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)建立物件，並開啟成功，否則為`FALSE`。  
  
### <a name="remarks"></a>備註  
 當使用者從工具列功能表按鈕開啟下拉式選單，則架構會呼叫此函數。  
  
##  <a name="resetimagetodefault"></a>CMFCToolBarMenuButton::ResetImageToDefault  

  
```  
virtual void ResetImageToDefault();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="savebarstate"></a>CMFCToolBarMenuButton::SaveBarState  

  
```  
virtual void SaveBarState();
```  
  
### <a name="remarks"></a>備註  
 建立工具列按鈕拖放作業的結果時，架構會呼叫這個方法。 這個方法會呼叫[CMFCPopupMenu::SaveState](../../mfc/reference/cmfcpopupmenu-class.md#savestate)方法的最上層的快顯功能表，這會導致重新建立其功能表快顯功能表的 [父] 按鈕。  
  
##  <a name="serialize"></a>CMFCToolBarMenuButton::Serialize  

  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 [in] `ar`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setaccdata"></a>CMFCToolBarMenuButton::SetACCData  
 設定功能區項目的協助工具資料。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 `pParent`  
 功能區項目的父視窗。  
  
 `data`  
 功能區項目的協助工具資料。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 依預設，此方法會設定功能區項目的協助工具資料，並一律傳回 `TRUE`。 覆寫此方法以設定協助工具資料並傳回值，以指出成功或失敗。  
  
##  <a name="setmenuonly"></a>CMFCToolBarMenuButton::SetMenuOnly  
 指定當它具有有效的命令 ID 和子功能表時，是否要按鈕繪製為功能表按鈕或分割按鈕。  
  
```  
void SetMenuOnly(BOOL bMenuOnly);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMenuOnly`  
 `TRUE`此按鈕顯示為功能表按鈕，它具有有效的命令 ID 和子功能表，當`FALSE`它具有有效的命令 ID 和子功能表時，顯示此按鈕為分割按鈕。  
  
### <a name="remarks"></a>備註  
 一般而言，當時工具列功能表按鈕具有子功能表和命令 ID，功能表會顯示分割按鈕向下箭號按鈕具有主要按鈕和附加。 如果您呼叫這個方法和`bMenuOnly`是`TRUE`，按鈕而似乎是單一的功能表中按鈕的向下箭號按鈕。 當使用者按一下任一種模式下的箭號時，就會開啟子功能表，並在使用者按一下非箭號按鈕組件架構哪一種模式中的執行的命令。  
  
##  <a name="setmenupalettemode"></a>CMFCToolBarMenuButton::SetMenuPaletteMode  
 指定是否在調色盤模式下拉式選單。  
  
```  
void SetMenuPaletteMode(
    BOOL bMenuPaletteMode=TRUE,  
    int nPaletteRows=1);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMenuPaletteMode`  
 指定是否在調色盤模式下拉式選單。  
  
 [in] `nPaletteRows`  
 調色盤中的資料列數目。  
  
### <a name="remarks"></a>備註  
 在調色盤模式中，所有功能表項目會都顯示為多個資料行的調色盤。 使用指定的資料列數目`nPaletteRows`。  
  
##  <a name="setmessagewnd"></a>CMFCToolBarMenuButton::SetMessageWnd  

  
```  
void SetMessageWnd(CWnd* pWndMessage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndMessage`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setradio"></a>CMFCToolBarMenuButton::SetRadio  
 設定顯示選項按鈕樣式圖示的核取時將工具列功能表按鈕。  
  
```  
virtual void SetRadio();
```  
  
### <a name="remarks"></a>備註  
 取出時繪製功能表按鈕時，它會呼叫[CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)繪製核取記號圖示。 根據預設，`OnDrawMenuCheck`要求目前的視覺管理員繪製核取方塊樣式的功能表按鈕上的核取記號。 呼叫這個方法之後，目前的視覺管理員改為功能表按鈕上繪製一個選項按鈕樣式核取記號。 這項變更無法復原。  
  
 當您呼叫這個方法目前顯示的功能表按鈕，則會重新整理。  
  
##  <a name="settearoff"></a>CMFCToolBarMenuButton::SetTearOff  
 指定下拉式選單撕列的識別碼。  
  
```  
virtual void SetTearOff(UINT uiBarID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiBarID`  
 指定新撕列識別碼。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以指定撕列在使用者拖曳功能表列上的 [功能表] 按鈕時所建立的識別碼。 如果`uiBarID`參數是 0，則使用者無法分離出來的功能表按鈕。  
  
 呼叫[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)啟用應用程式中的 tear-off 功能表功能。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)
