---
title: CContainedWindowT 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 2eae6e149cf6f7422d0653c1c15f46985d8d55c8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496852"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 類別

這個類別會執行包含在另一個物件中的視窗。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>參數

*TBase*<br/>
新類別的基類。 預設基類是`CWindow`。

*TWinTraits*<br/>
定義視窗樣式的特性類別。 預設為 `CControlWinTraits`。

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)是的特製化`CContainedWindowT`。 如果您想要變更基類或特性, 請直接使用`CContainedWindowT` 。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|建構函式。 初始化資料成員, 以指定哪一個訊息對應將處理包含的視窗訊息。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|建立視窗。|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|提供預設訊息處理。|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|傳回目前訊息。|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|註冊包含視窗的視窗類別。|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|子類別化視窗。|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|變更要用來處理所包含視窗訊息的訊息對應。|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|還原先前子類別化的視窗。|
|[CContainedWindowT::WindowProc](#windowproc)|靜止處理傳送至包含視窗的訊息。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|識別哪一個訊息對應會處理包含的視窗訊息。|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|指定現有的視窗類別名稱, 新的視窗類別將以此為基礎。|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|
|[CContainedWindowT::m_pObject](#m_pobject)|指向包含物件。|

## <a name="remarks"></a>備註

`CContainedWindowT`執行包含在另一個物件中的視窗。 `CContainedWindowT`的視窗程式會在包含物件中使用訊息對應, 將訊息導向適當的處理常式。 在建立`CContainedWindowT`物件時, 您可以指定應該使用的訊息對應。

`CContainedWindowT`可讓您藉由 superclassing 現有的視窗類別來建立新視窗。 方法會先註冊以現有類別為基礎的視窗類別, 但會使用`CContainedWindowT::WindowProc`。 `Create` `Create`然後根據這個新的視窗類別建立視窗。 的`CContainedWindowT`每個實例都可以類別不同的視窗類別。

`CContainedWindowT` 也支援視窗子類別化。 `SubclassWindow` 方法會將現有視窗附加至 `CContainedWindowT` 物件，並將視窗程序變更至 `CContainedWindowT::WindowProc`。 每個 `CContainedWindowT` 執行個體都可以子類別化為不同的視窗。

> [!NOTE]
>  針對任何指定`CContainedWindowT`的物件, `Create`呼叫或`SubclassWindow`。 您不應該在相同的物件上叫用這兩種方法。

當您使用 [ATL 專案嚮導] 中的 [以依據方式**加入控制項**] 選項時, 嚮導`CContainedWindowT`會自動將資料成員加入至執行控制項的類別。 下列範例顯示如何宣告包含的視窗:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|如需詳細資訊|請參閱|
|--------------------------------|---------|
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|
|在 ATL 中使用視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|
|Windows|Windows SDK 中的[Windows](/windows/win32/winmsg/windows)和後續主題|

## <a name="inheritance-hierarchy"></a>繼承階層

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>需求

**標頭:** atlwin.h。h

##  <a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT

此函式會初始化資料成員。

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

*lpszClassName*<br/>
在包含的視窗將依據的現有視窗類別名稱。

*pObject*<br/>
在宣告訊息對應之包含物件的指標。 這個物件的類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
在識別將處理所包含視窗之訊息的訊息對應。 預設值為 0, 指定使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)宣告的預設訊息對應。 若要使用以[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的替代訊息對應, `msgMapID`請傳遞。

### <a name="remarks"></a>備註

如果您想要透過 [[建立](#create)] 建立新的視窗, 您必須針對*lpszClassName*參數傳遞現有視窗類別的名稱。 如需範例, 請參閱[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)總覽。

有三個構造函式:

- 具有三個引數的函式是通常會呼叫的函式。

- 具有兩個引數的函式會使用`TBase::GetWndClassName`來自的類別名稱。

- 如果您想要在稍後提供引數, 則會使用不含引數的函式。 當您稍後呼叫`Create`時, 必須提供視窗類別名稱、訊息對應物件和訊息對應識別碼。

如果您透過[subclasswindow 前允許](#subclasswindow)將現有視窗子類別化, 將不會使用*lpszClassName*值;因此, 您可以為此參數傳遞 Null。

##  <a name="create"></a>CContainedWindowT:: Create

呼叫[RegisterWndSuperclass](#registerwndsuperclass)來註冊以現有類別為基礎的視窗類別, 但使用[CContainedWindowT:: WindowProc](#windowproc)。

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

*lpszClassName*<br/>
在包含的視窗將依據的現有視窗類別名稱。

*pObject*<br/>
在宣告訊息對應之包含物件的指標。 這個物件的類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
在識別將處理所包含視窗之訊息的訊息對應。 預設值為 0, 指定使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)宣告的預設訊息對應。 若要使用以[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的替代訊息對應, `msgMapID`請傳遞。

*hWndParent*<br/>
在父代或擁有者視窗的控制碼。

*rect*<br/>
在指定視窗位置的[矩形](/previous-versions/dd162897\(v=vs.85\))結構。 `RECT`可以透過指標或傳址方式傳遞。

*szWindowName*<br/>
在指定視窗的名稱。 預設值為 Null。

*dwStyle*<br/>
在視窗的樣式。 預設值為 WS_CHILD &#124; WS_VISIBLE。 如需可能值的清單, 請參閱 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 。

*dwExStyle*<br/>
在擴充的視窗樣式。 預設值為 0, 表示沒有擴充樣式。 如需可能值的清單, 請參閱 Windows SDK 中的[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 。

*MenuOrID*<br/>
在若為子視窗, 則為視窗識別碼。 如果是最上層視窗, 則為視窗的功能表控制碼。 預設值為 [ **0u**]。

*lpCreateParam*<br/>
在視窗建立資料的指標。 如需完整描述, 請參閱[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)最後一個參數的描述。

### <a name="return-value"></a>傳回值

如果成功, 則為新建立之視窗的控制碼;否則為 Null。

### <a name="remarks"></a>備註

現有的視窗類別名稱會儲存在[m_lpszClassName](#m_lpszclassname)中。 `Create`然後根據這個新類別建立視窗。 新建立的視窗會自動附加至`CContainedWindowT`物件。

> [!NOTE]
>  如果您已經`Create`呼叫[subclasswindow 前允許](#subclasswindow), 請勿呼叫。

> [!NOTE]
>  如果將0當做*MenuOrID*參數的值使用, 則必須將其指定為 0u (預設值), 以避免編譯器錯誤。

##  <a name="defwindowproc"></a>CContainedWindowT::D efWindowProc

由[WindowProc](#windowproc)呼叫以處理訊息對應未處理的訊息。

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*uMsg*<br/>
在傳送至視窗的訊息。

*wParam*<br/>
在其他訊息特定資訊。

*lParam*<br/>
在其他訊息特定資訊。

### <a name="return-value"></a>傳回值

訊息處理的結果。

### <a name="remarks"></a>備註

根據預設, `DefWindowProc`會呼叫[CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 函數, 將訊息資訊傳送至[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中指定的視窗程式。

##  <a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage

傳回目前的訊息 (`m_pCurrentMsg`)。

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>傳回值

封裝在`MSG`結構中的目前訊息。

##  <a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID

保留目前用於包含視窗之訊息對應的識別碼。

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>備註

此訊息對應必須在包含物件中宣告。

預設的訊息對應 (以[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)宣告) 一律會以零來識別。 以[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的替代訊息對應, 是由`msgMapID`所識別。

`m_dwMsgMapID`會先由函式初始化, 而且可以藉由呼叫[SwitchMessageMap](#switchmessagemap)來變更。 如需範例, 請參閱[CContainedWindowT 總覽](../../atl/reference/ccontainedwindowt-class.md)。

##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName

指定現有視窗類別的名稱。

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>備註

當您建立視窗時, [create](#create)會註冊以這個現有類別為基礎的新視窗類別, 但會使用[CContainedWindowT:: WindowProc](#windowproc)。

`m_lpszClassName`由函式初始化。 如需範例, 請參閱[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)總覽。

##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc

如果包含的視窗已子類別`m_pfnSuperWindowProc`化, 則會指向 window 類別的原始視窗程式。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>備註

如果包含的視窗是 superclass, 表示它是以修改現有類別的視窗類別為基礎, `m_pfnSuperWindowProc`則會指向現有的視窗類別的視窗程式。

[DefWindowProc](#defwindowproc)方法會將訊息資訊傳送至儲存在中`m_pfnSuperWindowProc`的視窗程式。

##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject

指向包含`CContainedWindowT`物件的物件。

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>備註

此容器 (其類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)) 會宣告包含的視窗所使用的訊息對應。

`m_pObject`由函式初始化。 如需範例, 請參閱[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)總覽。

##  <a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass

由[Create](#create)呼叫以註冊包含視窗的視窗類別。

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>傳回值

如果成功, 則為可唯一識別要註冊之視窗類別的 atom;否則為零。

### <a name="remarks"></a>備註

這個視窗類別是以現有類別為基礎, 但使用[CContainedWindowT:: WindowProc](#windowproc)。 現有視窗類別的名稱和視窗程式會分別儲存在[m_lpszClassName](#m_lpszclassname)和[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

##  <a name="subclasswindow"></a>CContainedWindowT:: Subclasswindow 前允許

子類別化*hWnd*所識別的視窗, 並將`CContainedWindowT`它附加至物件。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在要子類別化之視窗的控制碼。

### <a name="return-value"></a>傳回值

如果已成功將視窗子類別化, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

子類別化視窗現在會使用[CContainedWindowT:: WindowProc](#windowproc)。 原始的視窗程式會儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
>  如果您已經`SubclassWindow`呼叫[Create](#create), 請勿呼叫。

##  <a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap

變更將用來處理所包含視窗訊息的訊息對應。

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>參數

*dwMsgMapID*<br/>
在訊息對應識別碼。 若要使用以[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)宣告的預設訊息對應, 請傳遞零。 若要使用以[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的替代訊息對應, `msgMapID`請傳遞。

### <a name="remarks"></a>備註

訊息對應必須定義在包含物件中。

您一開始會在此函式中指定訊息對應識別碼。

##  <a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow

從`CContainedWindowT`物件卸離子類別化的視窗, 並還原原始視窗程式, 儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>參數

*bForce*<br/>
在設定為 TRUE, 即使此`CContainedWindowT`物件的視窗程式目前不在使用中, 也會強制還原原始視窗程式。 如果*bForce*設定為 FALSE, 而且這個`CContainedWindowT`物件的視窗程式目前不在使用中, 則不會還原原始的視窗程式。

### <a name="return-value"></a>傳回值

先前子類別化之視窗的控制碼。 如果*bForce*設定為 FALSE, 而且這個`CContainedWindowT`物件的視窗程式目前不在使用中, 則會傳回 Null。

### <a name="remarks"></a>備註

只有當您想要在終結視窗之前還原原始視窗程式時, 才使用這個方法。 否則, [WindowProc](#windowproc)會在視窗損毀時自動執行此動作。

##  <a name="windowproc"></a>CContainedWindowT:: WindowProc

這個靜態方法會實作為視窗程式。

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在視窗的控制碼。

*uMsg*<br/>
在傳送至視窗的訊息。

*wParam*<br/>
在其他訊息特定資訊。

*lParam*<br/>
在其他訊息特定資訊。

### <a name="return-value"></a>傳回值

訊息處理的結果。

### <a name="remarks"></a>備註

`WindowProc`將訊息導向[m_dwMsgMapID](#m_dwmsgmapid)所識別的訊息對應。 如有必要`WindowProc` , 會呼叫[DefWindowProc](#defwindowproc)以進行其他訊息處理。

## <a name="see-also"></a>另請參閱

[CWindow 類別](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap 類別](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[類別總覽](../../atl/atl-class-overview.md)
