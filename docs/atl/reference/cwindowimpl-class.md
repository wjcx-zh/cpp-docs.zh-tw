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
ms.openlocfilehash: d7f7f7363eb123181bd6e0389663810346094cba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330300"
---
# <a name="cwindowimpl-class"></a>CWindowImpl 類別

提供建立或子類別化視窗的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的新類別，衍生自 `CWindowImpl`。

*TBase*<br/>
您類別的基底類別。 預設情況下,基類是[CWindow](../../atl/reference/cwindow-class.md)。

*特溫·特威茨*<br/>
定義視窗樣式的[特徵類別](../../atl/understanding-window-traits.md)。 預設值為 `CControlWinTraits`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWindowImpl::建立](#create)|建立視窗。|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT 方法

|||
|-|-|
|[DefWindowProc](#defwindowproc)|提供預設訊息處理。|
|[GetCurrentMessage](#getcurrentmessage)|傳回目前訊息。|
|[GetWindowProc](#getwindowproc)|傳回目前的視窗程序。|
|[OnFinalMessage](#onfinalmessage)|收到最後一條消息后調用(通常WM_NCDESTROY)。|
|[SubclassWindow](#subclasswindow)|子類別化視窗。|
|[UnsubclassWindow](#unsubclasswindow)|還原先前子類別化的視窗。|

### <a name="static-methods"></a>靜態方法

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|返回[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的靜態實例,該實例管理視窗類資訊。|
|[WindowProc](#windowproc)|處理傳送至視窗的訊息。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|

## <a name="remarks"></a>備註

可以使用`CWindowImpl`創建現有視窗的視窗或子類。 `CWindowImpl`視窗過程使用消息映射將消息定向到相應的處理程式。

`CWindowImpl::Create`基於[由 CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)管理的視窗類資訊創建一個視窗。 `CWindowImpl`包含[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏`CWndClassInfo`,這意味著 註冊一個新的視窗類。 如果要超類現有視窗類,請從`CWindowImpl`DECLARE_WND_SUPERCLASS宏派生類並包含該[宏](window-class-macros.md#declare_wnd_superclass)。 在這種情況下，`CWndClassInfo` 會依據現有的類別註冊視窗類別，但是會使用 `CWindowImpl::WindowProc`。 例如：

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> 由於 `CWndClassInfo` 只會管理一個視窗類別的資訊，因此每個透過 `CWindowImpl` 執行個體所建立的視窗都是以相同的視窗類別為基礎。

`CWindowImpl` 也支援視窗子類別化。 `SubclassWindow` 方法會將現有視窗附加至 `CWindowImpl` 物件，並將視窗程序變更至 `CWindowImpl::WindowProc`。 每個 `CWindowImpl` 執行個體都可以子類別化為不同的視窗。

> [!NOTE]
> 對於任何給定`CWindowImpl`物件,呼叫`Create`任`SubclassWindow`一物件或 。 不要對同一物件叫用兩種方法。

除之外`CWindowImpl`,ATL 還提供[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)來創建包含在另一個物件中的視窗。

基質析構函數`CWindowImplRoot`(* ) 可確保視窗在物件銷毀之前消失。

`CWindowImpl`衍生自`CWindowImplBaseT`派生自`CWindowImplRoot``TBase`[和](../../atl/reference/cmessagemap-class.md)的 。

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

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="cwindowimplcreate"></a><a name="create"></a>CWindowImpl::建立

基於新視窗類創建視窗。

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

*hWnd 父母*<br/>
[在]父視窗或擁有者視窗的句柄。

*矩形*<br/>
[在]指定視窗位置的[RECT](/previous-versions/dd162897\(v=vs.85\))結構。 `RECT`可以通過指標或參考傳遞 。

*szWindow名稱*<br/>
[在]指定視窗的名稱。 預設值是 NULL。

*dwStyle*<br/>
[在]視窗的樣式。 此值與視窗的特徵類提供的樣式結合使用。 默認值使特徵類對樣式完全控制。 有關可能值的清單,請參閱在 Windows SDK 中[建立視窗](/windows/win32/api/winuser/nf-winuser-createwindoww)。

*dwExStyle*<br/>
[在]擴展視窗樣式。 此值與視窗的特徵類提供的樣式結合使用。 默認值使特徵類對樣式完全控制。 有關可能值的清單,請參閱在 Windows SDK 中[創建 WindowsEx。](/windows/win32/api/winuser/nf-winuser-createwindowexw)

*選單OrID*<br/>
[在]對於子視窗,窗口標識碼。 對於頂級視窗,視窗的功能表句柄。 預設值為**0U**。

*lpCreateParam*<br/>
[在]指向視窗創建資料的指標。 有關完整說明,請參閱[創建WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的最終參數的說明。

### <a name="return-value"></a>傳回值

如果成功,則對新創建的視窗的句柄。 否則為 NULL。

### <a name="remarks"></a>備註

`Create`如果視窗類尚未註冊,則首先註冊該視窗類。 新創建的視窗將自動附加到`CWindowImpl`物件。

> [!NOTE]
> 如果您已經呼叫`Create`[了子類別視窗](#subclasswindow),請不要呼叫 。

要使用基於現有視窗類的視窗類,請從`CWindowImpl`DECLARE_WND_SUPERCLASS宏派生類並包含該[宏](window-class-macros.md#declare_wnd_superclass)。 現有視窗類的視窗過程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。 有關詳細資訊,請參閱[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。

> [!NOTE]
> 如果 0 用作*MenuOrID*參數的值,則必須將其指定為 0U(預設值),以避免編譯器錯誤。

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a>CWindowImpl::DefWindowProc

由[WindowProc](#windowproc)調用以處理消息映射未處理的郵件。

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>參數

*烏姆斯格*<br/>
[在]發送到視窗的消息。

*wParam*<br/>
[在]其他特定於消息的資訊。

*lParam*<br/>
[在]其他特定於消息的資訊。

### <a name="return-value"></a>傳回值

消息處理的結果。

### <a name="remarks"></a>備註

預設情況下,`DefWindowProc`呼叫[CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 函數將消息資訊發送到[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中指定的視窗過程。

沒有參數的函數會自動從當前消息中檢索所需的參數。

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a>CWindowimpl::取得目前訊息

返回當前消息,該消息打包在`MSG`結構中。

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>傳回值

目前的訊息。

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a>CWindowImpl::取得視窗Proc

返回`WindowProc`,當前視窗過程。

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>傳回值

當前視窗過程。

### <a name="remarks"></a>備註

重寫此方法以將視窗過程取代為您自己的視窗過程。

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a>CWindowImpl::獲取WndClassinfo

由[Create](#create)調用以訪問視窗類資訊。

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>傳回值

[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)的靜態實例。

### <a name="remarks"></a>備註

預設情況下,`CWindowImpl`通過[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏獲取此方法,該宏指定了一個新的視窗類。

要超類現有視窗類,請從`CWindowImpl`派生類,並包括[要](window-class-macros.md#declare_wnd_superclass)重`GetWndClassInfo`寫的DECLARE_WND_SUPERCLASS宏。 有關詳細資訊,請參閱[CWindowImpl](../../atl/reference/cwindowimpl-class.md)概述。

除了使用DECLARE_WND_CLASS和DECLARE_WND_SUPERCLASS宏外,您還可以使用自己的實現進行`GetWndClassInfo`重寫。

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc

根據視窗的不同,指向以下視窗過程之一。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>備註

|視窗類型|視窗程序|
|--------------------|----------------------|
|基於新視窗類的視窗,通過[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)宏指定。|[DefWindow Proc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32 功能。|
|基於修改現有類的視窗類的視窗,該窗口通過[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏指定。|現有視窗類的視窗過程。|
|子類視窗。|子類視窗的原始視窗過程。|

[CWindowImpl::DefWindowProc](#defwindowproc)將消息資訊發送到保存在`m_pfnSuperWindowProc`中的視窗過程。

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a>CWindowimpl::開啟最終訊息

收到最後一條消息后調用(通常WM_NCDESTROY)。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[在]正在銷毀的視窗的句柄。

### <a name="remarks"></a>備註

的`OnFinalMessage`預設實現不執行任何操作,但您可以重寫此函數,以在銷毀視窗之前處理清理。 如果要在視窗破壞時自動刪除物件,可以呼叫 **「刪除此」;** 在此函數中。

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a>CWindowImpl::子類視窗

對*hWnd*標識的視窗進行子類,並將其`CWindowImpl`附加到 物件。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[在]正在子類視窗的句柄。

### <a name="return-value"></a>傳回值

如果視窗已成功下類,則為 TRUE;如果視窗已成功下分類。否則,FALSE。

### <a name="remarks"></a>備註

子類視窗現在使用[CWindowImpl::windowProc](#windowproc)。 原始視窗過程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
> 如果已呼叫`SubclassWindow` [Create,](#create)請不要呼叫 。

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a>CWindowImpl::取消子類視窗

從`CWindowImpl`物件分離子分類視窗,並還原保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)的原始視窗過程。

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>傳回值

以前子類視窗的句柄。

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a>視窗Impl::視窗Proc

此靜態函數實現視窗過程。

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[在]視窗的句柄。

*烏姆斯格*<br/>
[在]發送到視窗的消息。

*wParam*<br/>
[在]其他特定於消息的資訊。

*lParam*<br/>
[在]其他特定於消息的資訊。

### <a name="return-value"></a>傳回值

消息處理的結果。

### <a name="remarks"></a>備註

`WindowProc`使用預設消息映射(使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) 將消息定向到相應的處理程式。 如有必要,`WindowProc`請呼叫[DefWindowProc](#defwindowproc)進行其他訊息處理。 如果未處理最後一條訊息,`WindowProc`則執行以下操作:

- 如果視窗未下類,則執行取消子類。

- 清除 `m_hWnd`。

- 在窗口銷毀之前調用[「最終消息](#onfinalmessage)」。

您可以重寫`WindowProc`以提供用於處理消息的不同機制。

## <a name="see-also"></a>另請參閱

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
