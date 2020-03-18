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
ms.openlocfilehash: b57eaf105bfca1a49d53b5e5e99969b0fa2fc82f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417905"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 類別

這個類別會提供執行複合控制項所需的方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的類別，以及您想要支援複合控制項的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|建構函式。|
|[CComCompositeControl：： ~ CComCompositeControl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|呼叫這個方法，以建議或 unadvise 複合控制項主控的所有控制項。|
|[CComCompositeControl::CalcExtent](#calcextent)|呼叫這個方法來計算用來裝載複合控制項之對話資源的 HIMETRIC 單位大小。|
|[CComCompositeControl：： Create](#create)|呼叫這個方法是為了建立複合控制項的控制項視窗。|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|呼叫這個方法來建立控制項視窗，並建議任何裝載的控制項。|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|呼叫這個方法，以使用容器的背景色彩來設定複合控制項的背景色彩。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl：： m_hbrBackground](#m_hbrbackground)|背景筆刷。|
|[CComCompositeControl：： m_hWndFocus](#m_hwndfocus)|目前具有焦點之視窗的控制碼。|

## <a name="remarks"></a>備註

衍生自 class `CComCompositeControl` 的類別會繼承 ActiveX 複合控制項的功能。 衍生自 `CComCompositeControl` 的 ActiveX 控制項是由標準對話方塊所主控。 這些控制項類型稱為複合控制項，因為它們能夠裝載其他控制項（原生 Windows 控制項和 ActiveX 控制項）。

`CComCompositeControl` 藉由尋找子類別中的列舉資料成員，來識別要用來建立複合控制項的對話方塊資源。 這個子類別的成員 IDD 會設定為將當做控制項視窗使用之對話資源的資源識別碼。 以下是從 `CComCompositeControl` 衍生的類別所應包含的資料成員範例，以識別要用於控制項視窗的對話方塊資源：

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
>  複合控制項一律是視窗型控制項，雖然它們可以包含無視窗的控制項。

由 `CComCompositeControl`衍生類別所執行的控制項，具有內建的預設 tab 鍵行為。 當控制項在包含的應用程式中以索引標籤式的方式取得焦點時，連續按下 TAB 鍵會使焦點迴圈到所有複合控制項的包含控制項，然後從複合控制項移出，然後放到容器的定位順序。 裝載控制項的定位順序是由對話資源決定，並決定進行 tab 鍵的順序。

> [!NOTE]
>  為了讓快速鍵能夠與 `CComCompositeControl`正常搭配運作，您必須在建立控制項時載入快速鍵對應表、將控制碼和加速器數目傳遞回[IOleControlImpl：： GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)，最後在釋放控制項時損毀資料表。

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>需求

**標頭：** atlctl。h

##  <a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap

呼叫這個方法，以建議或 unadvise 複合控制項主控的所有控制項。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>參數

*bAdvise*<br/>
如果要建議所有控制項，則為 True;否則為 false。

### <a name="return-value"></a>傳回值

|||
|-|-|
|S_OK  |事件接收對應中的所有控制項都已成功連接或中斷與其事件來源的連線。|
|E_FAIL  |並非事件接收對應中的所有控制項都可以成功地連接或中斷其事件來源的連線。|
|E_POINTER  |此錯誤通常表示控制項的事件接收對應中的專案發生問題，或在 `IDispEventImpl` 或 `IDispEventSimpleImpl` 基類中使用樣板引數時發生問題。|
|CONNECT_E_ADVISELIMIT  |連接點已達到連線限制，無法接受更多連線。|
|CONNECT_E_CANNOTCONNECT  |接收不支援此連接點所需的介面。|
|CONNECT_E_NOCONNECTION  |Cookie 值不代表有效的連接。 此錯誤通常表示控制項的事件接收對應中的專案發生問題，或在 `IDispEventImpl` 或 `IDispEventSimpleImpl` 基類中使用樣板引數時發生問題。|

### <a name="remarks"></a>備註

這個方法的基底實作為搜尋事件接收對應中的專案。 然後，它會針對事件接收器對應的接收專案所描述的 COM 物件，建議或 unadvises 連接點。 這個成員方法也會依賴衍生類別從一個 `IDispEventImpl` 的實例繼承到接收對應中每個要建議或 unadvised 的控制項。

##  <a name="calcextent"></a>CComCompositeControl::CalcExtent

呼叫這個方法來計算用來裝載複合控制項之對話資源的 HIMETRIC 單位大小。

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>參數

*size*<br/>
要由這個方法填入之 `SIZE` 結構的參考。

### <a name="return-value"></a>傳回值

如果控制項是由對話方塊所主控，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

大小會在*size*參數中傳回。

##  <a name="create"></a>CComCompositeControl：： Create

呼叫這個方法是為了建立複合控制項的控制項視窗。

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
控制項父視窗的控制碼。

*rcPos*<br/>
保留。

*dwInitParam*<br/>
要在控制項建立期間傳遞至控制項的資料。 當做*dwInitParam*傳遞的資料會顯示為[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)訊息的 LPARAM 參數，在建立時，將會傳送至複合控制項。

### <a name="return-value"></a>傳回值

新建立之複合控制項對話方塊的控制碼。

### <a name="remarks"></a>備註

這個方法通常會在就地啟用控制項時呼叫。

##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

建構函式。

```
CComCompositeControl();
```

### <a name="remarks"></a>備註

將[CComCompositeControl：： m_hbrBackground](#m_hbrbackground)和[CComCompositeControl：： m_hWndFocus](#m_hwndfocus)資料成員初始化為 Null。

##  <a name="dtor"></a>CComCompositeControl：： ~ CComCompositeControl

解構函式。

```
~CComCompositeControl();
```

### <a name="remarks"></a>備註

移除背景物件（如果有的話）。

##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

呼叫這個方法來建立控制項視窗，並建議任何裝載的控制項。

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
控制項父視窗的控制碼。

*rcPos*<br/>
相對於*hWndParent*的用戶端座標中，複合控制項的位置矩形。

### <a name="return-value"></a>傳回值

傳回新建立之複合控制項對話方塊的控制碼。

### <a name="remarks"></a>備註

這個方法會呼叫[CComCompositeControl：： Create](#create)和[CComCompositeControl：： AdviseSinkMap](#advisesinkmap)。

##  <a name="m_hbrbackground"></a>CComCompositeControl：： m_hbrBackground

背景筆刷。

```
HBRUSH m_hbrBackground;
```

##  <a name="m_hwndfocus"></a>CComCompositeControl：： m_hWndFocus

目前具有焦點之視窗的控制碼。

```
HWND m_hWndFocus;
```

##  <a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient

呼叫這個方法，以使用容器的背景色彩來設定複合控制項的背景色彩。

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
