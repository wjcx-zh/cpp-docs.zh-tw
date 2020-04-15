---
title: 包含視窗 T 類別
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
ms.openlocfilehash: cde9c73a195303e57758cb4f27184b5136bdaf14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327208"
---
# <a name="ccontainedwindowt-class"></a>包含視窗 T 類別

此類實現包含在另一個物件中的視窗。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>參數

*TBase*<br/>
新類的基類。 預設基數為`CWindow`。

*特溫·特威茨*<br/>
定義視窗樣式的特性類別。 預設值為 `CControlWinTraits`。

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)是`CContainedWindowT`中的一個專門化。 如果要變更基類別或特徵,請使用`CContainedWindowT`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 包含視窗:C 包含視窗T](#ccontainedwindowt)|建構函式。 初始化數據成員以指定將處理包含的視窗的消息的消息。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 包含視窗T:建立](#create)|建立視窗。|
|[C包含視窗T::DefWindowProc](#defwindowproc)|提供預設訊息處理。|
|[C 包含視窗T:抓取目前的訊息](#getcurrentmessage)|傳回目前訊息。|
|[CContained視窗::註冊Wnd超級類](#registerwndsuperclass)|註冊包含視窗的視窗類。|
|[C包含視窗T::子類視窗](#subclasswindow)|子類別化視窗。|
|[C 包含視窗T:切換訊息映射](#switchmessagemap)|更改用於處理包含的視窗的消息的消息映射。|
|[包含視窗::取消子類視窗](#unsubclasswindow)|還原先前子類別化的視窗。|
|[C包含視窗T::視窗Proc](#windowproc)|(靜態)處理發送到包含的視窗的消息。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C包含視窗::m_dwMsgMapID](#m_dwmsgmapid)|標識將處理包含的視窗的消息的消息。|
|[C包含視窗::m_lpszClassName](#m_lpszclassname)|指定新視窗類別將基於的現有視窗類別的名稱。|
|[C 包含視窗T:m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|
|[C包含視窗T:m_pObject](#m_pobject)|指向包含的物件。|

## <a name="remarks"></a>備註

`CContainedWindowT`實現包含在另一個物件中的視窗。 `CContainedWindowT`的視窗過程使用包含物件中的消息映射將消息定向到相應的處理程式。 構造物件時`CContainedWindowT`,應指定應使用的消息映射。

`CContainedWindowT`允許您通過對現有視窗類進行超類化來創建新視窗。 該方法`Create`首先註冊一個基於現有類但`CContainedWindowT::WindowProc`使用 的視窗類。 `Create`然後基於此新視窗類創建一個視窗。 的每個`CContainedWindowT`實例都可以對不同的視窗類進行類超類。

`CContainedWindowT` 也支援視窗子類別化。 `SubclassWindow` 方法會將現有視窗附加至 `CContainedWindowT` 物件，並將視窗程序變更至 `CContainedWindowT::WindowProc`。 每個 `CContainedWindowT` 執行個體都可以子類別化為不同的視窗。

> [!NOTE]
> 對於任何給定`CContainedWindowT`物件,呼叫`Create`任`SubclassWindow`一物件或 。 不應在同一對象上調用這兩種方法。

當您使用基於 ATL 專案精靈中選項**的添加控制項**時,嚮導將自動向實現該`CContainedWindowT`控制件的類添加資料成員。 下面的範例展示如何宣告包含的視窗:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|如需下列項目的詳細資訊|請參閱|
|--------------------------------|---------|
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|
|在 ATL 中使用視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/win32/winmsg/windows) SDK 中的 Windows 及其後續主題|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a>C 包含視窗:C 包含視窗T

建構函數初始化數據成員。

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

*lpszClass 名稱*<br/>
[在]包含的視窗將基於的現有視窗類的名稱。

*pObject*<br/>
[在]指向聲明消息映射的包含物件的指標。 此物件的類別必須派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[在]標識將處理包含的視窗的消息的消息映射。 預設值 0 指定用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)聲明的預設消息映射。 要使用使用[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的備用訊息`msgMapID`映射 ,請透過 。

### <a name="remarks"></a>備註

如果要透過[Create](#create)建立新視窗,則必須傳遞*lpszClassName*參數的現有視窗類的名稱。 例如,請參閱[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)概述。

有三個建構函數:

- 具有三個參數的構造函數是通常調用的構造函數。

- 具有兩個參數的構造函數使用`TBase::GetWndClassName`中的類名稱。

- 如果以後要提供參數,將使用沒有參數的構造函數。 以後調用`Create`時,必須提供視窗類名稱、消息映射物件和消息映射 ID。

如果透過[子類視窗](#subclasswindow)對現有視窗進行子類類,則不會使用 lpszClassName 值;如果透過子類視窗對現有視窗進行子類類別,則不使用*lpszClassName*值。因此,您可以為此參數傳遞 NULL。

## <a name="ccontainedwindowtcreate"></a><a name="create"></a>C 包含視窗T:建立

調用[RegisterWndSuper 類](#registerwndsuperclass)註冊基於現有類但使用[CContainedWindowT::windowProc](#windowproc)的視窗類。

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

*lpszClass 名稱*<br/>
[在]包含的視窗將基於的現有視窗類的名稱。

*pObject*<br/>
[在]指向聲明消息映射的包含物件的指標。 此物件的類別必須派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[在]標識將處理包含的視窗的消息的消息映射。 預設值 0 指定用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)聲明的預設消息映射。 要使用使用[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的備用訊息`msgMapID`映射 ,請透過 。

*hWnd 父母*<br/>
[在]父視窗或擁有者視窗的句柄。

*矩形*<br/>
[在]指定視窗位置的[RECT](/previous-versions/dd162897\(v=vs.85\))結構。 `RECT`可以通過指標或參考傳遞 。

*szWindow名稱*<br/>
[在]指定視窗的名稱。 預設值是 NULL。

*dwStyle*<br/>
[在]視窗的樣式。 默認值為&#124;WS_VISIBLEWS_CHILD。 有關可能值的清單,請參閱在 Windows SDK 中[建立視窗](/windows/win32/api/winuser/nf-winuser-createwindoww)。

*dwExStyle*<br/>
[在]擴展視窗樣式。 默認值為 0,表示沒有擴展樣式。 有關可能值的清單,請參閱在 Windows SDK 中[創建 WindowsEx。](/windows/win32/api/winuser/nf-winuser-createwindowexw)

*選單OrID*<br/>
[在]對於子視窗,窗口標識碼。 對於頂級視窗,視窗的功能表句柄。 預設值為**0U**。

*lpCreateParam*<br/>
[在]指向視窗創建資料的指標。 有關完整說明,請參閱[創建WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的最終參數的說明。

### <a name="return-value"></a>傳回值

如果成功,則對新創建的視窗的句柄;否則,NULL。

### <a name="remarks"></a>備註

現有視窗類名稱保存在[m_lpszClassName](#m_lpszclassname)中。 `Create`然後基於此新類創建一個視窗。 新創建的視窗將自動附加到`CContainedWindowT`物件。

> [!NOTE]
> 如果您已經呼叫`Create`[了子類別視窗](#subclasswindow),請不要呼叫 。

> [!NOTE]
> 如果 0 用作*MenuOrID*參數的值,則必須將其指定為 0U(預設值),以避免編譯器錯誤。

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a>C包含視窗T::DefWindowProc

由[WindowProc](#windowproc)調用以處理消息映射未處理的郵件。

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a>C 包含視窗T:抓取目前的訊息

傳回目前的訊息`m_pCurrentMsg`( 。

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>傳回值

目前訊息,打包在結構中`MSG`。

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a>C包含視窗::m_dwMsgMapID

保存當前用於包含視窗的消息映射的標識符。

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>備註

必須在包含對象中聲明此消息映射。

默認消息映射(使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)聲明)始終以零標識。 使用[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的替代訊息映`msgMapID`射由 識別 。

`m_dwMsgMapID`首先由構造函數初始化,可以通過調用[SwitchMessageMap](#switchmessagemap)進行更改。 例如,請參閱[CContainedWindowT 概述](../../atl/reference/ccontainedwindowt-class.md)。

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a>C包含視窗::m_lpszClassName

指定現有視窗類的名稱。

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>備註

創建視窗時[,Create](#create)會註冊基於此現有類但使用[CContainedWindowT::windowProc](#windowproc)的新視窗類。

`m_lpszClassName`由構造函數初始化。 例如,請參閱[C包含視窗T](../../atl/reference/ccontainedwindowt-class.md)概述。

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>C 包含視窗T:m_pfnSuperWindowProc

如果包含的視窗被子分類,`m_pfnSuperWindowProc`則指向視窗類的原始視窗過程。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>備註

如果包含的視窗是超類的,這意味著它基於修改現有類的視窗類,則`m_pfnSuperWindowProc`指向現有視窗類的視窗過程。

[DefWindowProc](#defwindowproc)方法將消息資訊發送到保存在`m_pfnSuperWindowProc`中的視窗過程。

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a>C包含視窗T:m_pObject

指向包含`CContainedWindowT`物件的物件。

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>備註

此容器的類別必須派生自[CMessageMap,](../../atl/reference/cmessagemap-class.md)聲明包含的視窗使用的消息對應。

`m_pObject`由構造函數初始化。 例如,請參閱[C包含視窗T](../../atl/reference/ccontainedwindowt-class.md)概述。

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a>CContained視窗::註冊Wnd超級類

通過[「創建」](#create)呼叫以註冊包含視窗的視窗類。

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>傳回值

如果成功,則唯一標識要註冊的視窗類的原子;否則,零。

### <a name="remarks"></a>備註

此視窗類別基於現有類,但使用[CContainedWindowT::windowProc](#windowproc)。 現有視窗類的名稱和視窗過程分別保存在[m_lpszClassName](#m_lpszclassname)和[m_pfnSuperWindowProc。](#m_pfnsuperwindowproc)

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a>C包含視窗T::子類視窗

對*hWnd*標識的視窗進行子類,並將其`CContainedWindowT`附加到 物件。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[在]正在子類視窗的句柄。

### <a name="return-value"></a>傳回值

如果視窗已成功下類,則為 TRUE;如果視窗已成功下分類。否則,FALSE。

### <a name="remarks"></a>備註

子類視窗現在使用[CContainedWindowT::windowProc](#windowproc)。 原始視窗過程保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)中。

> [!NOTE]
> 如果已呼叫`SubclassWindow` [Create,](#create)請不要呼叫 。

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a>C 包含視窗T:切換訊息映射

更改將用於處理包含的視窗的消息的消息。

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>參數

*dwMsgMapID*<br/>
[在]消息映射標識碼。 要使用用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)聲明的預設消息映射,則傳遞零。 要使用使用[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的備用訊息`msgMapID`映射 ,請透過 。

### <a name="remarks"></a>備註

必須在包含物件中定義消息映射。

最初在建構函數中指定消息映射標識碼。

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a>包含視窗::取消子類視窗

從`CContainedWindowT`物件分離子分類視窗,並還原保存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)的原始視窗過程。

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>參數

*bForce*<br/>
[在]設置為 TRUE 以強制還原原始視窗過程,`CContainedWindowT`即使此 物件的視窗過程當前未處於活動狀態也是如此。 如果*bForce*設置為 FALSE,並且此`CContainedWindowT`物件的視窗過程當前未處於活動狀態,則原始視窗過程將不會還原。

### <a name="return-value"></a>傳回值

以前子類視窗的句柄。 如果*bForce*設定為 FALSE 並且此`CContainedWindowT`物件的視窗過程當前未處於活動狀態,則傳回 NULL。

### <a name="remarks"></a>備註

僅當要在銷毀視窗之前還原原始視窗過程時,才使用此方法。 否則[,WindowProc](#windowproc)將在視窗被銷毀時自動執行此操作。

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a>C包含視窗T::視窗Proc

此靜態方法實現視窗過程。

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

`WindowProc`將消息定向到[m_dwMsgMapID](#m_dwmsgmapid)標識的消息映射。 如有必要,`WindowProc`請呼叫[DefWindowProc](#defwindowproc)進行其他訊息處理。

## <a name="see-also"></a>另請參閱

[CWindow 類別](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap 類別](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[類別概觀](../../atl/atl-class-overview.md)
