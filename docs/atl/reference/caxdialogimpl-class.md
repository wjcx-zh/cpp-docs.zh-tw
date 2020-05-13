---
title: CAx 對話類
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: d8e60a817d197f67c14318a7d50ddf796e570142
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318733"
---
# <a name="caxdialogimpl-class"></a>CAx 對話類

此類實現承載 ActiveX 控件的對話框(模式或無模式)。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`CAxDialogImpl`。

*TBase*<br/>
的基本視窗類別`CDialogImplBaseT`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAx對話::建議SinkMap](#advisesinkmap)|呼叫此方法可建議或取消通知物件接收器映射事件映射中的所有項目。|
|[CAx 對話:建立](#create)|呼叫此方法以建立無模式對話方塊。|
|[CAx對話::D](#destroywindow)|調用此方法以銷毀無模式對話方塊。|
|[CAx對話::Do模態](#domodal)|調用此方法以創建模態對話方塊。|
|[CAx對話::結束對話](#enddialog)|調用此方法以銷毀模式對話方塊。|
|[CAx對話::取得對話Proc](#getdialogproc)|調用此方法以獲取指向回調函數的`DialogProc`指標。|
|[CAx對話::取得IDD](#getidd)|呼叫此方法取得對話框樣本資源識別碼|
|[CAx對話::對話訊息](#isdialogmessage)|呼叫此方法以確定訊息是否用於此對話方塊,如果是,則處理該消息。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAx對話::m_bModal](#m_bmodal)|僅在調試生成中存在的變數,如果對話框是模態的,則設置為 true。|

## <a name="remarks"></a>備註

`CAxDialogImpl`允許您創建模態或無模式對話方塊。 `CAxDialogImpl`提供對話框過程,該過程使用預設消息映射將消息定向到相應的處理程式。

`CAxDialogImpl`衍生`CDialogImplBaseT`, 它又派生自*TBase* (預設的`CWindow`狀況`CMessageMap`) 與 。

類別必須定義指定對話方塊樣本資源 ID 的 IDD 成員。 例如,使用 **「新增類」** 對話框新增 ATL 對話框會自動將以下行新增到類:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

ATL 對話框精靈中輸入`MyDialog`**的短名稱**的位置。

有關詳細資訊[,請參閱實現對話框](../../atl/implementing-a-dialog-box.md)。

請注意,使用模式`CAxDialogImpl`對話方塊創建的 ActiveX 控制項將不支援快速鍵。 要支援使用`CAxDialogImpl`創建的對話方塊上的快捷鍵,請建立一個無模式對話框,並使用您自己的消息迴圈,在從佇列中收到消息以處理快捷鍵後使用[CAxDialogImpl:isDialogMessage。](#isdialogmessage)

有關的詳細資訊`CAxDialogImpl`,請參閱[ATL 控制控制控制常見問題 解答](../../atl/atl-control-containment-faq.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="caxdialogimpladvisesinkmap"></a><a name="advisesinkmap"></a>CAx對話::建議SinkMap

呼叫此方法可建議或取消通知物件接收器映射事件映射中的所有項目。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>參數

*b 建議*<br/>
如果建議所有接收器條目,則設置為 true;如果所有接收器條目都是未通知的,則為 false。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="caxdialogimplcreate"></a><a name="create"></a>CAx 對話:建立

呼叫此方法以建立無模式對話方塊。

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
[在]擁有者視窗的句柄。

*德維尼帕拉姆*<br/>
[在]指定要傳遞給WM_INITDIALOG訊息的*lParam*參數中的對話框的值。

*reCT&*<br/>
不使用這個參數。 此參數透過傳入`CComControl`。

### <a name="return-value"></a>傳回值

新創建的對話框的句柄。

### <a name="remarks"></a>備註

此對話框會自動附加到`CAxDialogImpl`物件。 要建立模態對話框,請呼叫[DoModal](#domodal)。

第二個重寫僅提供,因此對話方塊可以與[CComControl](../../atl/reference/ccomcontrol-class.md)一起使用。

## <a name="caxdialogimpldestroywindow"></a><a name="destroywindow"></a>CAx對話::D

調用此方法以銷毀無模式對話方塊。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>傳回值

如果視窗已成功銷毀,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

不要調用`DestroyWindow`以銷毀模式對話方塊。 請改為呼叫[結束對話](#enddialog)。

## <a name="caxdialogimpldomodal"></a><a name="domodal"></a>CAx對話::Do模態

調用此方法以創建模態對話方塊。

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

如果成功,則調用[EndDialog](#enddialog)中指定的*nRetCode*參數的值。否則,-1。

### <a name="remarks"></a>備註

此對話框會自動附加到`CAxDialogImpl`物件。

要建立無模式對話框,請呼叫["創建](#create)"。

## <a name="caxdialogimplenddialog"></a><a name="enddialog"></a>CAx對話::結束對話

調用此方法以銷毀模式對話方塊。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
[在][DoModal](#domodal)要返回的值。

### <a name="return-value"></a>傳回值

如果對話框已銷毀,則為 TRUE;如果對話框已銷毀,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

`EndDialog`必須通過對話框過程調用。 銷毀對話框後,Windows 使用*nRetCode*的值作為`DoModal`創建對話框的返回值。

> [!NOTE]
> 不要調用`EndDialog`以銷毀無模式對話方塊。 請改為呼叫[的視窗](#destroywindow)。

## <a name="caxdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CAx對話::取得對話Proc

調用此方法以獲取指向回調函數的`DialogProc`指標。

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>傳回值

返回指向回調函數的`DialogProc`指標。

### <a name="remarks"></a>備註

該`DialogProc`函數是應用程式定義的回調函數。

## <a name="caxdialogimplgetidd"></a><a name="getidd"></a>CAx對話::取得IDD

呼叫此方法獲取對話方塊樣本資源 ID。

```
int GetIDD();
```

### <a name="return-value"></a>傳回值

返回對話框範本資源 ID。

## <a name="caxdialogimplisdialogmessage"></a><a name="isdialogmessage"></a>CAx對話::對話訊息

呼叫此方法以確定訊息是否用於此對話方塊,如果是,則處理該消息。

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
指向包含要檢查的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)結構的指標。

### <a name="return-value"></a>傳回值

如果消息已處理,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

此方法旨在從消息循環中調用。

## <a name="caxdialogimplm_bmodal"></a><a name="m_bmodal"></a>CAx對話::m_bModal

僅在調試生成中存在的變數,如果對話框是模態的,則設置為 true。

```
bool m_bModal;
```

## <a name="see-also"></a>另請參閱

[CDialogImplclass](../../atl/reference/cdialogimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
