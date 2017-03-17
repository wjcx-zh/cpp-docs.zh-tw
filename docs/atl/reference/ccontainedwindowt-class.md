---
title: "CContainedWindowT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 23
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
ms.openlocfilehash: e10aa4b455696fd217f88b6eb1de2421fccda6de
ms.lasthandoff: 02/24/2017

---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 類別
這個類別會實作包含在另一個物件中的視窗。  
  
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
 Traits 類別定義視窗樣式。 預設為 `CControlWinTraits`。  
  
> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)是特製化的`CContainedWindowT`。 如果您想要變更的基底類別或特性，使用`CContainedWindowT`直接。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|建構函式。 資料成員初始化為指定的訊息對應會處理包含的視窗的訊息。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CContainedWindowT::Create](#create)|建立視窗。|  
|[CContainedWindowT::DefWindowProc](#defwindowproc)|提供預設訊息處理。|  
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|傳回目前訊息。|  
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|登錄包含視窗的視窗類別。|  
|[CContainedWindowT::SubclassWindow](#subclasswindow)|子類別化視窗。|  
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|變更用來處理所包含的視窗訊息的訊息對應。|  
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|還原先前子類別化的視窗。|  
|[CContainedWindowT::WindowProc](#windowproc)|（靜態）處理訊息傳送至所包含的視窗。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|識別哪些訊息對應會處理包含的視窗的訊息。|  
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|指定新的視窗類別依據現有視窗類別名稱。|  
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|  
|[CContainedWindowT::m_pObject](#m_pobject)|包含物件的指標。|  
  
## <a name="remarks"></a>備註  
 `CContainedWindowT`實作包含在另一個物件中的視窗。 `CContainedWindowT`視窗程序會使用訊息對應中包含的物件，直接將訊息至適當的處理常式。 當建構`CContainedWindowT`物件時，您指定應該使用哪些訊息對應。  
  
 `CContainedWindowT`可讓您透過 superclassing 現有視窗類別建立新的視窗。 **建立**方法第一次註冊視窗類別，根據現有的類別，但使用`CContainedWindowT::WindowProc`。 **建立**接著會建立這個新的視窗類別為基礎的視窗。 每個執行個體`CContainedWindowT`可以超級類別不同的視窗類別。  
  
 `CContainedWindowT` 也支援視窗子類別化。 `SubclassWindow` 方法會將現有視窗附加至 `CContainedWindowT` 物件，並將視窗程序變更至 `CContainedWindowT::WindowProc`。 每個 `CContainedWindowT` 執行個體都可以子類別化為不同的視窗。  
  
> [!NOTE]
>  對於任一個`CContainedWindowT`物件，呼叫**建立**或`SubclassWindow`。 您不應該叫用的相同物件上的這兩種方法。  
  
 當您使用**加入控制項根據**選項在 ATL 專案精靈 中，精靈會自動加入`CContainedWindowT`来實作控制項的類別資料成員。 下列範例會示範如何宣告，包含的視窗︰  
  
 [!code-cpp[NVC_ATL_Windowing #&38;](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing #&39;](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing #&40;](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]  
  
|如需詳細資訊|請參閱|  
|--------------------------------|---------|  
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|  
|在 ATL 中使用視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|  
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|  
|Windows|[Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595)並在後續主題[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `TBase`  
  
 `CContainedWindowT`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT  
 建構函式會初始化資料成員。  
  
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
 [in]識別會被收納的視窗訊息處理的訊息對應。 預設值為 0，指定預設的訊息對應宣告[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)。 若要使用替代訊息對應宣告[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，傳遞`msgMapID`。  
  
### <a name="remarks"></a>備註  
 如果您想要建立新的視窗，透過[建立](#create)，您必須傳遞的現有視窗類別名稱`lpszClassName`參數。 如需範例，請參閱[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)概觀。  
  
 有三個建構函式︰  
  
-   具有三個引數的建構函式是通常稱為。  
  
-   兩個引數的建構函式會使用類別名稱從**TBase::GetWndClassName**。  
  
-   如果您想要稍後提供的引數，會使用不含引數的建構函式。 您稍後呼叫時必須提供的視窗類別名稱、 訊息對應物件和訊息對應識別碼**建立**。  
  
 如果您子類別化現有視窗透過[SubclassWindow](#subclasswindow)、`lpszClassName`值將不會使用; 因此，您可以傳遞**NULL**這個參數。  
  
##  <a name="create"></a>CContainedWindowT::Create  
 呼叫[RegisterWndSuperclass](#registerwndsuperclass)註冊視窗類別，根據現有的類別，但使用[CContainedWindowT::WindowProc](#windowproc)。  
  
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
 [in]識別會被收納的視窗訊息處理的訊息對應。 預設值為 0，指定預設的訊息對應宣告[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)。 若要使用替代訊息對應宣告[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，傳遞`msgMapID`。  
  
 `hWndParent`  
 [in]父系或擁有者的視窗控制代碼。  
  
 `rect`  
 [in]A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定視窗的位置。 `RECT`可以傳遞指標或參考。  
  
 `szWindowName`  
 [in]指定的視窗名稱。 預設值是**NULL**。  
  
 `dwStyle`  
 [in]視窗樣式。 預設值是**WS_CHILD |WS_VISIBLE**。 如需可能的值，請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwExStyle`  
 [in]延伸的視窗樣式。 預設值為 0，表示沒有任何延伸的樣式。 如需可能的值，請參閱[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `MenuOrID`  
 [in]子視窗中，視窗識別項。 最上層視窗中，請在視窗的功能表控制代碼。 預設值是**0U**。  
  
 `lpCreateParam`  
 [in]視窗建立資料指標。 如需完整的說明，請參閱的最後一個參數的描述[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，新建立的視窗; 控制代碼否則， **NULL**。  
  
### <a name="remarks"></a>備註  
 現有視窗類別名稱會儲存在[m_lpszClassName](#m_lpszclassname)。 **建立**接著會建立這個新類別為基礎的視窗。 新建立的視窗會自動附加至`CContainedWindowT`物件。  
  
> [!NOTE]
>  請勿呼叫**建立**如果已呼叫[SubclassWindow](#subclasswindow)。  
  
> [!NOTE]
>  如果使用 0 做為值`MenuOrID`參數，它必須指定為 0U （預設值） 以避免編譯器錯誤。  
  
##  <a name="defwindowproc"></a>CContainedWindowT::DefWindowProc  
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
 [in]其他訊息特定資訊。  
  
 `lParam`  
 [in]其他訊息特定資訊。  
  
### <a name="return-value"></a>傳回值  
 訊息處理的結果。  
  
### <a name="remarks"></a>備註  
 根據預設，`DefWindowProc`呼叫[CallWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633571) Win32 函式中指定的視窗程序來傳送的訊息資訊[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
##  <a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage  
 傳回目前訊息 ( **m_pCurrentMsg**)。  
  
```
const _ATL_MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>傳回值  
 目前的訊息，以封裝`MSG`結構。  
  
##  <a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID  
 保留目前正用於包含視窗的訊息對應的識別碼。  
  
```
DWORD m_dwMsgMapID;
```  
  
### <a name="remarks"></a>備註  
 此訊息的對應必須宣告中包含的物件。  
  
 預設的訊息對應，以宣告[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)，一定會識別為零。 以宣告的替代訊息對應， [ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，由`msgMapID`。  
  
 `m_dwMsgMapID`當初次初始化建構函式，而且可以變更藉由呼叫[SwitchMessageMap](#switchmessagemap)。 如需範例，請參閱[CContainedWindowT 概觀](../../atl/reference/ccontainedwindowt-class.md)。  
  
##  <a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName  
 指定現有視窗類別名稱。  
  
```
LPTSTR m_lpszClassName;
```  
  
### <a name="remarks"></a>備註  
 當您建立一個視窗，[建立](#create)會註冊新的視窗類別，這個現有的類別為基礎，但使用[CContainedWindowT::WindowProc](#windowproc)。  
  
 `m_lpszClassName`初始化建構函式。 如需範例，請參閱[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概觀。  
  
##  <a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc  
 如果包含的視窗進行子類別化，`m_pfnSuperWindowProc`指向視窗類別的原始視窗程序。  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>備註  
 如果包含的視窗 superclass，意思，它根據視窗類別，以修改現有的類別，`m_pfnSuperWindowProc`指向現有視窗類別的視窗程序。  
  
 [DefWindowProc](#defwindowproc)方法會將訊息資訊傳送至視窗程序儲存在`m_pfnSuperWindowProc`。  
  
##  <a name="m_pobject"></a>CContainedWindowT::m_pObject  
 指向物件，其中包含`CContainedWindowT`物件。  
  
```
CMessageMap* m_pObject;
```  
  
### <a name="remarks"></a>備註  
 此容器，其類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)，宣告所含的視窗所使用的訊息對應。  
  
 `m_pObject`初始化建構函式。 如需範例，請參閱[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概觀。  
  
##  <a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass  
 由呼叫[建立](#create)以註冊包含視窗的視窗類別。  
  
```
ATOM RegisterWndSuperClass();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，atom，可唯一識別視窗類別註冊。反之則為零。  
  
### <a name="remarks"></a>備註  
 此視窗類別根據現有的類別，但使用[CContainedWindowT::WindowProc](#windowproc)。 現有視窗類別的名稱和視窗程序會儲存在[m_lpszClassName](#m_lpszclassname)和[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)分別。  
  
##  <a name="subclasswindow"></a>CContainedWindowT::SubclassWindow  
 子視窗由`hWnd`，並將它附加`CContainedWindowT`物件。  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 [in]在子類別化的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**視窗是否成功子類別，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 子類別化的視窗現在會使用[CContainedWindowT::WindowProc](#windowproc)。 原始視窗程序儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
> [!NOTE]
>  請勿呼叫`SubclassWindow`如果已呼叫[建立](#create)。  
  
##  <a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap  
 變更的訊息對應將用於處理包含的視窗的訊息。  
  
```
void SwitchMessageMap(DWORD dwMsgMapID);
```  
  
### <a name="parameters"></a>參數  
 `dwMsgMapID`  
 [in]訊息對應識別項。 若要使用預設的訊息對應宣告[BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)，傳遞零。 若要使用替代訊息對應宣告[ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)，傳遞`msgMapID`。  
  
### <a name="remarks"></a>備註  
 訊息對應必須定義中包含的物件。  
  
 您一開始會在建構函式中指定的訊息對應識別項。  
  
##  <a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow  
 中斷連結子類別化的視窗，從`CContainedWindowT`物件，並還原原始視窗程序，儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。  
  
```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bForce`  
 [in]設定為**TRUE**強制要還原原始的視窗程序即使這個視窗程序`CContainedWindowT`物件不是目前使用中。 如果`bForce`設為**FALSE** ，而這個視窗程序`CContainedWindowT`物件不是目前使用中，將不會還原原始的視窗程序。  
  
### <a name="return-value"></a>傳回值  
 先前子類別化的視窗控制代碼。 如果`bForce`設為**FALSE** ，而這個視窗程序`CContainedWindowT`物件不是目前使用中，會傳回**NULL**。  
  
### <a name="remarks"></a>備註  
 只有當您想要還原視窗被終結之前的原始視窗程序，請使用這個方法。 否則， [WindowProc](#windowproc)會自動執行這項操作時終結視窗。  
  
##  <a name="windowproc"></a>CContainedWindowT::WindowProc  
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
 [in]其他訊息特定資訊。  
  
 `lParam`  
 [in]其他訊息特定資訊。  
  
### <a name="return-value"></a>傳回值  
 訊息處理的結果。  
  
### <a name="remarks"></a>備註  
 `WindowProc`指示訊息所識別的訊息對應至[m_dwMsgMapID](#m_dwmsgmapid)。 如有必要，`WindowProc`呼叫[DefWindowProc](#defwindowproc)處理其他訊息。  
  
## <a name="see-also"></a>另請參閱  
 [CWindow 類別](../../atl/reference/cwindow-class.md)   
 [CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)   
 [CMessageMap 類別](../../atl/reference/cmessagemap-class.md)   
 [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)   
 [ALT_MSG_MAP](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)   
 [類別概觀](../../atl/atl-class-overview.md)

