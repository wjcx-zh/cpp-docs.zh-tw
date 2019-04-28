---
title: CComCompositeControl 類別
ms.date: 11/04/2016
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
ms.openlocfilehash: f1a9a2d0628b3683f047ce9858d809040438db03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260236"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 類別

這個類別會提供實作複合控制項所需的方法。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或是[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)、 您想要從任何其他介面以支援您的複合控制項。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|建構函式。|
|[CComCompositeControl::~CComCompositeControl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|呼叫這個方法來通知或取消通知，複合控制項所裝載的所有控制項。|
|[CComCompositeControl::CalcExtent](#calcextent)|呼叫這個方法來計算以 himetric 為單位，用來裝載複合控制項的對話方塊資源的大小。|
|[CComCompositeControl::Create](#create)|建立複合控制項的 [控制] 視窗，會呼叫這個方法。|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|呼叫這個方法來建立控制項的視窗，也建議任何裝載的控制項。|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|呼叫此方法以設定使用容器的背景色彩的複合控制項的背景色彩。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|背景筆刷。|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|目前具有焦點的視窗控制代碼。|

## <a name="remarks"></a>備註

類別衍生自類別`CComCompositeControl`繼承 ActiveX 複合控制項的功能。 ActiveX 控制項衍生自`CComCompositeControl`所裝載的標準對話方塊。 這些類型的控制項稱為複合控制項，因為他們就能夠裝載其他控制項 （Windows 的原生控制項和 ActiveX 控制項）。

`CComCompositeControl` 識別用來建立複合控制項所尋找的子類別中的列舉的資料成員的對話方塊資源。 IDD 這個子類別的成員會設定為將用於控制項的視窗對話方塊資源的資源識別碼。 以下是此類別衍生自資料成員的範例`CComCompositeControl`來識別要用於控制項的視窗對話方塊資源應該包含：

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
>  複合控制項一律是視窗型控制項，但可以包含無視窗控制項。

藉由將控制項`CComCompositeControl`-衍生的類別有預設的定位停駐點內建的行為。 當控制項被定位停駐到包含的應用程式所收到焦點時，連續按 TAB 鍵，會導致將焦點轉給循環所有的複合控制項的包含的控制項，然後從複合控制項並到下一個項目容器的定位順序。 裝載控制項的定位順序取決於對話方塊資源，並決定的順序在哪一個定位停駐點將會發生。

> [!NOTE]
>  為了讓使用適當的加速器`CComCompositeControl`，就必須在建立控制項時，載入快速鍵對應表，則會傳遞的控制代碼和回加速器的數目[IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)，及當使用者放開控制項，最後終結資料表。

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="advisesinkmap"></a>  CComCompositeControl::AdviseSinkMap

呼叫這個方法來通知或取消通知，複合控制項所裝載的所有控制項。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>參數

*bAdvise*<br/>
如果接到; 的所有控制項都是，則為 true。否則為 false。

### <a name="return-value"></a>傳回值

|||
|-|-|
|S_OK  |所有控制項中的事件接收對應已連線或已成功中斷連接其事件來源。|
|E_FAIL  |並非所有控制在事件接收對應無法連線，或從其事件來源已成功中斷連接。|
|E_POINTER  |此錯誤通常表示控制項的事件接收對應中的項目有問題或樣板引數中所使用的問題`IDispEventImpl`或`IDispEventSimpleImpl`基底類別。|
|CONNECT_E_ADVISELIMIT  |連接點已達到其限制的連線，並無法接受更多。|
|CONNECT_E_CANNOTCONNECT  |接收不支援這個連接點所需的介面。|
|CONNECT_E_NOCONNECTION  |Cookie 值不代表有效的連接。 此錯誤通常表示控制項的事件接收對應中的項目有問題或樣板引數中所使用的問題`IDispEventImpl`或`IDispEventSimpleImpl`基底類別。|

### <a name="remarks"></a>備註

這個方法的基底實作會搜尋所有項目在事件接收器對應。 它接著會建議，或取消通知事件接收對應的接收項目所描述之 COM 物件的連接點。 這個成員方法也會依賴衍生的類別繼承自一個執行個體的事實`IDispEventImpl`將建議或 unadvised 接收對應中的每一個控制項。

##  <a name="calcextent"></a>  CComCompositeControl::CalcExtent

呼叫這個方法來計算以 himetric 為單位，用來裝載複合控制項的對話方塊資源的大小。

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>參數

*size*<br/>
參考`SIZE`填滿由這個方法的結構。

### <a name="return-value"></a>傳回值

如果控制項裝載在對話方塊中，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

大小會傳入*大小*參數。

##  <a name="create"></a>  CComCompositeControl::Create

建立複合控制項的 [控制] 視窗，會呼叫這個方法。

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
控制項的父視窗控制代碼。

*rcPos*<br/>
保留的。

*dwInitParam*<br/>
在建立控制項期間傳遞給控制項的資料。 將資料當做*dwInitParam*會顯示為的 LPARAM 參數[WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog)訊息，這會在建立時傳送至複合控制項。

### <a name="return-value"></a>傳回值

到新建立的複合控制項 對話方塊中的控制代碼。

### <a name="remarks"></a>備註

這個方法通常會在控制項的就地啟用期間呼叫。

##  <a name="ccomcompositecontrol"></a>  CComCompositeControl::CComCompositeControl

建構函式。

```
CComCompositeControl();
```

### <a name="remarks"></a>備註

初始化[CComCompositeControl::m_hbrBackground](#m_hbrbackground)並[CComCompositeControl::m_hWndFocus](#m_hwndfocus)為 NULL 的資料成員。

##  <a name="dtor"></a>  CComCompositeControl::~CComCompositeControl

解構函式。

```
~CComCompositeControl();
```

### <a name="remarks"></a>備註

若有的話，請刪除背景的物件。

##  <a name="createcontrolwindow"></a>  CComCompositeControl::CreateControlWindow

呼叫這個方法來建立控制項的視窗，也建議任何裝載的控制項。

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
控制項的父視窗控制代碼。

*rcPos*<br/>
用戶端中的複合控制項的位置矩形座標相對於*hWndParent*。

### <a name="return-value"></a>傳回值

傳回新建立的複合控制項 對話方塊的控制代碼。

### <a name="remarks"></a>備註

這個方法會呼叫[CComCompositeControl::Create](#create)並[CComCompositeControl::AdviseSinkMap](#advisesinkmap)。

##  <a name="m_hbrbackground"></a>  CComCompositeControl::m_hbrBackground

背景筆刷。

```
HBRUSH m_hbrBackground;
```

##  <a name="m_hwndfocus"></a>  CComCompositeControl::m_hWndFocus

目前具有焦點的視窗控制代碼。

```
HWND m_hWndFocus;
```

##  <a name="setbackgroundcolorfromambient"></a>  CComCompositeControl::SetBackgroundColorFromAmbient

呼叫此方法以設定使用容器的背景色彩的複合控制項的背景色彩。

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
