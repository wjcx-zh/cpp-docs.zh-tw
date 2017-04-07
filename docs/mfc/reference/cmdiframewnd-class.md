---
title: "CMDIFrameWnd 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
dev_langs:
- C++
helpviewer_keywords:
- MDI frame windows
- CMDIFrameWnd class
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
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
ms.openlocfilehash: 0eae6c14038dd27a5779757d1807068fbe865b81
ms.lasthandoff: 02/24/2017

---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd 類別
提供 Windows 多重文件介面 (MDI) 框架視窗的功能，以及管理視窗的成員。  
  
## <a name="syntax"></a>語法  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|建構 `CMDIFrameWnd`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMDIFrameWnd::CreateClient](#createclient)|建立 Windows **MDICLIENT**這個視窗`CMDIFrameWnd`。 由呼叫`OnCreate`成員函式`CWnd`。|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|建立新的子視窗。|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|傳回的視窗快顯功能表。|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|啟動不同的 MDI 子視窗。|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|排列所有的子視窗重疊顯示的格式。|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|會擷取目前現用 MDI 子視窗，以及旗標，指出為最大化子。|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|排列所有的最小化文件子視窗。|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|最大化 MDI 子視窗。|  
|[CMDIFrameWnd::MDINext](#mdinext)|啟動立即背後目前作用中的子視窗的子視窗，並將目前作用中的子視窗背後所有其他子視窗。|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|啟動前一個子視窗，並將其背後的目前作用中的子視窗。|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|最大化或最小化的大小，從還原 MDI 子視窗。|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|取代 MDI 框架視窗的功能表、 視窗快顯功能表上，或兩者。|  
|[CMDIFrameWnd::MDITile](#mditile)|排列所有的子視窗並排顯示的格式。|  
  
## <a name="remarks"></a>備註  
 若要建立您的應用程式有用 MDI 框架視窗，衍生自`CMDIFrameWnd`。 加入成員變數來儲存您的應用程式特定資料衍生的類別。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。  
  
 您可以藉由呼叫建構 MDI 框架視窗[建立](../../mfc/reference/cframewnd-class.md#create)或[LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)成員函式`CFrameWnd`。  
  
 然後再呼叫**建立**或`LoadFrame`，您必須建構使用 c + + 堆積上的框架視窗物件**新**運算子。 然後再呼叫**建立**您也可以註冊視窗類別[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函式，若要設定框架的圖示和類別樣式。  
  
 使用**建立**傳遞框架的建立參數為立即引數的成員函式。  
  
 `LoadFrame`需要較少的引數比**建立**，並改為擷取資源，包括框架的標題、 圖示、 快速鍵對應表，以及功能表中的大部分的預設值。 可供存取`LoadFrame`，所有這些資源都必須有相同的資源識別碼 (例如， **IDR_MAINFRAME**)。  
  
 雖然**MDIFrameWnd**衍生自`CFrameWnd`，框架視窗類別衍生自`CMDIFrameWnd`不需要使用宣告`DECLARE_DYNCREATE`。  
  
 `CMDIFrameWnd`類別會繼承它的預設實作的許多`CFrameWnd`。 這些功能的詳細清單，請參閱[CFrameWnd](../../mfc/reference/cframewnd-class.md)類別描述。 `CMDIFrameWnd`類別具有下列額外的功能︰  
  
-   MDI 框架視窗負責管理**MDICLIENT**  視窗中，與控制列一起重新置放。 MDI 用戶端視窗是 MDI 子框架視窗的直接父系。 **WS_HSCROLL**和**WS_VSCROLL**上指定的視窗樣式`CMDIFrameWnd`套用至 MDI 用戶端視窗而不是在主框架視窗，讓使用者可以向上捲動以 MDI 工作區 （如 Windows 程式經理，例如）。  
  
-   MDI 框架視窗擁有沒有現用 MDI 子視窗時用作功能表列的預設功能表。 使用中的 MDI 子系時，MDI 框架視窗的功能表列會自動取代 MDI 子視窗功能表。  
  
-   如果有一個與目前的 MDI 子視窗一起運作，MDI 框架視窗。 比方說，委派命令訊息至目前使用中的 MDI 子系，MDI 框架視窗之前。  
  
-   MDI 框架視窗會有下列的標準視窗功能表命令的預設處理常式︰  
  
    - **ID_WINDOW_TILE_VERT**  
  
    - **ID_WINDOW_TILE_HORZ**  
  
    - **ID_WINDOW_CASCADE**  
  
    - **ID_WINDOW_ARRANGE**  
  
-   MDI 框架視窗也會有的實作**ID_WINDOW_NEW**，這會建立新的框架和檢視目前的文件上。 應用程式可以覆寫以自訂 MDI 視窗處理這些預設命令實作。  
  
 不使用 c + +**刪除**終結框架視窗的運算子。 請改用 `CWnd::DestroyWindow` 。 `CFrameWnd`實作`PostNcDestroy`終結視窗時，將會刪除 c + + 物件。 當使用者關閉框架視窗時，預設`OnClose`處理常式會呼叫`DestroyWindow`。  
  
 如需有關`CMDIFrameWnd`，請參閱[框架視窗](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIFrameWnd`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cmdiframewnd"></a>CMDIFrameWnd::CMDIFrameWnd  
 建構 `CMDIFrameWnd` 物件。  
  
```  
CMDIFrameWnd();
```  
  
### <a name="remarks"></a>備註  
 呼叫**建立**或`LoadFrame`成員函式來建立顯示 MDI 框架視窗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&13;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]  
  
##  <a name="createclient"></a>CMDIFrameWnd::CreateClient  
 建立管理 MDI 用戶端視窗`CMDIChildWnd`物件。  
  
```  
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>參數  
 `lpCreateStruct`  
 長指標[CREATESTRUCT](../../mfc/reference/createstruct-structure.md)結構。  
  
 `pWindowMenu`  
 視窗的快顯功能表上的指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您覆寫應該呼叫此成員函式`OnCreate`直接成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&14;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]  
  
##  <a name="createnewchild"></a>CMDIFrameWnd::CreateNewChild  
 建立新的子視窗。  
  
```  
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,  
    UINT nResource,  
    HMENU hMenu = NULL,  
    HACCEL hAccel = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pClass`  
 若要建立子視窗的執行階段類別。  
  
 *nResource*  
 子視窗相關聯的共用資源的識別碼。  
  
 `hMenu`  
 子視窗的功能表。  
  
 `hAccel`  
 子視窗的快速鍵。  
  
### <a name="remarks"></a>備註  
 使用此函數來建立子視窗的 MDI 框架視窗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&15;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 這個範例是摘錄自知識庫文件 Q201045，「 如何︰ 將多個視窗類型加入至非文件/檢視 MDI 應用程式。 」 知識庫文件可在 MSDN Library 中的 Visual Studio 文件或[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="getwindowmenupopup"></a>CMDIFrameWnd::GetWindowMenuPopup  
 呼叫此成員函式可取得目前的快顯功能表，名為 「 視窗 」 （快顯功能表的 MDI 視窗管理的功能表項目） 的控制代碼。  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>參數  
 *hMenuBar*  
 目前的功能表列。  
  
### <a name="return-value"></a>傳回值  
 視窗的快顯功能表一樣存在;否則**NULL**。  
  
### <a name="remarks"></a>備註  
 預設實作會快顯功能表包含標準視窗功能表命令，例如尋找**ID_WINDOW_NEW**和**ID_WINDOW_TILE_HORZ**。  
  
 如果您有不會使用標準功能表命令識別碼 [視窗] 功能表，請覆寫此成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&16;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]  
  
##  <a name="mdiactivate"></a>CMDIFrameWnd::MDIActivate  
 啟動不同的 MDI 子視窗。  
  
```  
void MDIActivate(CWnd* pWndActivate);
```  
  
### <a name="parameters"></a>參數  
 *pWndActivate*  
 指向以 MDI 子視窗，才能啟動。  
  
### <a name="remarks"></a>備註  
 此成員函式會將[WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate)訊息給子視窗，使其無法啟動而正在停用子視窗。  
  
 這是如果使用者使用滑鼠或鍵盤將焦點變更為 MDI 子視窗傳送相同訊息。  
  
> [!NOTE]
>  獨立 MDI 框架視窗啟用 MDI 子視窗。 當框架變成使用中時，會傳送上次啟動的子視窗[WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate)訊息来繪製的使用中視窗框架和標題列，但是不會接收另一個`WM_MDIACTIVATE`訊息。  
  
### <a name="example"></a>範例  
 請參閱範例[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)。  
  
##  <a name="mdicascade"></a>CMDIFrameWnd::MDICascade  
 排列所有 MDI 子視窗重疊顯示格式。  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>參數  
 `nType`  
 指定 cascade 旗標。 您可以指定下列旗標︰ `MDITILE_SKIPDISABLED`，它可防止已停用的 MDI 子視窗的重疊顯示。  
  
### <a name="remarks"></a>備註  
 第一版`MDICascade`，沒有參數，以重疊顯示所有 MDI 子視窗，包括停用的。 第二個版本 （選擇性） 不會不停用的重疊顯示 MDI 子視窗，如果您指定`MDITILE_SKIPDISABLED`的`nType`參數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&17;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>CMDIFrameWnd::MDIGetActive  
 擷取目前現用 MDI 子視窗，以及旗標，指出是否要最大化子視窗。  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 *pbMaximized*  
 指標**BOOL**傳回值。 設定為**TRUE**如果視窗最大化，否則傳回**FALSE**。  
  
### <a name="return-value"></a>傳回值  
 作用中的 MDI 子視窗的指標。  
  
### <a name="example"></a>範例  
 請參閱範例[CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。  
  
##  <a name="mdiiconarrange"></a>CMDIFrameWnd::MDIIconArrange  
 排列所有的最小化文件子視窗。  
  
```  
void MDIIconArrange();
```  
  
### <a name="remarks"></a>備註  
 它不會影響不降到最低的子視窗。  
  
### <a name="example"></a>範例  
 請參閱範例[CMDIFrameWnd::MDICascade](#mdicascade)。  
  
##  <a name="mdimaximize"></a>CMDIFrameWnd::MDIMaximize  
 將指定的 MDI 子視窗的最大化。  
  
```  
void MDIMaximize(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 若要最大化視窗的指標。  
  
### <a name="remarks"></a>備註  
 子視窗會最大化時，Windows 會調整大小，使其填滿用戶端視窗的工作區。 Windows 框架的功能表列中放置子視窗的控制功能表，讓使用者可以還原或關閉子視窗。 它也會加入至框架視窗標題的子視窗的標題。  
  
 如果目前現用 MDI 子視窗最大化時，會啟動另一個 MDI 子視窗，Windows 還原目前作用中的子系，並將新啟動的子視窗最大化。  
  
### <a name="example"></a>範例  
 請參閱範例[CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。  
  
##  <a name="mdinext"></a>CMDIFrameWnd::MDINext  
 啟動立即背後目前作用中的子視窗的子視窗，並將目前作用中的子視窗背後所有其他子視窗。  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>備註  
 目前現用 MDI 子視窗最大化時，如果成員函式還原目前作用中的子系，並充分發揮新啟動的子系。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&18;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>CMDIFrameWnd::MDIPrev  
 啟動前一個子視窗，並將其背後的目前作用中的子視窗。  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>備註  
 目前現用 MDI 子視窗最大化時，如果成員函式還原目前作用中的子系，並充分發揮新啟動的子系。  
  
##  <a name="mdirestore"></a>CMDIFrameWnd::MDIRestore  
 最大化或最小化的大小，從還原 MDI 子視窗。  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 若要還原視窗的指標。  
  
### <a name="example"></a>範例  
 請參閱範例[CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore)。  
  
##  <a name="mdisetmenu"></a>CMDIFrameWnd::MDISetMenu  
 取代 MDI 框架視窗的功能表、 視窗快顯功能表上，或兩者。  
  
```  
CMenu* MDISetMenu(
    CMenu* pFrameMenu,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>參數  
 *pFrameMenu*  
 指定新的框架視窗功能表的功能表。 如果**NULL**，則不會變更功能表。  
  
 `pWindowMenu`  
 指定新的視窗快顯功能表的功能表。 如果**NULL**，則不會變更功能表。  
  
### <a name="return-value"></a>傳回值  
 指標取代為此訊息的框架視窗功能表。 該指標可能是暫時性的，因此不應該儲存供日後使用。  
  
### <a name="remarks"></a>備註  
 在呼叫`MDISetMenu`，應用程式必須呼叫[DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)成員函式`CWnd`更新功能表列。  
  
 如果這個呼叫來取代 視窗中的快顯功能表上，MDI 子視窗功能表項目會從先前的視窗功能表中移除，並新增到新的視窗快顯功能表。  
  
 如果 MDI 子視窗最大化，這個呼叫會取代 MDI 框架視窗功能表控制項功能表和還原控制項從上一個框架視窗功能表移除，並加入至新的功能表。  
  
 如果您使用架構來管理您的 MDI 子視窗，請不要呼叫此成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&19;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing #&20;](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]  
  
##  <a name="mditile"></a>CMDIFrameWnd::MDITile  
 排列所有的子視窗並排顯示的格式。  
  
```  
void MDITile();  
void MDITile(int nType);
```  
  
### <a name="parameters"></a>參數  
 `nType`  
 指定的並排顯示旗標。 這個參數可以是下列旗標的任一項︰  
  
- `MDITILE_HORIZONTAL`並排顯示 MDI 子視窗，另一個上方顯示一個視窗。  
  
- `MDITILE_SKIPDISABLED`已停用的 MDI 子視窗可防止在並排顯示。  
  
- `MDITILE_VERTICAL`並排顯示 MDI 子視窗，另一個旁邊顯示一個視窗。  
  
### <a name="remarks"></a>備註  
 第一版`MDITile`，如果沒有參數，並排顯示視窗以垂直方式在 Windows 3.1 和更新版本的版本。 第二個版本並排顯示視窗垂直或水平方向的值而定`nType`參數。  
  
### <a name="example"></a>範例  
 請參閱範例[CMDIFrameWnd::MDICascade](#mdicascade)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 範例 SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)

