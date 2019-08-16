---
title: CDialogImpl 類別
ms.date: 11/04/2016
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: bc39a5deeb270b0426a4b199fc9ba01917c292bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496806"
---
# <a name="cdialogimpl-class"></a>CDialogImpl 類別

這個類別提供建立模式或非強制回應對話方塊的方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`CDialogImpl`的類別。

*TBase*<br/>
新類別的基類。 預設基類為[CWindow](../../atl/reference/cwindow-class.md)。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[建立](#create)|建立非強制回應對話方塊。|
|[DestroyWindow](#destroywindow)|終結非強制回應對話方塊。|
|[DoModal](#domodal)|建立強制回應對話方塊。|
|[EndDialog](#enddialog)|終結強制回應對話方塊。|

### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT 方法

|||
|-|-|
|[GetDialogProc](#getdialogproc)|傳回目前的對話方塊程式。|
|[MapDialogRect](#mapdialogrect)|將指定矩形的對話方塊單位對應到螢幕單元 (圖元)。|
|[OnFinalMessage](#onfinalmessage)|在收到最後一則訊息後呼叫, 通常是 WM_NCDESTROY。|

### <a name="static-functions"></a>靜態函式

|||
|-|-|
|[DialogProc](#dialogproc)|處理傳送至對話方塊的訊息。|
|[StartDialogProc](#startdialogproc)|當收到第一個訊息來處理傳送至對話方塊的訊息時呼叫。|

## <a name="remarks"></a>備註

您`CDialogImpl`可以使用來建立強制回應或非強制回應對話方塊。 `CDialogImpl`提供對話方塊程式, 它會使用預設的訊息對應, 將訊息導向適當的處理常式。

基類的析構函`~CWindowImplRoot`式可確保在終結物件之前, 視窗已消失。

`CDialogImpl`衍生自`CDialogImplBaseT`, 而後者又衍生自`CWindowImplRoot`。

> [!NOTE]
>  您的類別必須定義`IDD`指定對話方塊範本資源識別碼的成員。 例如, ATL 專案嚮導會自動將下面這一行新增至您的類別:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

其中`MyDlg`是在 wizard 的 [**名稱**] 頁面中輸入的**簡短名稱**。

|如需詳細資訊|請參閱|
|--------------------------------|---------|
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|
|在 ATL 中使用對話方塊|[ATL 視窗類別](../../atl/atl-window-classes.md)|
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|
|對話方塊|[對話方塊](/windows/win32/dlgbox/dialog-boxes)和 Windows SDK 中的後續主題|

## <a name="requirements"></a>需求

**標頭:** atlwin.h。h

##  <a name="create"></a>CDialogImpl:: Create

建立非強制回應對話方塊。

```
HWND Create(
    HWND hWndParent,
    LPARAM dwInitParam = NULL );

HWND Create(
    HWND hWndParent,
    RECT&,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
在主控視窗的控制碼。

**RECT &** *rect*在[矩形](/previous-versions/dd162897\(v=vs.85\))結構, 指定對話方塊的大小和位置。

*dwInitParam*<br/>
在指定要傳遞至 WM_INITDIALOG 訊息之*lParam*參數中對話方塊的值。

### <a name="return-value"></a>傳回值

新建立之對話方塊的控制碼。

### <a name="remarks"></a>備註

這個對話方塊會自動附加至`CDialogImpl`物件。 若要建立強制回應對話方塊, 請呼叫[DoModal](#domodal)。 上述的第二個覆寫只能搭配[CComControl](../../atl/reference/ccomcontrol-class.md)使用。

##  <a name="destroywindow"></a>CDialogImpl::D estroyWindow

終結非強制回應對話方塊。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>傳回值

如果已成功終結對話方塊, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果已成功終結對話方塊, 則傳回 TRUE;否則為 FALSE。

##  <a name="dialogproc"></a>CDialogImpl::D ialogProc

這個靜態函式會實作用對話方塊程式。

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在對話方塊的控制碼。

*uMsg*<br/>
在傳送至對話方塊的訊息。

*wParam*<br/>
在其他訊息特定資訊。

*lParam*<br/>
在其他訊息特定資訊。

### <a name="return-value"></a>傳回值

如果已處理訊息, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

`DialogProc`會使用預設的訊息對應, 將訊息導向適當的處理常式。

您可以覆`DialogProc`寫來提供處理訊息的不同機制。

##  <a name="domodal"></a>CDialogImpl::D oModal

建立強制回應對話方塊。

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
在主控視窗的控制碼。 預設值是[GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32 函數的傳回值。

*dwInitParam*<br/>
在指定要傳遞至 WM_INITDIALOG 訊息之*lParam*參數中對話方塊的值。

### <a name="return-value"></a>傳回值

如果成功, 則為[EndDialog](#enddialog)呼叫中所指定的*nRetCode*參數值。 否則為-1。

### <a name="remarks"></a>備註

這個對話方塊會自動附加至`CDialogImpl`物件。

若要建立非強制回應對話方塊, 請呼叫[create](#create)。

##  <a name="enddialog"></a>CDialogImpl:: EndDialog

終結強制回應對話方塊。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
在要由 CDialogImpl 傳回的值[::D omodal](#domodal)。

### <a name="return-value"></a>傳回值

如果對話方塊已終結, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

`EndDialog`必須透過對話程式呼叫。 終結對話方塊之後, Windows 會使用*nRetCode*的值做為的傳回值`DoModal`, 以建立此對話方塊。

> [!NOTE]
>  請勿呼叫`EndDialog`來摧毀非強制回應對話方塊。 請改[為呼叫 CWindow::D estroywindow](../../atl/reference/cwindow-class.md#destroywindow) 。

##  <a name="getdialogproc"></a>CDialogImpl:: GetDialogProc

`DialogProc`傳回目前的對話方塊程式。

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>傳回值

目前的對話方塊程式。

### <a name="remarks"></a>備註

覆寫這個方法, 將對話方塊程式取代為您自己的進程。

##  <a name="mapdialogrect"></a>CDialogImpl:: MapDialogRect

將指定矩形的對話方塊單位轉換 (對應) 為螢幕單元 (圖元)。

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向物件或`CRect` [矩形](/windows/win32/api/windef/ns-windef-rect)結構, 用來接收包含更新區域之更新的用戶端座標。

### <a name="return-value"></a>傳回值

如果更新成功, 則為非零;如果更新失敗, 則為0。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

### <a name="remarks"></a>備註

函式會以轉換的座標取代`RECT`指定之結構中的座標, 讓您可以使用結構來建立對話方塊, 或在對話方塊中放置控制項。

##  <a name="onfinalmessage"></a>CDialogImpl:: OnFinalMessage

在收到最後一則訊息之後呼叫`WM_NCDESTROY`(通常是)。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在要終結之視窗的控制碼。

### <a name="remarks"></a>備註

請注意, 如果您想要在視窗損毀時自動刪除物件, 您可以在這裡呼叫**delete** 。

##  <a name="startdialogproc"></a>CDialogImpl:: StartDialogProc

在收到第一個訊息時呼叫一次, 以處理傳送至對話方塊的訊息。

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
在對話方塊的控制碼。

*uMsg*<br/>
在傳送至對話方塊的訊息。

*wParam*<br/>
在其他訊息特定資訊。

*lParam*<br/>
在其他訊息特定資訊。

### <a name="return-value"></a>傳回值

視窗程式。

### <a name="remarks"></a>備註

初始呼叫`StartDialogProc`之後, `DialogProc`會設定為對話程式, 並在該處進行進一步的呼叫。

## <a name="see-also"></a>另請參閱

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[類別總覽](../../atl/atl-class-overview.md)
