---
title: CWindowImpl 類別
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: b8b633dcf4ea14e899ee00552b553476cf697689
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417765"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 類別

提供建立或子類別化視窗的方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的新類別，衍生自 `CWindowImpl`。

*TBase*<br/>
您類別的基底類別。 根據預設，基底類別為[CWindow](../../atl/reference/cwindow-class.md)。

*TWinTraits*<br/>
定義視窗樣式的[特性類別](../../atl/understanding-window-traits.md)。 預設值為 `CControlWinTraits`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWindowImpl：： Create](#create)|建立視窗。|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT 方法

|||
|-|-|
|[DefWindowProc](#defwindowproc)|提供預設訊息處理。|
|[GetCurrentMessage](#getcurrentmessage)|傳回目前訊息。|
|[GetWindowProc](#getwindowproc)|傳回目前的視窗程序。|
|[OnFinalMessage](#onfinalmessage)|在收到最後一個訊息之後呼叫（通常是 WM_NCDESTROY）。|
|[Subclasswindow 前允許](#subclasswindow)|子類別化視窗。|
|[UnsubclassWindow](#unsubclasswindow)|還原先前子類別化的視窗。|

### <a name="static-methods"></a>靜態方法

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|傳回[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的靜態實例，它會管理視窗類別資訊。|
|[WindowProc](#windowproc)|處理傳送至視窗的訊息。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|

## <a name="remarks"></a>備註

您可以使用 `CWindowImpl` 來建立視窗，或將現有的視窗子類別化。 `CWindowImpl` 視窗程式會使用訊息對應，將訊息導向至適當的處理常式。

`CWindowImpl::Create` 會根據[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)所管理的視窗類別資訊來建立視窗。 `CWindowImpl` 包含[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏，這表示 `CWndClassInfo` 會註冊新的視窗類別。 如果您想要將現有的視窗類別設為超級類別，請從 `CWindowImpl` 衍生您的類別，並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏。 在這種情況下，`CWndClassInfo` 會依據現有的類別註冊視窗類別，但是會使用 `CWindowImpl::WindowProc`。 例如，

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  由於 `CWndClassInfo` 只會管理一個視窗類別的資訊，因此每個透過 `CWindowImpl` 執行個體所建立的視窗都是以相同的視窗類別為基礎。

`CWindowImpl` 也支援視窗子類別化。 `SubclassWindow` 方法會將現有視窗附加至 `CWindowImpl` 物件，並將視窗程序變更至 `CWindowImpl::WindowProc`。 每個 `CWindowImpl` 執行個體都可以子類別化為不同的視窗。

> [!NOTE]
>  針對任何指定的 `CWindowImpl` 物件，呼叫 `Create` 或 `SubclassWindow`。 不要對同一物件叫用兩種方法。

除了 `CWindowImpl`以外，ATL 還提供[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)來建立包含在另一個物件中的視窗。

基類析構函式（~ `CWindowImplRoot`）可確保在終結物件之前，視窗已消失。

`CWindowImpl` 衍生自 `CWindowImplBaseT`，而此衍生自 `CWindowImplRoot`，而此衍生自 `TBase` 和[CMessageMap](../../atl/reference/cmessagemap-class.md)。

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

**標頭：** atlwin.h。h

##  <a name="create"></a>CWindowImpl：： Create

根據新的視窗類別建立視窗。

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

*hWndParent*<br/>
在父代或擁有者視窗的控制碼。

*各種*<br/>
在指定視窗位置的[矩形](/previous-versions/dd162897\(v=vs.85\))結構。 `RECT` 可以透過指標或傳址方式來傳遞。

*szWindowName*<br/>
在指定視窗的名稱。 預設值為 NULL。

*dwStyle*<br/>
在視窗的樣式。 這個值會與視窗的特性類別所提供的樣式結合。 預設值可讓特性類別完全控制樣式。 如需可能值的清單，請參閱 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 。

*dwExStyle*<br/>
在擴充的視窗樣式。 這個值會與視窗的特性類別所提供的樣式結合。 預設值可讓特性類別完全控制樣式。 如需可能值的清單，請參閱 Windows SDK 中的[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 。

*MenuOrID*<br/>
在若為子視窗，則為視窗識別碼。 如果是最上層視窗，則為視窗的功能表控制碼。 預設值為 [ **0u**]。

*lpCreateParam*<br/>
在視窗建立資料的指標。 如需完整描述，請參閱[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)最後一個參數的描述。

### <a name="return-value"></a>傳回值

如果成功，則為新建立之視窗的控制碼。 否則為 NULL。

### <a name="remarks"></a>備註

`Create` 會先註冊視窗類別（如果尚未註冊）。 新建立的視窗會自動附加至 `CWindowImpl` 物件。

> [!NOTE]
>  如果您已呼叫[subclasswindow 前允許](#subclasswindow)，請勿呼叫 `Create`。

若要使用以現有視窗類別為基礎的視窗類別，請從 `CWindowImpl` 衍生您的類別，並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏。 現有視窗類別的視窗程式會儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。 如需詳細資訊，請參閱[CWindowImpl](../../atl/reference/cwindowimpl-class.md)總覽。

> [!NOTE]
>  如果將0當做*MenuOrID*參數的值使用，則必須將其指定為0u （預設值），以避免編譯器錯誤。

##  <a name="defwindowproc"></a>CWindowImpl：:D efWindowProc

由[WindowProc](#windowproc)呼叫以處理訊息對應未處理的訊息。

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
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

根據預設，`DefWindowProc` 會呼叫[CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 函數，將訊息資訊傳送至[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中指定的視窗程式。

沒有參數的函式會自動從目前訊息抓取所需的參數。

##  <a name="getcurrentmessage"></a>CWindowImpl：： GetCurrentMessage

傳回封裝在 `MSG` 結構中的目前訊息。

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>傳回值

目前的訊息。

##  <a name="getwindowproc"></a>CWindowImpl：： GetWindowProc

傳回目前的視窗程式 `WindowProc`。

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>傳回值

目前的視窗程式。

### <a name="remarks"></a>備註

覆寫這個方法，將視窗程式取代為您自己的進程。

##  <a name="getwndclassinfo"></a>CWindowImpl：： GetWndClassInfo

由[Create](#create)呼叫以存取視窗類別資訊。

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>傳回值

[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的靜態實例。

### <a name="remarks"></a>備註

根據預設，`CWindowImpl` 會透過[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏取得這個方法，這會指定新的視窗類別。

若要將現有的視窗類別設為超級類別，請從 `CWindowImpl` 衍生您的類別，並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏以覆寫 `GetWndClassInfo`。 如需詳細資訊，請參閱[CWindowImpl](../../atl/reference/cwindowimpl-class.md)總覽。

除了使用 DECLARE_WND_CLASS 和 DECLARE_WND_SUPERCLASS 宏之外，您還可以使用自己的執行覆寫 `GetWndClassInfo`。

##  <a name="m_pfnsuperwindowproc"></a>CWindowImpl：： m_pfnSuperWindowProc

視視窗而定，會指向下列其中一個視窗程式。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>備註

|視窗類型|視窗程式|
|--------------------|----------------------|
|以新視窗類別為基礎的視窗，透過[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏指定。|[DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32 函數。|
|以修改現有類別的視窗類別為基礎的視窗，透過[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏指定。|現有視窗類別的視窗程式。|
|子類別化的視窗。|子類別化視窗的原始視窗程式。|

[CWindowImpl：:D efwindowproc](#defwindowproc)會將訊息資訊傳送至儲存在 `m_pfnSuperWindowProc`中的視窗程式。

##  <a name="onfinalmessage"></a>CWindowImpl：： OnFinalMessage

在收到最後一則訊息之後呼叫（通常是 WM_NCDESTROY）。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在要終結之視窗的控制碼。

### <a name="remarks"></a>備註

`OnFinalMessage` 的預設執行不會執行任何工作，但是您可以覆寫此函式來處理清除，然後再終結視窗。 如果您想要在視窗損毀時自動刪除物件，您可以在此函式中呼叫**delete this** 。

##  <a name="subclasswindow"></a>CWindowImpl：： Subclasswindow 前允許

子類別化*hWnd*所識別的視窗，並將它附加至 `CWindowImpl` 物件。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在要子類別化之視窗的控制碼。

### <a name="return-value"></a>傳回值

如果已成功將視窗子類別化，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

子類別化視窗現在會使用[CWindowImpl：： WindowProc](#windowproc)。 原始的視窗程式會儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
>  如果您已經呼叫 [[建立](#create)]，請勿呼叫 `SubclassWindow`。

##  <a name="unsubclasswindow"></a>CWindowImpl：： UnsubclassWindow

從 `CWindowImpl` 物件卸離子類別化的視窗，並還原原始視窗程式，並儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>傳回值

先前子類別化之視窗的控制碼。

##  <a name="windowproc"></a>CWindowImpl：： WindowProc

這個靜態函式會實作用視窗程式。

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

`WindowProc` 使用預設的訊息對應（使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)宣告），將訊息導向適當的處理常式。 如有必要，`WindowProc` 會呼叫[DefWindowProc](#defwindowproc)以進行其他訊息處理。 如果未處理最後的訊息，`WindowProc` 會執行下列動作：

- 如果視窗是 unsubclassed，則執行 unsubclassing。

- 清除 `m_hWnd`。

- 在終結視窗之前呼叫[OnFinalMessage](#onfinalmessage) 。

您可以覆寫 `WindowProc`，以提供不同的機制來處理訊息。

## <a name="see-also"></a>另請參閱

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
