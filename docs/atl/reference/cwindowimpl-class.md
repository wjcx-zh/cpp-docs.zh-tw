---
title: 類別 CWindowImpl |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::DefWindowProc
- ATLWIN/ATL::GetCurrentMessage
- ATLWIN/ATL::GetWindowProc
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::SubclassWindow
- ATLWIN/ATL::UnsubclassWindow
- ATLWIN/ATL::GetWndClassInfo
- ATLWIN/ATL::WindowProc
- ATLWIN/ATL::m_pfnSuperWindowProc
dev_langs:
- C++
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4884bbacd03675d00cb1a49b937265ab5faa2835
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366152"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 類別
提供建立或子類別化視窗的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```    
  
#### <a name="parameters"></a>參數  
 `T`  
 您的新類別，衍生自 `CWindowImpl`。  
  
 *TBase*  
 您類別的基底類別。 根據預設，基底類別是[CWindow](../../atl/reference/cwindow-class.md)。  
  
 `TWinTraits`  
 A [traits 類別](../../atl/understanding-window-traits.md)，定義視窗樣式。 預設值為 `CControlWinTraits`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CWindowImpl::Create](#create)|建立視窗。|  
  
### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT 方法  
  
|||  
|-|-|  
|[DefWindowProc](#defwindowproc)|提供預設訊息處理。|  
|[GetCurrentMessage](#getcurrentmessage)|傳回目前訊息。|  
|[GetWindowProc](#getwindowproc)|傳回目前的視窗程序。|  
|[OnFinalMessage](#onfinalmessage)|在收到最後一則訊息之後呼叫 (通常是 `WM_NCDESTROY`)。|  
|[SubclassWindow](#subclasswindow)|子類別化視窗。|  
|[UnsubclassWindow](#unsubclasswindow)|還原先前子類別化的視窗。|  
  
### <a name="static-methods"></a>靜態方法  
  
|||  
|-|-|  
|[GetWndClassInfo](#getwndclassinfo)|傳回的靜態執行個體[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)，它負責管理視窗類別資訊。|  
|[WindowProc](#windowproc)|處理傳送至視窗的訊息。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|  
  
## <a name="remarks"></a>備註  
 您可以使用`CWindowImpl`建立視窗或子類別化現有的視窗。 `CWindowImpl`視窗程序會使用訊息對應訊息導向適當的處理常式。  
  
 `CWindowImpl::Create` 建立視窗由管理的視窗類別資訊為基礎[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)。 `CWindowImpl` 包含[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)巨集，這表示`CWndClassInfo`註冊新的視窗類別。 如果您想要讓現有視窗類別，衍生您的類別從`CWindowImpl`並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集。 在這種情況下，`CWndClassInfo` 會依據現有的類別註冊視窗類別，但是會使用 `CWindowImpl::WindowProc`。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  由於 `CWndClassInfo` 只會管理一個視窗類別的資訊，因此每個透過 `CWindowImpl` 執行個體所建立的視窗都是以相同的視窗類別為基礎。  
  
 `CWindowImpl` 也支援視窗子類別化。 `SubclassWindow` 方法會將現有視窗附加至 `CWindowImpl` 物件，並將視窗程序變更至 `CWindowImpl::WindowProc`。 每個 `CWindowImpl` 執行個體都可以子類別化為不同的視窗。  
  
> [!NOTE]
>  任何給定的`CWindowImpl`物件，呼叫**建立**或`SubclassWindow`。 不要對同一物件叫用兩種方法。  
  
 除了`CWindowImpl`，ATL 提供[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)到在另一個物件建立所在的視窗。  
  
 基底類別解構函式 (~ **CWindowImplRoot**) 可確保視窗會消失，就會終結物件之前。  
  
 `CWindowImpl` 衍生自**CWindowImplBaseT**，其衍生自**CWindowImplRoot**，其衍生自**TBase**和[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
|如需詳細資訊|請參閱|  
|--------------------------------|---------|  
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|  
|在 ATL 中使用視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|  
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="create"></a>  CWindowImpl::Create  
 建立新的視窗類別為基礎的視窗。  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 [in]父系或擁有者的視窗控制代碼。  
  
 `rect`  
 [in]A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定視窗的位置。 `RECT`可以傳遞指標或參考。  
  
 `szWindowName`  
 [in]指定視窗的名稱。 預設值是**NULL**。  
  
 `dwStyle`  
 [in]視窗樣式。 這個值會結合 traits 類別所提供的視窗樣式。 預設值讓 traits 類別完全掌控樣式。 如需可能值的清單，請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) Windows SDK 中。  
  
 `dwExStyle`  
 [in]延伸的視窗樣式。 這個值會結合 traits 類別所提供的視窗樣式。 預設值讓 traits 類別完全掌控樣式。 如需可能值的清單，請參閱[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 `MenuOrID`  
 [in]子視窗的視窗識別項。 最上層視窗中，請在視窗的功能表控制代碼。 預設值是**0U**。  
  
 `lpCreateParam`  
 [in]視窗建立資料指標。 如需完整說明，請參閱的最後一個參數的描述[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，新建立的視窗控制代碼。 否則， **NULL**。  
  
### <a name="remarks"></a>備註  
 **建立**第一次註冊視窗類別，如果尚未註冊。 新建立的視窗會自動附加至`CWindowImpl`物件。  
  
> [!NOTE]
>  請勿呼叫**建立**如果已呼叫[SubclassWindow](#subclasswindow)。  
  
 若要使用現有的視窗類別為基礎的視窗類別，衍生您的類別從`CWindowImpl`並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集。 現有視窗類別的視窗程序儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。 如需詳細資訊，請參閱[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概觀。  
  
> [!NOTE]
>  如果使用做為值 0`MenuOrID`參數，它必須指定為 0U （預設值） 若要避免編譯器錯誤。  
  
##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc  
 由呼叫[WindowProc](#windowproc)未處理的訊息對應處理訊息。  
  
```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```  
  
### <a name="parameters"></a>參數  
 `uMsg`  
 [in]傳送至視窗的訊息。  
  
 `wParam`  
 [in]其他訊息的特定資訊。  
  
 `lParam`  
 [in]其他訊息的特定資訊。  
  
### <a name="return-value"></a>傳回值  
 訊息處理的結果。  
  
### <a name="remarks"></a>備註  
 根據預設，`DefWindowProc`呼叫[CallWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633571) Win32 函式中指定的視窗程序來傳送的訊息資訊[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
 不含任何參數的函式會自動擷取需要的參數，從目前的訊息。  
  
##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage  
 傳回目前的訊息，封裝在`MSG`結構。  
  
```
const MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>傳回值  
 目前的訊息。  
  
