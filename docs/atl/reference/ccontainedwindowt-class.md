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
ms.openlocfilehash: 7fd9a941210407edc3424454b3375040717a05a2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261657"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT 類別

這個類別會實作包含在另一個物件的視窗。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>參數

*TBase*<br/>
您的新類別的基底類別。 預設的基底類別是`CWindow`。

*TWinTraits*<br/>
定義視窗樣式的 traits 類別。 預設為 `CControlWinTraits`。

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md)是的特製化`CContainedWindowT`。 如果您想要變更的基底類別或特性，使用`CContainedWindowT`直接。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|建構函式。 資料成員初始化為指定的訊息對應將會處理包含的視窗的訊息。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|建立視窗。|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|提供預設訊息處理。|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|傳回目前訊息。|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|註冊包含視窗的視窗類別。|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|子類別化視窗。|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|變更的訊息對應用來處理包含的視窗的訊息。|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|還原先前子類別化的視窗。|
|[CContainedWindowT::WindowProc](#windowproc)|（靜態）處理傳送至自主的視窗訊息。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|識別哪些訊息對應將會處理包含的視窗的訊息。|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|指定新的視窗類別為基礎的現有視窗類別名稱。|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|指向視窗類別的原始視窗程序。|
|[CContainedWindowT::m_pObject](#m_pobject)|指向包含的物件。|

## <a name="remarks"></a>備註

`CContainedWindowT` 實作包含在另一個物件的視窗。 `CContainedWindowT`視窗程序會使用訊息對應中包含的物件，以直接將訊息至適當的處理常式。 在建構時`CContainedWindowT`物件時，您指定應該使用哪一個訊息對應。

`CContainedWindowT` 可讓您建立新的視窗由 superclassing 現有視窗類別。 `Create`方法會先註冊視窗類別以現有的類別為基礎，但使用`CContainedWindowT::WindowProc`。 `Create` 接著會建立這個新的視窗類別為基礎的視窗。 每個執行個體`CContainedWindowT`可以超級類別不同的視窗類別。

`CContainedWindowT` 也支援視窗子類別化。 
  `SubclassWindow` 方法會將現有視窗附加至 `CContainedWindowT` 物件，並將視窗程序變更至 `CContainedWindowT::WindowProc`。 每個 `CContainedWindowT` 執行個體都可以子類別化為不同的視窗。

> [!NOTE]
>  針對任何給定`CContainedWindowT`物件，呼叫`Create`或`SubclassWindow`。 您不應該叫用的相同物件上的這兩種方法。

當您使用**新增控制項依據**選項在 ATL 專案精靈 中，精靈會自動將`CContainedWindowT`實作控制項的類別資料成員。 下列範例會示範如何宣告，包含的視窗：

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|如需詳細資訊|請參閱|
|--------------------------------|---------|
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|
|在 ATL 中使用視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/desktop/winmsg/windows)和後續 Windows SDK 中的主題|

## <a name="inheritance-hierarchy"></a>繼承階層

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="ccontainedwindowt"></a>  CContainedWindowT::CContainedWindowT

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

*lpszClassName*<br/>
[in]包含的視窗為基礎的現有視窗類別名稱。

*pObject*<br/>
[in]宣告訊息對應包含物件的指標。 這個物件的類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[in]識別會被收納的視窗訊息處理的訊息對應。 預設值為 0，指定預設的訊息對應宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 若要使用替代的訊息對應，以宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，傳遞`msgMapID`。

### <a name="remarks"></a>備註

如果您想要建立新的視窗，透過[Create](#create)，您必須將現有視窗類別的名稱傳遞給*lpszClassName*參數。 如需範例，請參閱[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)概觀。

有三個建構函式：

- 使用三個引數的建構函式是通常會呼叫。

- 兩個引數的建構函式會使用類別名稱，從`TBase::GetWndClassName`。

- 如果您想要稍後提供的引數，則會使用不含引數的建構函式。 您稍後呼叫時必須提供的視窗類別名稱、 訊息對應物件和訊息對應識別碼`Create`。

如果您子類別化現有視窗透過[SubclassWindow](#subclasswindow)，則*lpszClassName*將不會使用值; 因此，您可以傳遞 NULL，這個參數。

##  <a name="create"></a>  CContainedWindowT::Create

呼叫[RegisterWndSuperclass](#registerwndsuperclass)註冊視窗類別，以現有的類別為基礎，但會使用[CContainedWindowT::WindowProc](#windowproc)。

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
[in]包含的視窗為基礎的現有視窗類別名稱。

*pObject*<br/>
[in]宣告訊息對應包含物件的指標。 這個物件的類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[in]識別會被收納的視窗訊息處理的訊息對應。 預設值為 0，指定預設的訊息對應宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 若要使用替代的訊息對應，以宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，傳遞`msgMapID`。

*hWndParent*<br/>
[in]父系或擁有者的視窗控制代碼。

*rect*<br/>
[in]A [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定視窗的位置。 `RECT`可以傳遞指標或參考。

*szWindowName*<br/>
[in]指定視窗的名稱。 預設值是 NULL。

*dwStyle*<br/>
[in]視窗的樣式。 預設值是 WS_CHILD &#124; WS_VISIBLE。 如需可能值的清單，請參閱 < [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) Windows SDK 中。

*dwExStyle*<br/>
[in]延伸的視窗樣式。 預設值為 0，這表示沒有延伸的樣式。 如需可能值的清單，請參閱 < [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*MenuOrID*<br/>
[in]子視窗的視窗識別項。 最上層視窗中，視窗的功能表控制代碼。 預設值是**0U**。

*lpCreateParam*<br/>
[in]視窗建立資料指標。 如需完整說明，請參閱的最後一個參數的描述[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)。

### <a name="return-value"></a>傳回值

如果成功，新建立的視窗; 的控制代碼否則為 NULL。

### <a name="remarks"></a>備註

現有的視窗類別名稱會儲存在[m_lpszClassName](#m_lpszclassname)。 `Create` 接著會建立這個新的類別為基礎的視窗。 新建立的視窗會自動附加至`CContainedWindowT`物件。

> [!NOTE]
>  請勿呼叫`Create`如果您已呼叫[SubclassWindow](#subclasswindow)。

> [!NOTE]
>  如果使用 0 做為值*MenuOrID*參數，它必須指定為 0U （預設值） 以避免編譯器錯誤。

##  <a name="defwindowproc"></a>  CContainedWindowT::DefWindowProc

由呼叫[WindowProc](#windowproc)來處理訊息的未處理的訊息對應。

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage

傳回目前的訊息 (`m_pCurrentMsg`)。

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>傳回值

目前的訊息，並封裝在`MSG`結構。

##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID

保留目前正用於包含視窗的訊息對應的識別碼。

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>備註

此訊息的對應必須宣告中包含的物件。

預設訊息對應中，以宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，一定會識別為零。 替代訊息對應，以宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，由`msgMapID`。

`m_dwMsgMapID` 第一次由建構函式進行初始化，而且可以變更藉由呼叫[SwitchMessageMap](#switchmessagemap)。 如需範例，請參閱[CContainedWindowT 概觀](../../atl/reference/ccontainedwindowt-class.md)。

##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName

指定現有視窗類別名稱。

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>備註

當您建立的視窗中， [Create](#create)註冊這個現有的類別為基礎，但使用新的視窗類別[CContainedWindowT::WindowProc](#windowproc)。

`m_lpszClassName` 初始化建構函式。 如需範例，請參閱[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概觀。

##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc

如果包含的視窗子類別化，`m_pfnSuperWindowProc`指向視窗類別的原始視窗程序。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>備註

如果包含的視窗是超級類別，亦即它會根據視窗類別，以修改現有的類別，`m_pfnSuperWindowProc`指向現有視窗類別的視窗程序。

[DefWindowProc](#defwindowproc)方法會將訊息資訊傳送至儲存在視窗程序`m_pfnSuperWindowProc`。

##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject

指向物件，包含`CContainedWindowT`物件。

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>備註

此容器，其類別必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)，宣告包含視窗所使用的訊息對應。

`m_pObject` 初始化建構函式。 如需範例，請參閱[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)概觀。

##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass

由呼叫[建立](#create)註冊包含視窗的視窗類別。

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>傳回值

如果成功，atom 可唯一識別視窗類別註冊;否則為零。

### <a name="remarks"></a>備註

此視窗類別以現有的類別為基礎，但會使用[CContainedWindowT::WindowProc](#windowproc)。 現有的視窗類別名稱和視窗程序就會存入[m_lpszClassName](#m_lpszclassname)並[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)分別。

##  <a name="subclasswindow"></a>  CContainedWindowT::SubclassWindow

視窗所識別的子類別*hWnd*並將它附加至`CContainedWindowT`物件。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[in]在子類別化視窗的控制代碼。

### <a name="return-value"></a>傳回值

如果成功子類別化視窗;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

子類別化的視窗現在會使用[CContainedWindowT::WindowProc](#windowproc)。 原始的視窗程序會儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。

> [!NOTE]
>  請勿呼叫`SubclassWindow`如果您已呼叫[建立](#create)。

##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap

變更的訊息對應將會用來處理包含的視窗的訊息。

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>參數

*dwMsgMapID*<br/>
[in]訊息對應識別項。 若要使用預設的訊息對應，以宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，傳遞零。 若要使用替代的訊息對應，以宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，傳遞`msgMapID`。

### <a name="remarks"></a>備註

訊息對應必須包含物件中定義。

您一開始先建構函式中指定的訊息對應識別項。

##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow

中斷連結子類別化的視窗`CContainedWindowT`物件，並會還原原始的視窗程序，儲存在[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)。

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>參數

*bForce*<br/>
[in]設為 true 會強制要還原原始的視窗程序即使這個視窗程序`CContainedWindowT`物件不是目前作用中。 如果*bForce*設為 FALSE，而且視窗程序這`CContainedWindowT`物件不是目前作用中，將不會還原原始的視窗程序。

### <a name="return-value"></a>傳回值

先前子類別化視窗的控制代碼。 如果*bForce*設為 FALSE，而且視窗程序這`CContainedWindowT`物件不是目前作用中，會傳回 NULL。

### <a name="remarks"></a>備註

只有當您想要還原原始的視窗程序，在終結視窗之前，請使用這個方法。 否則，請[WindowProc](#windowproc)會自動執行這項操作時終結視窗。

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

`WindowProc` 將導向至所識別的訊息對應的訊息[m_dwMsgMapID](#m_dwmsgmapid)。 如果有必要，請`WindowProc`呼叫[DefWindowProc](#defwindowproc)進行額外的訊息處理。

## <a name="see-also"></a>另請參閱

[CWindow 類別](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap 類別](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[類別概觀](../../atl/atl-class-overview.md)
