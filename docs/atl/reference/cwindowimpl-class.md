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
ms.openlocfilehash: 56b503dfcfbe4fae215f61081446bd3a5070af3c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835528"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 類別

提供建立或子類別化視窗的方法。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的新類別，衍生自 `CWindowImpl`。

*TBase*<br/>
您類別的基底類別。 根據預設，基類是 [CWindow](../../atl/reference/cwindow-class.md)。

*TWinTraits*<br/>
定義視窗樣式的 [特性類別](../../atl/understanding-window-traits.md) 。 預設為 `CControlWinTraits`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWindowImpl：： Create](#create)|建立視窗。|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT 方法

|名稱|描述|
|-|-|
|[DefWindowProc](#defwindowproc)|提供預設訊息處理。|
|[GetCurrentMessage](#getcurrentmessage)|傳回目前訊息。|
|[GetWindowProc](#getwindowproc)|傳回目前的視窗程序。|
|[OnFinalMessage](#onfinalmessage)|在收到最後一個訊息之後呼叫 (通常 WM_NCDESTROY) 。|
|[SubclassWindow](#subclasswindow)|子類別化視窗。|
|[UnsubclassWindow](#unsubclasswindow)|還原先前子類別化的視窗。|

### <a name="static-methods"></a>靜態方法

|名稱|描述|
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|傳回 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的靜態實例，此實例會管理視窗類別資訊。|
|[WindowProc](#windowproc)|處理傳送至視窗的訊息。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|

## <a name="remarks"></a>備註

您可以使用 `CWindowImpl` 建立現有視窗的視窗或子類別。 視窗程式會 `CWindowImpl` 使用訊息對應，將訊息導向至適當的處理常式。

`CWindowImpl::Create` 根據 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)所管理的視窗類別資訊來建立視窗。 `CWindowImpl` 包含 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) 宏，這表示會 `CWndClassInfo` 註冊新的視窗類別。 如果您想要將現有的視窗類別設為超類，請從衍生類別， `CWindowImpl` 並包含 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 宏。 在這種情況下，`CWndClassInfo` 會依據現有的類別註冊視窗類別，但是會使用 `CWindowImpl::WindowProc`。 例如：

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> 由於 `CWndClassInfo` 只會管理一個視窗類別的資訊，因此每個透過 `CWindowImpl` 執行個體所建立的視窗都是以相同的視窗類別為基礎。

`CWindowImpl` 也支援視窗子類別化。 `SubclassWindow` 方法會將現有視窗附加至 `CWindowImpl` 物件，並將視窗程序變更至 `CWindowImpl::WindowProc`。 每個 `CWindowImpl` 執行個體都可以子類別化為不同的視窗。

> [!NOTE]
> 針對任何指定的 `CWindowImpl` 物件，呼叫 `Create` 或 `SubclassWindow` 。 不要對同一物件叫用兩種方法。

除了之外 `CWindowImpl` ，ATL 還提供 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 來建立包含在另一個物件中的視窗。

基類的函式 (~ `CWindowImplRoot`) 可確保視窗會在終結物件之前消失。

`CWindowImpl` 衍生自（衍生自 `CWindowImplBaseT` `CWindowImplRoot` `TBase` 和 [CMessageMap](../../atl/reference/cmessagemap-class.md)）。

|如需下列項目的詳細資訊|請參閱|
|--------------------------------|---------|
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|
|在 ATL 中使用視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="cwindowimplcreate"></a><a name="create"></a> CWindowImpl：： Create

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
在父系或擁有者視窗的控制碼。

*矩形*<br/>
在 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構，指定視窗的位置。 `RECT`可以透過指標或傳址方式來傳遞。

*szWindowName*<br/>
在指定視窗的名稱。 預設值是 NULL。

*dwStyle*<br/>
在視窗的樣式。 這個值會與視窗的特性類別所提供的樣式結合。 預設值可讓特性類別完全控制樣式。 如需可能值的清單，請參閱 Windows SDK 中的 [ [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) ]。

*dwExStyle*<br/>
在延伸的視窗樣式。 這個值會與視窗的特性類別所提供的樣式結合。 預設值可讓特性類別完全控制樣式。 如需可能值的清單，請參閱 Windows SDK 中的 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 。

*MenuOrID*<br/>
在子視窗的視窗識別碼。 適用于最上層視窗，也就是視窗的功能表控點。 預設值為 **0u**。

*lpCreateParam*<br/>
在視窗建立資料的指標。 如需完整描述，請參閱最後一個參數的描述 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)。

### <a name="return-value"></a>傳回值

如果成功，則為新建立之視窗的控制碼。 否則為 NULL。

### <a name="remarks"></a>備註

`Create` 如果尚未註冊，請先註冊視窗類別。 新建立的視窗會自動附加到 `CWindowImpl` 物件。

> [!NOTE]
> `Create`如果您已呼叫[SubclassWindow](#subclasswindow)，請勿呼叫。

若要使用以現有視窗類別為基礎的視窗類別，請從衍生您的類別， `CWindowImpl` 並包含 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 宏。 現有視窗類別的視窗程式會儲存在 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。 如需詳細資訊，請參閱 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 總覽。

> [!NOTE]
> 如果使用0作為 *MenuOrID* 參數的值，則必須將其指定為 0u (預設值) ，以避免編譯器錯誤。

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a> CWindowImpl：:D efWindowProc

由 [WindowProc](#windowproc) 呼叫以處理訊息對應未處理的訊息。

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

依預設，會 `DefWindowProc` 呼叫 [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 函式，將訊息資訊傳送至 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中指定的視窗程式。

沒有參數的函式會自動從目前的訊息抓取所需的參數。

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a> CWindowImpl：： GetCurrentMessage

傳回封裝在結構中的目前訊息 `MSG` 。

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>傳回值

目前的訊息。

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a> CWindowImpl：： GetWindowProc

傳回 `WindowProc` 目前的視窗程式。

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>傳回值

目前的視窗程式。

### <a name="remarks"></a>備註

覆寫這個方法，將視窗程式取代為您自己的程式。

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a> CWindowImpl：： GetWndClassInfo

由 [Create](#create) 呼叫以存取視窗類別資訊。

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>傳回值

[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的靜態實例。

### <a name="remarks"></a>備註

根據預設，會 `CWindowImpl` 透過 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) 宏取得這個方法，以指定新的視窗類別。

若要將現有的視窗類別設為超類，請從衍生類別， `CWindowImpl` 並包含要覆寫的 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 宏 `GetWndClassInfo` 。 如需詳細資訊，請參閱 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 總覽。

除了使用 DECLARE_WND_CLASS 和 DECLARE_WND_SUPERCLASS 宏之外，您還可以 `GetWndClassInfo` 使用自己的實作為來覆寫。

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a> CWindowImpl：： m_pfnSuperWindowProc

根據視窗，指向下列其中一個視窗程式。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>備註

|視窗類型|視窗程式|
|--------------------|----------------------|
|以新視窗類別為基礎的視窗，透過 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) 宏指定。|[DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32 函數。|
|以視窗類別為基礎的視窗，可修改透過 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 宏指定的現有類別。|現有視窗類別的視窗程式。|
|子類別化視窗。|子類別化視窗的原始視窗程式。|

[CWindowImpl：:D efwindowproc](#defwindowproc) 會將訊息資訊傳送至中儲存的視窗程式 `m_pfnSuperWindowProc` 。

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a> CWindowImpl：： OnFinalMessage

在收到最後一個訊息之後呼叫 (通常是 WM_NCDESTROY) 。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在要終結的視窗控制碼。

### <a name="remarks"></a>備註

的預設執行 `OnFinalMessage` 不會執行任何動作，但是您可以覆寫這個函式來處理清除，然後再終結視窗。 如果您想要在視窗損毀時自動刪除您的物件，您可以在此函數中呼叫 **delete** 。

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a> CWindowImpl：： SubclassWindow

子類別： *hWnd* 所識別的視窗，並將其附加至 `CWindowImpl` 物件。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在要子類別化之視窗的控制碼。

### <a name="return-value"></a>傳回值

如果成功將視窗子類別化，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

子類別化視窗現在會使用 [CWindowImpl：： WindowProc](#windowproc)。 原始的視窗程式會儲存在 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
> `SubclassWindow`如果您已呼叫[Create](#create)，請勿呼叫。

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a> CWindowImpl：： UnsubclassWindow

從物件卸離子類別化視窗， `CWindowImpl` 然後還原原始視窗程式，儲存在 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>傳回值

先前子類別的視窗控制碼。

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a> CWindowImpl：： WindowProc

此靜態函式會執行視窗程式。

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

`WindowProc` 使用 ([BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) 宣告的預設訊息對應，將訊息導向適當的處理常式。 如有必要，會 `WindowProc` 呼叫 [DefWindowProc](#defwindowproc) 來進行額外的訊息處理。 如果未處理最後的訊息，則 `WindowProc` 會執行下列動作：

- 如果視窗已 unsubclassed，則執行 unsubclassing。

- 清除 `m_hWnd`。

- 在終結視窗之前呼叫 [OnFinalMessage](#onfinalmessage) 。

您可以覆寫 `WindowProc` 以提供不同的機制來處理訊息。

## <a name="see-also"></a>另請參閱

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
