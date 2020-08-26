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
ms.openlocfilehash: a37386c40f119c855dcb8584a72ce85c48a66381
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834735"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 類別

這個類別會提供執行複合控制項所需的方法。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別（衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)），以及您想要為複合控制項支援的其他任何介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl：： CComCompositeControl](#ccomcompositecontrol)|建構函式。|
|[CComCompositeControl：： ~ CComCompositeControl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl：： AdviseSinkMap](#advisesinkmap)|呼叫這個方法來建議或 unadvise 複合控制項所裝載的所有控制項。|
|[CComCompositeControl：： CalcExtent](#calcextent)|呼叫這個方法來計算用來裝載複合控制項之對話方塊資源的 HIMETRIC 單位大小。|
|[CComCompositeControl：： Create](#create)|呼叫這個方法來建立複合控制項的控制項視窗。|
|[CComCompositeControl：： CreateControlWindow](#createcontrolwindow)|呼叫這個方法來建立控制項視窗，並建議任何裝載的控制項。|
|[CComCompositeControl：： SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|呼叫這個方法，以使用容器的背景色彩來設定複合控制項的背景色彩。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComCompositeControl：： m_hbrBackground](#m_hbrbackground)|背景筆刷。|
|[CComCompositeControl：： m_hWndFocus](#m_hwndfocus)|目前具有焦點的視窗控制碼。|

## <a name="remarks"></a>備註

衍生自類別的類別會 `CComCompositeControl` 繼承 ActiveX 複合控制項的功能。 衍生自的 ActiveX 控制項 `CComCompositeControl` 是由標準對話方塊所主控。 這些類型的控制項稱為複合控制項，因為它們可以裝載其他控制項， (原生 Windows 控制項和 ActiveX 控制項) 。

`CComCompositeControl` 藉由尋找子類別中的列舉資料成員，識別用來建立複合控制項的對話方塊資源。 此子類別的成員 IDD 會設定為將作為控制項視窗的對話資源的資源識別碼。 以下是衍生自的類別應該包含的資料成員範例， `CComCompositeControl` 以識別要用於控制項視窗的對話資源：

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> 複合控制項一直都是視窗控制項，不過它們可以包含無視窗控制項。

由衍生類別所執行的控制項 `CComCompositeControl` 具有內建的預設定位行為。 當控制項在包含的應用程式中按下 tab 鍵時，會連續按下 TAB 鍵，將焦點放在所有複合控制項的包含控制項中，然後從複合控制項移至容器的定位順序中的下一個專案。 裝載控制項的定位順序是由對話方塊資源決定，並決定進行定位的順序。

> [!NOTE]
> 為了讓加速器正常運作，您必須在 `CComCompositeControl` 建立控制項時載入快速鍵對應表、將控制碼和快速鍵數目傳遞回 [IOleControlImpl：： GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)，最後在釋放控制項時終結資料表。

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>規格需求

**標頭：** atlctl。h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a> CComCompositeControl：： AdviseSinkMap

呼叫這個方法來建議或 unadvise 複合控制項所裝載的所有控制項。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>參數

*bAdvise*<br/>
如果要建議所有控制項，則為 True;否則為 false。

### <a name="return-value"></a>傳回值

| 值 | 描述 |
|--|--|
| `S_OK` | 事件接收對應中的所有控制項都已成功連接或中斷與其事件來源的連接。 |
| `E_FAIL` | 並非事件接收對應中的所有控制項都可以成功連接或中斷與其事件來源的連接。 |
| `E_POINTER` | 此錯誤通常表示控制項的事件接收對應發生問題，或是在或基類中使用的樣板引數有問題 `IDispEventImpl` `IDispEventSimpleImpl` 。 |
| `CONNECT_E_ADVISELIMIT` | 連接點已達到連線限制，無法接受更多連線。 |
| `CONNECT_E_CANNOTCONNECT` | 接收不支援這個連接點所需的介面。 |
| `CONNECT_E_NOCONNECTION` | Cookie 值不代表有效的連接。 此錯誤通常表示控制項的事件接收對應發生問題，或是在或基類中使用的樣板引數有問題 `IDispEventImpl` `IDispEventSimpleImpl` 。 |

### <a name="remarks"></a>備註

這個方法的基底實作為搜尋事件接收對應中的專案。 然後，它會建議或 unadvises 連接點，指向事件接收對應的接收專案所描述的 COM 物件。 此成員方法也會依賴衍生類別 `IDispEventImpl` 針對接收對應中的每個控制項（要建議或 unadvised）繼承自一個實例的事實。

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a> CComCompositeControl：： CalcExtent

呼叫這個方法來計算用來裝載複合控制項之對話方塊資源的 HIMETRIC 單位大小。

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>參數

*size*<br/>
`SIZE`要由這個方法填入之結構的參考。

### <a name="return-value"></a>傳回值

如果控制項是由對話方塊主控，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

大小會在 *size* 參數中傳回。

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a> CComCompositeControl：： Create

呼叫這個方法來建立複合控制項的控制項視窗。

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
控制項之父視窗的控制碼。

*rcPos*<br/>
保留的。

*dwInitParam*<br/>
在控制項建立期間傳遞至控制項的資料。 以 *dwInitParam* 傳遞的資料會顯示為 [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) 訊息的 LPARAM 參數，而此參數會在建立時傳送至複合控制項。

### <a name="return-value"></a>傳回值

新建立的複合控制項對話方塊的控制碼。

### <a name="remarks"></a>備註

在就地啟用控制項時，通常會呼叫這個方法。

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a> CComCompositeControl：： CComCompositeControl

建構函式。

```
CComCompositeControl();
```

### <a name="remarks"></a>備註

將 [CComCompositeControl：： m_hbrBackground](#m_hbrbackground) 和 [CComCompositeControl：： m_hWndFocus](#m_hwndfocus) 資料成員初始化為 Null。

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a> CComCompositeControl：： ~ CComCompositeControl

解構函式。

```
~CComCompositeControl();
```

### <a name="remarks"></a>備註

移除背景物件（如果有的話）。

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a> CComCompositeControl：： CreateControlWindow

呼叫這個方法來建立控制項視窗，並建議任何裝載的控制項。

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
控制項之父視窗的控制碼。

*rcPos*<br/>
相對於 *hWndParent*之用戶端座標中複合控制項的位置矩形。

### <a name="return-value"></a>傳回值

傳回新建立的複合控制項對話方塊的控制碼。

### <a name="remarks"></a>備註

這個方法會呼叫 [CComCompositeControl：： Create](#create) 和 [CComCompositeControl：： AdviseSinkMap](#advisesinkmap)。

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a> CComCompositeControl：： m_hbrBackground

背景筆刷。

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a> CComCompositeControl：： m_hWndFocus

目前具有焦點的視窗控制碼。

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a> CComCompositeControl：： SetBackgroundColorFromAmbient

呼叫這個方法，以使用容器的背景色彩來設定複合控制項的背景色彩。

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