##  <a name="getwindowproc"></a>  CWindowImpl::GetWindowProc  
 傳回`WindowProc`，目前的視窗程序。  
  
```
virtual WNDPROC GetWindowProc();
```  
  
### <a name="return-value"></a>傳回值  
 目前的視窗程序。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以取代您自己的視窗程序。  
  
##  <a name="getwndclassinfo"></a>  CWindowImpl::GetWndClassInfo  
 由呼叫[建立](#create)存取視窗類別資訊。  
  
```
static CWndClassInfo& GetWndClassInfo();
```  
  
### <a name="return-value"></a>傳回值  
 靜態執行個體[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)。  
  
### <a name="remarks"></a>備註  
 根據預設，`CWindowImpl`透過這個方法會取得[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)巨集，指定新的視窗類別。  
  
 要讓現有視窗類別，衍生您的類別從`CWindowImpl`並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集，以覆寫`GetWndClassInfo`。 如需詳細資訊，請參閱[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概觀。  
  
 除了使用`DECLARE_WND_CLASS`和`DECLARE_WND_SUPERCLASS`巨集，可以覆寫`GetWndClassInfo`與您自己的實作。  
  
##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc  
 視窗中，根據指向下列視窗程序的其中一個。  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>備註  
  
|視窗類型|視窗程序|  
|--------------------|----------------------|  
|視窗會根據新的視窗類別，透過指定[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)巨集。|[DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572) Win32 函式。|  
|修改現有的類別，透過指定的視窗類別為基礎的視窗[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集。|現有視窗類別的視窗程序。|  
|子類別化的視窗中。|子類別化的視窗的原始視窗程序。|  
  
 [CWindowImpl::DefWindowProc](#defwindowproc)傳送訊息至視窗程序中儲存的資訊`m_pfnSuperWindowProc`。  
  
##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage  
 收到的最後一個訊息後呼叫 (通常`WM_NCDESTROY`)。  
  
```
virtual void OnFinalMessage(HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]終結視窗的控制代碼。  
  
### <a name="remarks"></a>備註  
 預設實作`OnFinalMessage`不做任何動作，但是您可以覆寫這個函式來處理清理，然後再終結視窗。 如果您想要自動刪除您的物件，在視窗解構時，您可以呼叫`delete this;`在這個函式。  
  
##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow  
 視窗所識別的子類別`hWnd`並將它附加至`CWindowImpl`物件。  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]正在子類別化的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**視窗是否成功地衍生子類別，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 子類別化的視窗現在會使用[CWindowImpl::WindowProc](#windowproc)。 原始視窗程序儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
> [!NOTE]
>  請勿呼叫`SubclassWindow`如果已呼叫[建立](#create)。  
  
##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow  
 中斷連結的子類別化的視窗`CWindowImpl`物件，並還原原始視窗程序，儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
```
HWND UnsubclassWindow();
```  
  
### <a name="return-value"></a>傳回值  
 先前子類別化的視窗控制代碼。  
  
##  <a name="windowproc"></a>  CWindowImpl::WindowProc  
 此靜態函式實作的視窗程序。  
  
```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]視窗控制代碼。  
  
 `uMsg`  
 [in]傳送至視窗的訊息。  
  
 `wParam`  
 [in]其他訊息的特定資訊。  
  
 `lParam`  
 [in]其他訊息的特定資訊。  
  
### <a name="return-value"></a>傳回值  
 訊息處理的結果。  
  
### <a name="remarks"></a>備註  
 `WindowProc` 使用預設的訊息對應 (以宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) 將導向至適當的處理常式的訊息。 如有必要，`WindowProc`呼叫[DefWindowProc](#defwindowproc)進行額外的訊息處理。 如果未處理的最後一個訊息，`WindowProc`會進行下列作業：  
  
-   執行 unsubclassing 如果視窗已 unsubclassed。  
  
-   清除 `m_hWnd`。  
  
-   呼叫[OnFinalMessage](#onfinalmessage)終結視窗之前。  
  
 您可以覆寫`WindowProc`提供不同的機制，來處理訊息。  
  
## <a name="see-also"></a>另請參閱  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
