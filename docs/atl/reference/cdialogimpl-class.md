---
title: CDialogImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba47b7f78e372f05a851d2180590bbc68a8c61ca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068431"
---
# <a name="cdialogimpl-class"></a>CDialogImpl 類別

這個類別提供方法來建立非強制回應或非強制回應對話方塊。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`CDialogImpl`。

*TBase*<br/>
您的新類別的基底類別。 預設的基底類別[CWindow](../../atl/reference/cwindow-class.md)。

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
|[GetDialogProc](#getdialogproc)|傳回目前對話方塊程序。|
|[MapDialogRect](#mapdialogrect)|對話方塊單位，指定矩形的會對應至畫面單位 （像素為單位）。|
|[OnFinalMessage](#onfinalmessage)|接收到最後一則訊息，通常控制後呼叫。|

### <a name="static-functions"></a>靜態函式

|||
|-|-|
|[DialogProc](#dialogproc)|處理傳送至對話方塊中的訊息。|
|[StartDialogProc](#startdialogproc)|當第一個訊息接收到處理傳送至對話方塊中的訊息時呼叫。|

## <a name="remarks"></a>備註

使用`CDialogImpl`您可以建立強制回應或非強制回應對話方塊。 `CDialogImpl` 提供的對話方塊方塊程序，會使用預設的訊息對應將導向至適當的處理常式的訊息。

基底類別解構函式`~CWindowImplRoot`可確保視窗已不存在，然後再終結物件。

`CDialogImpl` 衍生自`CDialogImplBaseT`，而後者又衍生自`CWindowImplRoot`。

> [!NOTE]
>  您的類別必須定義`IDD`成員，指定對話方塊範本資源識別碼。 比方說，ATL 專案精靈 會自動會將下面這一行加入您的類別：

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

何處`MyDlg`是**簡短名稱**在精靈中輸入**名稱**頁面。

|如需詳細資訊|請參閱|
|--------------------------------|---------|
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|
|使用 ATL 中的對話方塊|[ATL 視窗類別](../../atl/atl-window-classes.md)|
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|
|對話方塊|[對話方塊](https://msdn.microsoft.com/library/windows/desktop/ms632588)和後續 Windows SDK 中的主題|

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="create"></a>  CDialogImpl::Create

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
[in]主控視窗控制代碼。

**RECT &** *rect* [in] [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定對話方塊的大小和位置。

*dwInitParam*<br/>
[in]指定要傳遞至對話方塊中的值*lParam* WM_INITDIALOG 訊息參數。

### <a name="return-value"></a>傳回值

新建立的對話方塊中的控制代碼。

### <a name="remarks"></a>備註

此對話方塊會自動附加至`CDialogImpl`物件。 若要建立強制回應對話方塊，請呼叫[DoModal](#domodal)。 上述的第二個覆寫僅適用於[CComControl](../../atl/reference/ccomcontrol-class.md)。

##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow

終結非強制回應對話方塊。  

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>傳回值

如果對話方塊已成功地損毀;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

如果對話方塊已成功地被終結; 為 true，則傳回否則為 FALSE。

##  <a name="dialogproc"></a>  CDialogImpl::DialogProc

此靜態函式會實作對話方塊程序。  

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[in]對話方塊中的控制代碼。

*uMsg*<br/>
[in]傳送到對話方塊中的訊息。

*wParam*<br/>
[in]其他特定訊息資訊。

*lParam*<br/>
[in]其他特定訊息資訊。

### <a name="return-value"></a>傳回值

如果訊息已處理，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

`DialogProc` 會使用預設的訊息對應將導向至適當的處理常式的訊息。

您可以覆寫`DialogProc`提供不同的機制，來處理訊息。

##  <a name="domodal"></a>  CDialogImpl::DoModal

建立強制回應對話方塊。

```
INT_PTR DoModal(  
    HWND hWndParent = ::GetActiveWindow(),   
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
[in]主控視窗控制代碼。 預設值是傳回值[GetActiveWindow](https://msdn.microsoft.com/library/windows/desktop/ms646292) Win32 函式。

*dwInitParam*<br/>
[in]指定要傳遞至對話方塊中的值*lParam* WM_INITDIALOG 訊息參數。

### <a name="return-value"></a>傳回值

如果成功，值*nRetCode*呼叫中指定的參數[EndDialog](#enddialog)。 否則為-1。

### <a name="remarks"></a>備註

此對話方塊會自動附加至`CDialogImpl`物件。

若要建立非強制回應對話方塊，請呼叫[建立](#create)。

##  <a name="enddialog"></a>  CDialogImpl::EndDialog

終結強制回應對話方塊。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
[in]要傳回的值[CDialogImpl::DoModal](#domodal)。

### <a name="return-value"></a>傳回值

如果對話方塊時終結;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

`EndDialog` 必須透過對話方塊程序呼叫。 終結對話方塊之後，Windows 會使用值*nRetCode*的傳回值為`DoModal`，其中建立對話方塊。

> [!NOTE]
>  請勿呼叫`EndDialog`終結非強制回應對話方塊。 呼叫[CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow)改。

##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc

傳回`DialogProc`，目前對話方塊程序。

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>傳回值

目前對話方塊程序。

### <a name="remarks"></a>備註

覆寫這個方法，以取代您自己的對話方塊程序。

##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect

將轉換 (maps) 對話方塊單位畫面以指定之矩形的單位 （像素為單位）。

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`CRect`物件或[RECT](../../mfc/reference/rect-structure1.md)結構要接收的更新，包含更新區域的用戶端座標。

### <a name="return-value"></a>傳回值

如果更新成功，則為非零0，如果更新失敗。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

### <a name="remarks"></a>備註

函數會取代在指定座標`RECT`結構已轉換的座標，可讓要用來建立對話方塊或調整控制項的位置 對話方塊中的結構。

##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage

接收到最後一則訊息後呼叫 (通常`WM_NCDESTROY`)。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[in]終結視窗控制代碼。

### <a name="remarks"></a>備註

請注意，是否您想要自動刪除您的物件，在視窗解構時，您可以呼叫**刪除此;** 這裡。

##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc

只呼叫一次，當收到的第一個訊息時，處理傳送至對話方塊中的訊息。

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[in]對話方塊中的控制代碼。

*uMsg*<br/>
[in]傳送到對話方塊中的訊息。

*wParam*<br/>
[in]其他特定訊息資訊。

*lParam*<br/>
[in]其他特定訊息資訊。

### <a name="return-value"></a>傳回值

視窗程序。

### <a name="remarks"></a>備註

初始呼叫後面`StartDialogProc`，`DialogProc`為設定的對話方塊程序，並進一步呼叫前往該處。

## <a name="see-also"></a>另請參閱

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[類別概觀](../../atl/atl-class-overview.md)