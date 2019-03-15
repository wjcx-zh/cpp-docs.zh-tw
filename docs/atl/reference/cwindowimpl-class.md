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
ms.openlocfilehash: f835f2869af20a1cb22595837c317eb165ef5fe9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820347"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 類別

提供建立或子類別化視窗的方法。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的新類別，衍生自 `CWindowImpl`。

*TBase*<br/>
您類別的基底類別。 根據預設，基底類別是[CWindow](../../atl/reference/cwindow-class.md)。

*TWinTraits*<br/>
A [traits 類別](../../atl/understanding-window-traits.md)定義視窗樣式。 預設為 `CControlWinTraits`。

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
|[OnFinalMessage](#onfinalmessage)|呼叫之後收到的最後一個訊息 （通常是控制）。|
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

您可以使用`CWindowImpl`建立視窗或子類別化現有視窗。 `CWindowImpl`視窗程序會使用訊息對應將導向至適當的處理常式的訊息。

`CWindowImpl::Create` 建立視窗由管理的視窗類別資訊為基礎[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)。 `CWindowImpl` 包含[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class)巨集，這表示`CWndClassInfo`註冊新的視窗類別。 如果您想要在現有視窗類別，衍生您的類別，從`CWindowImpl`，並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集。 在這種情況下，`CWndClassInfo` 會依據現有的類別註冊視窗類別，但是會使用 `CWindowImpl::WindowProc`。 例如: 

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  由於 `CWndClassInfo` 只會管理一個視窗類別的資訊，因此每個透過 `CWindowImpl` 執行個體所建立的視窗都是以相同的視窗類別為基礎。

`CWindowImpl` 也支援視窗子類別化。 
  `SubclassWindow` 方法會將現有視窗附加至 `CWindowImpl` 物件，並將視窗程序變更至 `CWindowImpl::WindowProc`。 每個 `CWindowImpl` 執行個體都可以子類別化為不同的視窗。

> [!NOTE]
>  針對任何給定`CWindowImpl`物件，呼叫`Create`或`SubclassWindow`。 不要對同一物件叫用兩種方法。

除了`CWindowImpl`，提供 ATL [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)建立的視窗會包含在另一個物件。

基底類別解構函式 (~ `CWindowImplRoot`) 可確保視窗會消失，終結物件之前。

`CWindowImpl` 衍生自`CWindowImplBaseT`，其衍生自`CWindowImplRoot`，其衍生自`TBase`並[CMessageMap](../../atl/reference/cmessagemap-class.md)。

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

*hWndParent*<br/>
[in]父系或擁有者的視窗控制代碼。

*rect*<br/>
[in]A [RECT](/previous-versions/dd162897\(v=vs.85\))結構，指定視窗的位置。 `RECT`可以傳遞指標或參考。

*szWindowName*<br/>
[in]指定視窗的名稱。 預設值是 NULL。

*dwStyle*<br/>
[in]視窗的樣式。 這個值會結合 traits 類別所提供之視窗的樣式。 預設值可讓類別完全控制樣式特性。 如需可能值的清單，請參閱 < [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) Windows SDK 中。

*dwExStyle*<br/>
[in]延伸的視窗樣式。 這個值會結合 traits 類別所提供之視窗的樣式。 預設值可讓類別完全控制樣式特性。 如需可能值的清單，請參閱 < [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*MenuOrID*<br/>
[in]子視窗的視窗識別項。 最上層視窗中，視窗的功能表控制代碼。 預設值是**0U**。

*lpCreateParam*<br/>
[in]視窗建立資料指標。 如需完整說明，請參閱的最後一個參數的描述[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)。

### <a name="return-value"></a>傳回值

如果成功，新建立的視窗控制代碼。 否則為 NULL。

### <a name="remarks"></a>備註

`Create` 如果尚未註冊，請先註冊視窗類別。 新建立的視窗會自動附加至`CWindowImpl`物件。

> [!NOTE]
>  請勿呼叫`Create`如果您已呼叫[SubclassWindow](#subclasswindow)。

若要使用現有的視窗類別為基礎的視窗類別，衍生您的類別，從`CWindowImpl`，並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集。 現有視窗類別的視窗程序會儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。 如需詳細資訊，請參閱 < [CWindowImpl](../../atl/reference/cwindowimpl-class.md)概觀。

> [!NOTE]
>  如果使用 0 做為值*MenuOrID*參數，它必須指定為 0U （預設值） 以避免編譯器錯誤。

##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc

由呼叫[WindowProc](#windowproc)來處理訊息的未處理的訊息對應。

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>參數

*uMsg*<br/>
[in]傳送至視窗的訊息。

*wParam*<br/>
[in]其他特定訊息資訊。

*lParam*<br/>
[in]其他特定訊息資訊。

### <a name="return-value"></a>傳回值

訊息處理的結果。

### <a name="remarks"></a>備註

根據預設，`DefWindowProc`呼叫[CallWindowProc](/windows/desktop/api/winuser/nf-winuser-callwindowproca)要傳送的訊息資訊中指定的視窗程序的 Win32 函式[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。

不含任何參數的函式會自動擷取所需的參數，從目前的訊息。

##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage

傳回目前的訊息，並封裝在`MSG`結構。

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

根據預設，`CWindowImpl`取得透過這個方法[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class)巨集，指定新的視窗類別。

要在現有視窗類別，衍生您的類別，從`CWindowImpl`，並包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集來覆寫`GetWndClassInfo`。 如需詳細資訊，請參閱 < [CWindowImpl](../../atl/reference/cwindowimpl-class.md)概觀。

除了使用 {2&gt;declare_wnd_class&lt;2 和 DECLARE_WND_SUPERCLASS 巨集，您可以覆寫`GetWndClassInfo`與您自己的實作。

##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc

根據視窗中，指向其中一個下列的視窗程序。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>備註

|視窗類型|視窗程序|
|--------------------|----------------------|
|根據新的視窗類別，透過指定的視窗[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class)巨集。|[DefWindowProc](/windows/desktop/api/winuser/nf-winuser-defwindowproca) Win32 函式。|
|修改現有的類別，透過指定的視窗類別為基礎的視窗[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集。|現有視窗類別的視窗程序。|
|子類別化的視窗。|子類別化之的視窗的原始視窗程序。|

[CWindowImpl::DefWindowProc](#defwindowproc)傳送訊息至儲存在視窗程序的資訊`m_pfnSuperWindowProc`。

##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage

呼叫之後收到最後一則訊息 （通常是控制）。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[in]終結視窗控制代碼。

### <a name="remarks"></a>備註

預設實作`OnFinalMessage`不執行任何動作，但您可以覆寫這個函式來處理清除，然後再終結視窗。 如果您想要自動刪除您的物件，在視窗解構時，您可以呼叫**刪除此;** 中此函式。

##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow

視窗所識別的子類別*hWnd*並將它附加至`CWindowImpl`物件。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[in]在子類別化視窗的控制代碼。

### <a name="return-value"></a>傳回值

如果成功子類別化視窗;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

子類別化的視窗現在會使用[CWindowImpl::WindowProc](#windowproc)。 原始的視窗程序會儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。

> [!NOTE]
>  請勿呼叫`SubclassWindow`如果您已呼叫[建立](#create)。

##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow

中斷連結子類別化的視窗`CWindowImpl`物件，並會還原原始的視窗程序，儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>傳回值

先前子類別化視窗的控制代碼。

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

*hWnd*<br/>
[in]視窗控制代碼。

*uMsg*<br/>
[in]傳送至視窗的訊息。

*wParam*<br/>
[in]其他特定訊息資訊。

*lParam*<br/>
[in]其他特定訊息資訊。

### <a name="return-value"></a>傳回值

訊息處理的結果。

### <a name="remarks"></a>備註

`WindowProc` 使用預設的訊息對應 (以宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) 將導向至適當的處理常式的訊息。 如果有必要，請`WindowProc`呼叫[DefWindowProc](#defwindowproc)進行額外的訊息處理。 如果未處理的最後一個訊息，`WindowProc`會進行下列作業：

- 執行 unsubclassing unsubclassed 視窗時。

- 清除 `m_hWnd`。

- 呼叫[OnFinalMessage](#onfinalmessage)終結視窗之前。

您可以覆寫`WindowProc`提供不同的機制，來處理訊息。

## <a name="see-also"></a>另請參閱

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
