---
title: CAxDialogImpl 類別
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
ms.openlocfilehash: 548d2aed0644187b4b8dee1e472b581f1f92d6a1
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418010"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl 類別

這個類別會執行裝載 ActiveX 控制項的對話方塊（強制回應或非強制回應）。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自 `CAxDialogImpl`的類別。

*TBase*<br/>
`CDialogImplBaseT`的基底視窗類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|呼叫這個方法，以建議或 unadvise 物件接收對應事件對應中的所有專案。|
|[CAxDialogImpl：： Create](#create)|呼叫這個方法來建立非強制回應對話方塊。|
|[CAxDialogImpl：:D estroyWindow](#destroywindow)|呼叫這個方法以終結非強制回應對話方塊。|
|[CAxDialogImpl：:D oModal](#domodal)|呼叫這個方法來建立強制回應對話方塊。|
|[CAxDialogImpl：： EndDialog](#enddialog)|呼叫這個方法以終結強制回應對話方塊。|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|呼叫這個方法，以取得 `DialogProc` 回呼函數的指標。|
|[CAxDialogImpl::GetIDD](#getidd)|呼叫此方法以取得對話方塊範本資源識別碼|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|呼叫這個方法來判斷訊息是否適用于此對話方塊，如果是，則處理訊息。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAxDialogImpl：： m_bModal](#m_bmodal)|只存在於 debug 組建中的變數，如果對話方塊為強制回應，則設定為 true。|

## <a name="remarks"></a>備註

`CAxDialogImpl` 可讓您建立模式或非強制回應對話方塊。 `CAxDialogImpl` 提供對話方塊程式，它會使用預設的訊息對應，將訊息導向至適當的處理常式。

`CAxDialogImpl` 衍生自 `CDialogImplBaseT`，而後者又衍生自*TBase* （根據預設，`CWindow`）和 `CMessageMap`。

您的類別必須定義指定對話方塊範本資源識別碼的 IDD 成員。 例如，使用 [**加入類別**] 對話方塊新增 ATL 對話方塊物件時，會自動在您的類別中新增下列程式程式碼：

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

其中 `MyDialog` 是在 ATL 對話方塊嚮導中輸入的**簡短名稱**。

如需詳細資訊，請參閱[執行對話方塊](../../atl/implementing-a-dialog-box.md)。

請注意，使用 `CAxDialogImpl` 建立的強制回應對話方塊上的 ActiveX 控制項不會支援快速鍵。 若要在使用 `CAxDialogImpl`建立的對話方塊上支援快速鍵，請建立非強制回應對話方塊，並使用您自己的訊息迴圈，在從佇列取得訊息以處理快速鍵之後，使用[CAxDialogImpl：： IsDialogMessage](#isdialogmessage) 。

如需 `CAxDialogImpl`的詳細資訊，請參閱[ATL 控制項](../../atl/atl-control-containment-faq.md)內含專案常見問題。

## <a name="inheritance-hierarchy"></a>繼承階層

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>需求

**標頭：** atlwin.h。h

##  <a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

呼叫這個方法，以建議或 unadvise 物件接收對應事件對應中的所有專案。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>參數

*bAdvise*<br/>
如果要建議所有接收專案，請設定為 true;如果要 unadvised 所有接收專案，則為 false。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

##  <a name="create"></a>CAxDialogImpl：： Create

呼叫這個方法來建立非強制回應對話方塊。

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
在主控視窗的控制碼。

*dwInitParam*<br/>
在在 WM_INITDIALOG 訊息的*lParam*參數中，指定要傳遞至對話方塊的值。

*RECT &*<br/>
不使用這個參數。 這個參數是由 `CComControl`傳入。

### <a name="return-value"></a>傳回值

新建立之對話方塊的控制碼。

### <a name="remarks"></a>備註

這個對話方塊會自動附加至 `CAxDialogImpl` 物件。 若要建立強制回應對話方塊，請呼叫[DoModal](#domodal)。

只會提供第二個覆寫，讓對話方塊可與[CComControl](../../atl/reference/ccomcontrol-class.md)搭配使用。

##  <a name="destroywindow"></a>CAxDialogImpl：:D estroyWindow

呼叫這個方法以終結非強制回應對話方塊。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>傳回值

如果已成功終結視窗，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

請勿呼叫 `DestroyWindow` 來摧毀強制回應對話方塊。 請改為呼叫[EndDialog](#enddialog) 。

##  <a name="domodal"></a>CAxDialogImpl：:D oModal

呼叫這個方法來建立強制回應對話方塊。

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
在主控視窗的控制碼。 預設值是[GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32 函數的傳回值。

*dwInitParam*<br/>
在在 WM_INITDIALOG 訊息的*lParam*參數中，指定要傳遞至對話方塊的值。

### <a name="return-value"></a>傳回值

如果成功，則為[EndDialog](#enddialog)呼叫中所指定的*nRetCode*參數值。否則為-1。

### <a name="remarks"></a>備註

這個對話方塊會自動附加至 `CAxDialogImpl` 物件。

若要建立非強制回應對話方塊，請呼叫[create](#create)。

##  <a name="enddialog"></a>CAxDialogImpl：： EndDialog

呼叫這個方法以終結強制回應對話方塊。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
在要由[DoModal](#domodal)傳回的值。

### <a name="return-value"></a>傳回值

如果對話方塊已終結，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

`EndDialog` 必須透過對話方塊程式來呼叫。 終結對話方塊之後，Windows 會使用*nRetCode*的值做為建立對話方塊之 `DoModal`的傳回值。

> [!NOTE]
>  請勿呼叫 `EndDialog` 來摧毀非強制回應對話方塊。 請改為呼叫[DestroyWindow](#destroywindow) 。

##  <a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc

呼叫這個方法，以取得 `DialogProc` 回呼函數的指標。

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>傳回值

傳回 `DialogProc` 回呼函數的指標。

### <a name="remarks"></a>備註

`DialogProc` 函數是應用程式定義的回呼函式。

##  <a name="getidd"></a>CAxDialogImpl::GetIDD

呼叫此方法以取得對話方塊範本資源識別碼。

```
int GetIDD();
```

### <a name="return-value"></a>傳回值

傳回對話方塊範本資源識別碼。

##  <a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

呼叫這個方法來判斷訊息是否適用于此對話方塊，如果是，則處理訊息。

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
包含要檢查之訊息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)結構的指標。

### <a name="return-value"></a>傳回值

如果訊息已處理，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

這個方法是要從訊息迴圈內呼叫。

##  <a name="m_bmodal"></a>CAxDialogImpl：： m_bModal

只存在於 debug 組建中的變數，如果對話方塊為強制回應，則設定為 true。

```
bool m_bModal;
```

## <a name="see-also"></a>另請參閱

[CDialogImpl 類別](../../atl/reference/cdialogimpl-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
