---
title: CDialogImplclass
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
ms.openlocfilehash: d5ab7293f73429a93c3fcab243c2e34d3c78f28a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747714"
---
# <a name="cdialogimpl-class"></a>CDialogImplclass

此類提供了創建模式或無模式對話方塊的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`CDialogImpl`。

*TBase*<br/>
新類的基類。 預設基項是[CWindow](../../atl/reference/cwindow-class.md)。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[建立](#create)|創建無模式對話方塊。|
|[銷毀視窗](#destroywindow)|銷毀無模式對話方塊。|
|[多模態](#domodal)|創建模式對話方塊。|
|[結束交談](#enddialog)|銷毀模式對話方塊。|

### <a name="cdialogimplbaset-methods"></a>CDialogimplbaseT 方法

|||
|-|-|
|[取得對話](#getdialogproc)|返回當前對話框過程。|
|[對應對話](#mapdialogrect)|將指定矩形的對話框單位映射到螢幕單位(圖元)。|
|[OnFinalMessage](#onfinalmessage)|收到最後一條消息后調用,通常WM_NCDESTROY。|

### <a name="static-functions"></a>靜態函式

|||
|-|-|
|[DialogProc](#dialogproc)|處理發送到對話框的消息。|
|[開始對話](#startdialogproc)|收到第一條消息以處理發送到對話框的消息時調用。|

## <a name="remarks"></a>備註

有了`CDialogImpl`,您可以創建一個模態或無模式對話方塊。 `CDialogImpl`提供對話框過程,該過程使用預設消息映射將消息定向到相應的處理程式。

基類析構函數`~CWindowImplRoot`可確保在銷毀物件之前視窗已消失。

`CDialogImpl`衍生,`CDialogImplBaseT`後者又派生`CWindowImplRoot`自 。

> [!NOTE]
> 類別必須定義指定對話框`IDD`樣本資源 ID 的成員。 例如,ATL 專案精靈會自動將以下行添加到您的類:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

嚮導`MyDlg`名稱頁中輸入的**短名稱**的位置。 **Names**

|如需下列項目的詳細資訊|請參閱|
|--------------------------------|---------|
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|
|在 ATL 中使用對話框|[ATL 視窗類別](../../atl/atl-window-classes.md)|
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|
|對話方塊|[Windows](/windows/win32/dlgbox/dialog-boxes) SDK 中的對話框及其後續主題|

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="cdialogimplcreate"></a><a name="create"></a>CDialogImpl::建立

創建無模式對話方塊。

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

*hWnd 父母*<br/>
[在]擁有者視窗的句柄。

**RECT&** *rect* [in] 指定對話框大小和位置的[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*德維尼帕拉姆*<br/>
[在]指定要傳遞給WM_INITDIALOG訊息的*lParam*參數中的對話框的值。

### <a name="return-value"></a>傳回值

新創建的對話框的句柄。

### <a name="remarks"></a>備註

此對話框會自動附加到`CDialogImpl`物件。 要建立模態對話框,請呼叫[DoModal](#domodal)。 上面的第二個覆寫僅用於[CComControl](../../atl/reference/ccomcontrol-class.md)。

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogimpl::D

銷毀無模式對話方塊。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>傳回值

如果對話框已成功銷毀,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

如果對話框已成功銷毀,則返回 TRUE;否則 FALSE。

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl::DialogProc

此靜態函數實現對話框過程。

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[在]對話框的句柄。

*烏姆斯格*<br/>
[在]發送到對話框的消息。

*wParam*<br/>
[在]其他特定於消息的資訊。

*lParam*<br/>
[在]其他特定於消息的資訊。

### <a name="return-value"></a>傳回值

如果處理消息,則為 TRUE;如果消息已處理,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

`DialogProc`使用預設消息映射將消息定向到相應的處理程式。

您可以重寫`DialogProc`以提供用於處理消息的不同機制。

## <a name="cdialogimpldomodal"></a><a name="domodal"></a>CDialogimpl::Do模態

創建模式對話方塊。

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
[在]擁有者視窗的句柄。 默認值是[GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32 函數的返回值。

*德維尼帕拉姆*<br/>
[在]指定要傳遞給WM_INITDIALOG訊息的*lParam*參數中的對話框的值。

### <a name="return-value"></a>傳回值

如果成功,則調用[EndDialog](#enddialog)中指定的*nRetCode*參數的值。 否則為 -1。

### <a name="remarks"></a>備註

此對話框會自動附加到`CDialogImpl`物件。

要建立無模式對話框,請呼叫["創建](#create)"。

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a>CDialogimpl:結束對話

銷毀模式對話方塊。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
[在][CDialogImpl::Do模態](#domodal))要返回的值。

### <a name="return-value"></a>傳回值

如果對話框已銷毀,則為 TRUE;如果對話框已銷毀,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

`EndDialog`必須通過對話過程調用。 銷毀對話框後,Windows 使用*nRetCode*的值作為`DoModal`創建對話框的返回值。

> [!NOTE]
> 不要調用`EndDialog`以銷毀無模式對話方塊。 呼叫[CWindow::D視窗](../../atl/reference/cwindow-class.md#destroywindow)。

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl::取得對話Proc

返回`DialogProc`,當前對話框過程。

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>傳回值

當前對話框過程。

### <a name="remarks"></a>備註

重寫此方法以將對話框過程替換為您自己的對話框過程。

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogimpl::映射對話重新

將指定矩形的對話框單位轉換為螢幕單位(圖元)。

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向物件`CRect`或[RECT](/windows/win32/api/windef/ns-windef-rect)結構,該結構用於接收包含更新區域的更新的用戶端座標。

### <a name="return-value"></a>傳回值

如果更新成功,則非零;如果更新失敗,為 0。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

### <a name="remarks"></a>備註

該函數將指定`RECT`結構中的座標替換為轉換的座標,從而允許該結構用於創建對話方塊或在對話方塊中定位控制件。

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>CDialogimpl::在最終消息

收到最後一條消息後調用`WM_NCDESTROY`( 通常 )。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[在]正在銷毀的視窗的句柄。

### <a name="remarks"></a>備註

請注意,如果要在視窗銷毀時自動刪除物件,可以調用 **「刪除此」;** 此處。

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl::開始對話

只調用一次,當收到第一條消息時,處理發送到對話方塊的消息。

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
[在]對話框的句柄。

*烏姆斯格*<br/>
[在]發送到對話框的消息。

*wParam*<br/>
[在]其他特定於消息的資訊。

*lParam*<br/>
[在]其他特定於消息的資訊。

### <a name="return-value"></a>傳回值

視窗過程。

### <a name="remarks"></a>備註

初始呼叫 後`StartDialogProc``DialogProc`, 設定為對話框過程,並進一步調用轉到那裡。

## <a name="see-also"></a>另請參閱

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[類別概觀](../../atl/atl-class-overview.md)
