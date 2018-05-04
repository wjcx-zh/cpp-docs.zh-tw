---
title: CContainedWindowT 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
dev_langs:
- C++
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f3f90e23eed3bd1eba80bbf90fe73de45eb7cfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 類別
這個類別會實作包含在另一個物件內的視窗。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class CContainedWindowT : public TBase
```  
  
#### <a name="parameters"></a>參數  
 *TBase*  
 您的新類別的基底類別。 預設基底類別是`CWindow`。  
  
 `TWinTraits`  
 定義視窗樣式 traits 類別。 預設值為 `CControlWinTraits`。  
  
> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)的特製化`CContainedWindowT`。 如果您想要變更基底類別或特性，使用`CContainedWindowT`直接。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|建構函式。 初始化指定的訊息對應會包含的視窗的訊息處理的資料成員。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CContainedWindowT::Create](#create)|建立視窗。|  
|[CContainedWindowT::DefWindowProc](#defwindowproc)|提供預設訊息處理。|  
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|傳回目前訊息。|  
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|登錄包含視窗的視窗類別。|  
|[CContainedWindowT::SubclassWindow](#subclasswindow)|子類別化視窗。|  
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|用來處理所包含的視窗訊息的訊息對應的變更。|  
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|還原先前子類別化的視窗。|  
|[CContainedWindowT::WindowProc](#windowproc)|（靜態）處理訊息傳送至自主的視窗。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|識別哪些訊息對應會包含的視窗的訊息處理。|  
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|指定新的視窗類別依據現有視窗類別名稱。|  
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|  
|[CContainedWindowT::m_pObject](#m_pobject)|指向包含的物件。|  
  
## <a name="remarks"></a>備註  
 `CContainedWindowT` 實作包含在另一個物件內的視窗。 `CContainedWindowT`視窗程序會使用訊息對應中包含的物件，直接將訊息到適當的處理常式。 建構時`CContainedWindowT`物件，您指定應該使用哪一個訊息對應。  
  
 `CContainedWindowT` 可讓您根據 superclassing 現有視窗類別建立新的視窗。 **建立**方法會先註冊視窗類別現有的類別為基礎，但會使用`CContainedWindowT::WindowProc`。 **建立**接著會建立這個新的視窗類別為基礎的視窗。 每個執行個體`CContainedWindowT`可以超級類別不同的視窗類別。  
  
 `CContainedWindowT` 也支援視窗子類別化。 `SubclassWindow` 方法會將現有視窗附加至 `CContainedWindowT` 物件，並將視窗程序變更至 `CContainedWindowT::WindowProc`。 每個 `CContainedWindowT` 執行個體都可以子類別化為不同的視窗。  
  
> [!NOTE]
>  任何給定的`CContainedWindowT`物件，呼叫**建立**或`SubclassWindow`。 您不應叫用相同的物件上的這兩種方法。  
  
 當您使用**加入控制項根據**選項在 ATL 專案精靈中，精靈會自動將`CContainedWindowT`来實作此控制項的類別資料成員。 下列範例會示範如何宣告，包含的視窗：  
  
 [!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]  
  
|如需詳細資訊|請參閱|  
|--------------------------------|---------|  
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|  
|在 ATL 中使用視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|  
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|  
|Windows|[Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595)和後續 Windows SDK 中的主題|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `TBase`  
  
 `CContainedWindowT`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="ccontainedwindowt"></a>  CContainedWindowT::CContainedWindowT  
 建構函式初始化資料成員。  
  
```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```     
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 [in]包含的視窗依據現有視窗類別名稱。  
  
 `pObject`  
 [in]包含宣告的訊息對應的物件指標。 此物件的類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
 `dwMsgMapID`  
 [in]識別會被收納的視窗訊息處理的訊息對應。 預設值為 0，指定與宣告的預設訊息對應[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 若要使用替代的訊息對應宣告為具有[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，傳遞`msgMapID`。  
  
### <a name="remarks"></a>備註  
 如果您想要建立新的視窗，透過[建立](#create)，您必須傳遞的現有視窗類別名稱`lpszClassName`參數。 如需範例，請參閱[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)概觀。  
  
 有三個建構函式：  
  
-   具有三個引數的建構函式是通常稱為。  
  
-   兩個引數的建構函式會使用類別名稱，從**TBase::GetWndClassName**。  
  
-   如果您想要稍後提供的引數，會使用不含引數的建構函式。 您稍後呼叫時必須提供的視窗類別名稱、 訊息對應物件和訊息對應識別碼**建立**。  
  
 如果您子類別化現有視窗透過[SubclassWindow](#subclasswindow)、`lpszClassName`將不會使用值; 因此，您可以傳遞**NULL**這個參數。  
  
##  <a name="create"></a>  CContainedWindowT::Create  
 呼叫[RegisterWndSuperclass](#registerwndsuperclass)註冊視窗類別現有的類別為基礎，但會使用[CContainedWindowT::WindowProc](#windowproc)。  
  
```
HWND Create(  
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 [in]包含的視窗依據現有視窗類別名稱。  
  
 `pObject`  
 [in]包含宣告的訊息對應的物件指標。 此物件的類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
 `dwMsgMapID`  
 [in]識別會被收納的視窗訊息處理的訊息對應。 預設值為 0，指定與宣告的預設訊息對應[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 若要使用替代的訊息對應宣告為具有[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，傳遞`msgMapID`。  
  
 `hWndParent`  
 [in]父系或擁有者的視窗控制代碼。  
  
 `rect`  
 [in]A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定視窗的位置。 `RECT`可以傳遞指標或參考。  
  
 `szWindowName`  
 [in]指定視窗的名稱。 預設值是**NULL**。  
  
 `dwStyle`  
 [in]視窗樣式。 預設值是**WS_CHILD &#124; WS_VISIBLE**。 如需可能值的清單，請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) Windows SDK 中。  
  
 `dwExStyle`  
 [in]延伸的視窗樣式。 預設值為 0，這表示沒有延伸的樣式。 如需可能值的清單，請參閱[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 `MenuOrID`  
 [in]子視窗的視窗識別項。 最上層視窗中，請在視窗的功能表控制代碼。 預設值是**0U**。  
  
 `lpCreateParam`  
 [in]視窗建立資料指標。 如需完整說明，請參閱的最後一個參數的描述[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，新建立的視窗; 的控制代碼否則， **NULL**。  
  
### <a name="remarks"></a>備註  
 現有的視窗類別名稱會儲存在[m_lpszClassName](#m_lpszclassname)。 **建立**接著會建立這個新的類別為基礎的視窗。 新建立的視窗會自動附加至`CContainedWindowT`物件。  
  
> [!NOTE]
>  請勿呼叫**建立**如果已呼叫[SubclassWindow](#subclasswindow)。  
  
> [!NOTE]
>  如果使用做為值 0`MenuOrID`參數，它必須指定為 0U （預設值） 若要避免編譯器錯誤。  
  
##  <a name="defwindowproc"></a>  CContainedWindowT::DefWindowProc  
 由呼叫[WindowProc](#windowproc)未處理的訊息對應處理訊息。  
  
```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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
  
##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage  
 傳回目前訊息 ( **m_pCurrentMsg**)。  
  
```
const _ATL_MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>傳回值  
 目前的訊息，封裝在`MSG`結構。  
  
##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID  
 保存目前正用於包含視窗的訊息對應的識別碼。  
  
```
DWORD m_dwMsgMapID;
```  
  
### <a name="remarks"></a>備註  
 此訊息的對應必須宣告中包含的物件。  
  
 預設的訊息對應，以宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，一律由零。 使用替代的訊息對應宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，由`msgMapID`。  
  
 `m_dwMsgMapID` 建構函式會先初始化，而且可以藉由呼叫變更[SwitchMessageMap](#switchmessagemap)。 如需範例，請參閱[CContainedWindowT 概觀](../../atl/reference/ccontainedwindowt-class.md)。  
  
##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName  
 指定現有的視窗類別名稱。  
  
```
LPTSTR m_lpszClassName;
```  
  
### <a name="remarks"></a>備註  
 當您建立一個視窗，[建立](#create)註冊這個現有的類別為基礎，但是會使用新的視窗類別[CContainedWindowT::WindowProc](#windowproc)。  
  
 `m_lpszClassName` 會初始化建構函式。 如需範例，請參閱[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概觀。  
  
##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc  
 如果包含的視窗子類別化，`m_pfnSuperWindowProc`指向視窗類別的原始視窗程序。  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>備註  
 如果 superclass 包含的視窗，這表示它為基礎的視窗類別，以修改現有的類別，`m_pfnSuperWindowProc`指向現有視窗類別的視窗程序。  
  
 [DefWindowProc](#defwindowproc)方法會將訊息資訊傳送至視窗程序儲存在`m_pfnSuperWindowProc`。  
  
##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject  
 指向物件，包含`CContainedWindowT`物件。  
  
```
CMessageMap* m_pObject;
```  
  
### <a name="remarks"></a>備註  
 此容器，其類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)，宣告包含視窗所使用的訊息對應。  
  
 `m_pObject` 會初始化建構函式。 如需範例，請參閱[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概觀。  
  
##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass  
 由呼叫[建立](#create)註冊包含視窗的視窗類別。  
  
```
ATOM RegisterWndSuperClass();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，atom 可唯一識別視窗類別註冊。否則為零。  
  
### <a name="remarks"></a>備註  
 此視窗類別現有的類別為基礎，但是會使用[CContainedWindowT::WindowProc](#windowproc)。 現有的視窗類別名稱和視窗程序會儲存在[m_lpszClassName](#m_lpszclassname)和[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)分別。  
  
##  <a name="subclasswindow"></a>  CContainedWindowT::SubclassWindow  
 視窗所識別的子類別`hWnd`並將它附加至`CContainedWindowT`物件。  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]正在子類別化的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**視窗是否成功地衍生子類別，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 子類別化的視窗現在會使用[CContainedWindowT::WindowProc](#windowproc)。 原始視窗程序儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
> [!NOTE]
>  請勿呼叫`SubclassWindow`如果已呼叫[建立](#create)。  
  
##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap  
 變更的訊息對應將用於處理包含的視窗的訊息。  
  
```
void SwitchMessageMap(DWORD dwMsgMapID);
```  
  
### <a name="parameters"></a>參數  
 `dwMsgMapID`  
 [in]訊息對應識別碼。 若要使用預設的訊息對應宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，傳遞零。 若要使用替代的訊息對應宣告為具有[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，傳遞`msgMapID`。  
  
### <a name="remarks"></a>備註  
 訊息對應必須定義中包含的物件。  
  
 您一開始建構函式中指定的訊息對應的識別項。  
  
##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow  
 中斷連結的子類別化的視窗`CContainedWindowT`物件，並還原原始視窗程序，儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bForce`  
 [in]設定為**TRUE**強制還原原始視窗程序即使這個視窗程序`CContainedWindowT`物件不是目前作用中。 如果`bForce`設**FALSE**和視窗程序，這個`CContainedWindowT`物件不是目前作用中，將不會還原原始視窗程序。  
  
### <a name="return-value"></a>傳回值  
 先前子類別化的視窗控制代碼。 如果`bForce`設**FALSE**和視窗程序，這個`CContainedWindowT`物件不是目前作用中，傳回**NULL**。  
  
### <a name="remarks"></a>備註  
 只有當您想要還原原始視窗程序之前的視窗終結時，請使用這個方法。 否則， [WindowProc](#windowproc)會自動執行此作業會在終結視窗時。  
  
##  <a name="windowproc"></a>  CContainedWindowT::WindowProc  
 這個靜態方法實作的視窗程序。  
  
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
 `WindowProc` 會指示訊息所識別的訊息對應至[m_dwMsgMapID](#m_dwmsgmapid)。 如有必要，`WindowProc`呼叫[DefWindowProc](#defwindowproc)進行額外的訊息處理。  
  
## <a name="see-also"></a>另請參閱  
 [CWindow 類別](../../atl/reference/cwindow-class.md)   
 [CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)   
 [CMessageMap 類別](../../atl/reference/cmessagemap-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [類別概觀](../../atl/atl-class-overview.md)
