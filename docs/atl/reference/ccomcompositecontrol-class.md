---
title: CCom 複合控制類
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
ms.openlocfilehash: 700a8047ab1fa9df85c8e6530eb3eed5f29bd3d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320810"
---
# <a name="ccomcompositecontrol-class"></a>CCom 複合控制類

此類提供實現複合控件所需的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別,派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及您要支援複合控制項的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom複合控制:CCom複合控制](#ccomcompositecontrol)|建構函式。|
|[CCom複合控制:*CCom複合控制](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom複合控制::建議SinkMap](#advisesinkmap)|調用此方法可建議或取消建議由複合控件承載的所有控制項。|
|[CCom複合控制::鈣度](#calcextent)|調用此方法以 HIMETRIC 單位的形式計算用於承載複合控制元件的對話方塊資源的大小。|
|[CCom 複合控制:建立](#create)|調用此方法是為了創建複合控制件的控制視窗。|
|[CCom 複合控制:建立控制視窗](#createcontrolwindow)|調用此方法以創建控制項視窗並通知任何託管控件。|
|[CCom複合控制::從環境設定背景顏色](#setbackgroundcolorfromambient)|呼叫此方法以使用容器的背景顏色設定複合控制項的背景顏色。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCom複合控制::m_hbrBackground](#m_hbrbackground)|背景畫筆。|
|[CCom複合控制::m_hWndFocus](#m_hwndfocus)|當前具有焦點的視窗的句柄。|

## <a name="remarks"></a>備註

從類`CComCompositeControl`派生的類繼承 ActiveX 複合控件的功能。 派生自的`CComCompositeControl`ActiveX 控件由標準對話框承載。 這些類型的控制項稱為複合控制項,因為它們能夠承載其他控制項(本機Windows控制件和ActiveX控制項)。

`CComCompositeControl`通過在子類中查找枚舉的數據成員,標識用於創建複合控制件的對話框資源。 此子類的成員 IDD 設定為將用作控制項視窗的對話方塊資源的資源 ID。 下面是派生的`CComCompositeControl`類別包含的資料成員的範例,用於識別要用於控制項視窗的對話框資源:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> 複合控件始終是視窗控制項,儘管它們可以包含無視窗控制項。

派生`CComCompositeControl`類實現的控制項內置了默認製表符行為。 當控件通過在包含應用程式中的選項卡式接收焦點時,連續按下 TAB 鍵將導致焦點循環通過所有複合控制項的包含控制項,然後從複合控制項中迴圈到容器的選項卡順序下一個項。 托管控件的選項卡順序由對話框資源確定,並確定選項卡的進行順序。

> [!NOTE]
> 為了使加速器在`CComCompositeControl`創建控制項時載入加速器表,將句柄和加速器數傳回[IOleControlImpl:getControlInfo,](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)最後在釋放控制項時銷毀該表。

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a>CCom複合控制::建議SinkMap

調用此方法可建議或取消建議由複合控件承載的所有控制項。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>參數

*b 建議*<br/>
如果建議所有控制項,則為 True;否則是虛假的。

### <a name="return-value"></a>傳回值

|||
|-|-|
|S_OK  |事件接收器對應中的所有控制項已成功連接或斷開其事件來源。|
|E_FAIL  |並非所有事件接收器映射中的控制件都可以成功連接或斷開其事件源。|
|E_POINTER  |此錯誤通常表示控制項的事件接收器映射中的項目有問題,`IDispEventImpl`或者在或`IDispEventSimpleImpl`基類中使用的範本參數有問題。|
|CONNECT_E_ADVISELIMIT  |連接點已達到連線限制，無法接受更多連線。|
|CONNECT_E_CANNOTCONNECT  |接收器不支援此連接點所需的介面。|
|CONNECT_E_NOCONNECTION  |Cookie 值不表示有效的連接。 此錯誤通常表示控制項的事件接收器映射中的項目有問題,`IDispEventImpl`或者在或`IDispEventSimpleImpl`基類中使用的範本參數有問題。|

### <a name="remarks"></a>備註

此方法的基本實現搜索事件接收器映射中的條目。 然後,它建議或取消建議與事件接收器映射的接收器條目描述的 COM 物件的連接點。 此成員方法還依賴於派生類從要建議或不通知的接收器映射中每個控件`IDispEventImpl`的一個實例繼承這一事實。

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a>CCom複合控制::鈣度

調用此方法以 HIMETRIC 單位的形式計算用於承載複合控制元件的對話方塊資源的大小。

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>參數

*大小*<br/>
對要由此方法`SIZE`填充的結構的引用。

### <a name="return-value"></a>傳回值

如果控件由對話框承載,則為 TRUE;如果控件由對話框承載,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

大小在*大小*參數中返回。

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a>CCom 複合控制:建立

調用此方法是為了創建複合控制件的控制視窗。

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
控件的父視窗的句柄。

*rcPos*<br/>
已保留。

*德維尼帕拉姆*<br/>
在創建控制項期間要傳遞給控制項的數據。 作為*dwInitParam*傳遞的資料將顯示為[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息的 LPARAM 參數,該參數將在創建時發送到複合控制項。

### <a name="return-value"></a>傳回值

新創建的複合控制項對話框的句柄。

### <a name="remarks"></a>備註

此方法通常在控件的就地激活期間調用。

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a>CCom複合控制:CCom複合控制

建構函式。

```
CComCompositeControl();
```

### <a name="remarks"></a>備註

初始化[CCom 複合控制::m_hbrBackground](#m_hbrbackground)和[CCom 複合控制::m_hWndFocus](#m_hwndfocus)資料成員到 NULL。

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a>CCom複合控制:*CCom複合控制

解構函式。

```
~CComCompositeControl();
```

### <a name="remarks"></a>備註

刪除背景物件(如果存在)。

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CCom 複合控制:建立控制視窗

調用此方法以創建控制項視窗並通知任何託管控件。

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
控件的父視窗的句柄。

*rcPos*<br/>
相對於*hWndParent*的複合控制者的位置矩形。

### <a name="return-value"></a>傳回值

將句柄返回到新創建的複合控制項對話框。

### <a name="remarks"></a>備註

此方法呼叫[CCom 複合控制::建立](#create)與[CCom 複合控制::建議 SinkMap](#advisesinkmap)。

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a>CCom複合控制::m_hbrBackground

背景畫筆。

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a>CCom複合控制::m_hWndFocus

當前具有焦點的視窗的句柄。

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a>CCom複合控制::從環境設定背景顏色

呼叫此方法以使用容器的背景顏色設定複合控制項的背景顏色。

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
