---
title: "CMDIChildWnd 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
dev_langs:
- C++
helpviewer_keywords:
- MDI [C++], child windows
- windows [C++], MDI
- CMDIChildWnd class
- child windows, CMDIChildWnd class
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 240af1fe5f3afa4cdb7d4d585dc74cc4836799cc
ms.lasthandoff: 02/24/2017

---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd 類別
提供 Windows 多重文件介面 (MDI) 子視窗的功能，以及管理視窗的成員。  
  
## <a name="syntax"></a>語法  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|建構 `CMDIChildWnd` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMDIChildWnd::Create](#create)|建立相關聯的 Windows MDI 子視窗`CMDIChildWnd`物件。|  
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|傳回父 MDI 用戶端視窗的 MDI 框架。|  
|[CMDIChildWnd::MDIActivate](#mdiactivate)|啟動這個 MDI 子視窗。|  
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|終結這個 MDI 子視窗。|  
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|最大化這個 MDI 子視窗。|  
|[CMDIChildWnd::MDIRestore](#mdirestore)|最大化或最小化的大小，從還原此 MDI 子視窗。|  
|[CMDIChildWnd::SetHandles](#sethandles)|設定功能表和快速鍵資源控制代碼。|  
  
## <a name="remarks"></a>備註  
 MDI 子視窗看起來很像一般的框架視窗中，不同之處在於 MDI 子視窗會出現在 MDI 框架視窗內，而不是在桌面上。 MDI 子視窗並沒有自己的功能表列，但改為共用 MDI 框架視窗的功能表。 架構會自動變更 MDI 框架功能表來代表目前現用 MDI 子視窗。  
  
 若要建立有用的 MDI 子視窗應用程式，衍生自`CMDIChildWnd`。 加入成員變數來儲存您的應用程式特定資料衍生的類別。 實作訊息處理常式成員函式，和衍生類別中對應的訊息，以指定訊息被導向至視窗時會發生什麼事。  
  
 有三種方式來建構 MDI 子視窗︰  
  
-   直接建構使用**建立**。  
  
-   直接建構使用`LoadFrame`。  
  
-   間接建構透過文件範本。  
  
 然後再呼叫**建立**或`LoadFrame`，您必須建構使用 c + + 堆積上的框架視窗物件**新**運算子。 然後再呼叫**建立**您也可以註冊視窗類別[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函式，若要設定框架的圖示和類別樣式。  
  
 使用**建立**傳遞框架的建立參數為立即引數的成員函式。  
  
 `LoadFrame`需要較少的引數比**建立**，並改為擷取資源，包括框架的標題、 圖示、 快速鍵對應表，以及功能表中的大部分的預設值。 若要能夠存取`LoadFrame`，所有這些資源都必須有相同的資源識別碼 (例如， **IDR_MAINFRAME**)。  
  
 當`CMDIChildWnd`物件包含檢視表和文件，它們由間接的架構，而不是直接由程式設計人員。 `CDocTemplate`框架的建立，包含檢視中，建立並連接至適當的文件檢視的物件會協調流程。 參數的`CDocTemplate`建構函式指定`CRuntimeClass`三個類別的相關 （文件、 框架和檢視）。 A`CRuntimeClass`架構使用物件來動態建立新的框架時使用者所指定 （例如，藉由使用新檔案 命令或 MDI 視窗新命令）。  
  
 框架視窗類別衍生自`CMDIChildWnd`必須以宣告`DECLARE_DYNCREATE`為了讓上述`RUNTIME_CLASS`機制正確運作。  
  
 `CMDIChildWnd`類別會繼承它的預設實作的許多`CFrameWnd`。 如需這些功能的詳細清單，請參閱[CFrameWnd](../../mfc/reference/cframewnd-class.md)類別描述。 `CMDIChildWnd`類別具有下列額外的功能︰  
  
-   搭配`CMultiDocTemplate`類別，多個`CMDIChildWnd`從相同的文件範本的物件共用相同的功能表上，儲存 Windows 系統資源。  
  
-   完全取代目前使用中的 MDI 子視窗功能表的 MDI 框架視窗的功能表上，而且目前現用 MDI 子視窗的標題會加入至 MDI 框架視窗的標題。 如需進一步的 MDI 子視窗函式實作搭配 MDI 框架視窗的範例，請參閱`CMDIFrameWnd`類別描述。  
  
 不使用 c + +**刪除**終結框架視窗的運算子。 請改用 `CWnd::DestroyWindow` 。 `CFrameWnd`實作`PostNcDestroy`終結視窗時，將會刪除 c + + 物件。 當使用者關閉框架視窗時，預設`OnClose`處理常式會呼叫`DestroyWindow`。  
  
 如需有關`CMDIChildWnd`，請參閱[框架視窗](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIChildWnd`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd  
 呼叫建構`CMDIChildWnd`物件。  
  
```  
CMDIChildWnd();
```  
  
### <a name="remarks"></a>備註  
 呼叫**建立**建立可見的視窗。  
  
### <a name="example"></a>範例  
  請參閱範例[CMDIChildWnd::Create](#create)。  
  
##  <a name="create"></a>CMDIChildWnd::Create  
 呼叫此成員函式，來建立 Windows MDI 子視窗，並將其附加至`CMDIChildWnd`物件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CMDIFrameWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 指向以 null 結束的字元字串，名稱的 Windows 類別 ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)結構)。 類別名稱可以是任何名稱向[AfxRegisterWndClass](http://msdn.microsoft.com/library/62c7d4b1-7a29-4abb-86f7-dec541659db0)全域函式。 應該是**NULL**標準`CMDIChildWnd`。  
  
 `lpszWindowName`  
 指向以 null 結束的字元字串，表示視窗名稱。 做為標題列的文字。  
  
 `dwStyle`  
 指定的視窗[樣式](../../mfc/reference/window-styles.md)屬性。 **WS_CHILD**樣式是必要。  
  
 `rect`  
 包含大小和視窗的位置。 `rectDefault`值允許指定的大小和位置的新 Windows `CMDIChildWnd`。  
  
 `pParentWnd`  
 指定視窗的父代。 如果**NULL**，使用主應用程式視窗。  
  
 `pContext`  
 指定[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)結構。 這個參數可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 目前使用中的 MDI 子框架視窗可以判斷父框架視窗的標題。 這項功能已被關閉**FWS_ADDTOTITLE**子框架視窗樣式位元。  
  
 架構會呼叫此成員函式以回應使用者命令來建立子視窗，架構會使用`pContext`參數，以正確地連接到應用程式的子視窗。 當您呼叫**建立**，`pContext`可以是**NULL**。  
  
### <a name="example"></a>範例  
 範例 1:  
  
 [!code-cpp[NVC_MFCWindowing #&7;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]  
  
### <a name="example"></a>範例  
 範例 2:  
  
 [!code-cpp[NVC_MFCWindowing #&8;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing #&9;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]  
  
##  <a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame  
 呼叫此函式來傳回 MDI 父框架。  
  
```  
CMDIFrameWnd* GetMDIFrame();
```  
  
### <a name="return-value"></a>傳回值  
 MDI 父框架視窗的指標。  
  
### <a name="remarks"></a>備註  
 傳回的框架是兩個父代移除`CMDIChildWnd`視窗類型的父系**MDICLIENT**管理`CMDIChildWnd`物件。 呼叫[GetParent](../../mfc/reference/cwnd-class.md#getparent)成員函式來傳回`CMDIChildWnd`物件的直屬**MDICLIENT**做為暫時的父`CWnd`指標。  
  
### <a name="example"></a>範例  
  請參閱範例[CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)。  
  
##  <a name="mdiactivate"></a>CMDIChildWnd::MDIActivate  
 呼叫此成員函式，以啟動獨立 MDI 框架視窗的 MDI 子視窗。  
  
```  
void MDIActivate();
```  
  
### <a name="remarks"></a>備註  
 當框架變成使用中時，也將會啟動上次啟動的子視窗。  
  
### <a name="example"></a>範例  
  請參閱範例[CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)。  
  
##  <a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy  
 呼叫此成員函式，可摧毀 MDI 子視窗。  
  
```  
void MDIDestroy();
```  
  
### <a name="remarks"></a>備註  
 成員函式移除從框架視窗的子視窗的標題，並停用子視窗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&10;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]  
  
##  <a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize  
 呼叫此成員函式，以最大化 MDI 子視窗。  
  
```  
void MDIMaximize();
```  
  
### <a name="remarks"></a>備註  
 子視窗會最大化時，Windows 會調整大小，使其填滿的框架視窗工作區的工作區。 Windows 會放置框架的功能表列中的子視窗的 [控制] 功能表，讓使用者可以還原或關閉子視窗，並將子視窗的標題加入至框架視窗標題。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&11;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]  
  
##  <a name="mdirestore"></a>CMDIChildWnd::MDIRestore  
 呼叫此成員函式，從最大化或最小化大小還原 MDI 子視窗。  
  
```  
void MDIRestore();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&12;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]  
  
##  <a name="sethandles"></a>CMDIChildWnd::SetHandles  
 設定功能表和快速鍵資源控制代碼。  
  
```  
void SetHandles(
    HMENU hMenu,  
    HACCEL hAccel);
```  
  
### <a name="parameters"></a>參數  
 `hMenu`  
 功能表資源控制代碼。  
  
 `hAccel`  
 快速鍵對應資源控制代碼。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可將設定 MDI 子視窗物件所使用的功能表和快速鍵資源。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 範例 SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd 類別](../../mfc/reference/cmdiframewnd-class.md)

