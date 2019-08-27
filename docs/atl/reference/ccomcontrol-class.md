---
title: CComControl 類別
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: bf0f64d8c7b8e8a3347e4c0fcad902b9e8a0ecb4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497525"
---
# <a name="ccomcontrol-class"></a>CComControl 類別

這個類別會提供建立和管理 ATL 控制項的方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>參數

*T*<br/>
執行控制項的類別。

*WinBase*<br/>
用來執行視窗化函數的基類。 預設為[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|擷取所要求介面的指標。|
|[CComControl::CreateControlWindow](#createcontrolwindow)|建立控制項的視窗。|
|[CComControl::FireOnChanged](#fireonchanged)|通知容器的接收器, 控制項屬性已變更。|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|通知容器的接收, 控制項屬性即將變更, 而且物件正在要求接收如何繼續。|
|[CComControl::MessageBox](#messagebox)|呼叫這個方法來建立、顯示及操作訊息方塊。|

## <a name="remarks"></a>備註

`CComControl`是一組實用的控制項 helper 函式, 以及 ATL 控制項的重要資料成員。 當您使用 ATL 控制項 Wizard 建立標準控制項或 DHTML 控制項時, 嚮導會自動從`CComControl`衍生您的類別。 `CComControl`從[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)衍生其大部分的方法。

如需建立控制項的詳細資訊, 請參閱[ATL 教學](../../atl/active-template-library-atl-tutorial.md)課程。 如需 ATL 專案 Wizard 的詳細資訊, 請參閱[建立 Atl 專案一](../../atl/reference/creating-an-atl-project.md)文。

如需`CComControl`方法和資料成員的示範, 請參閱[CIRC](../../overview/visual-cpp-samples.md)範例。

## <a name="inheritance-hierarchy"></a>繼承階層

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="ccomcontrol"></a>CComControl::CComControl

建構函式。

```
CComControl();
```

### <a name="remarks"></a>備註

呼叫[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase)的函式, 傳遞`m_hWnd`透過[CWindowImpl](../../atl/reference/cwindowimpl-class.md)繼承的資料成員。

##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface

擷取所要求介面的指標。

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>參數

*iid*<br/>
在所要求之介面的 GUID。

*ppv*<br/>
脫銷*Iid*所識別之介面指標的指標, 如果找不到介面, 則為 Null。

### <a name="remarks"></a>備註

只處理 COM 對應表中的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow

根據預設, 會藉由呼叫`CWindowImpl::Create`來建立控制項的視窗。

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
在父系或擁有者視窗的控制碼。 必須提供有效的視窗控制碼。 [控制] 視窗會局限于其父視窗的區域。

*rcPos*<br/>
在要建立之視窗的初始大小和位置。

### <a name="remarks"></a>備註

如果您想要執行其他動作, 而不是建立單一視窗 (例如, 建立兩個視窗), 其中一個會成為控制項的工具列, 請覆寫這個方法。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>CComControl::FireOnChanged

通知容器的接收器, 控制項屬性已變更。

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>參數

*dispID*<br/>
在已變更之屬性的識別碼。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

如果您的控制項類別衍生自[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), 這個方法會呼叫[CFirePropNotifyEvent:: FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged)來通知`IPropertyNotifySink`所有連接的介面, 指定的控制項屬性已經變更。 如果您的控制項類別不是衍生`IPropertyNotifySink`自, 則這個方法會傳回 S_OK。

即使您的控制項不支援連接點, 此方法仍可放心呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit

通知容器的接收, 控制項屬性即將變更, 而且物件正在要求接收如何繼續。

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>參數

*dispID*<br/>
在要變更之屬性的識別碼。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

如果您的控制項類別衍生自[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), 這個方法會呼叫[CFirePropNotifyEvent:: FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit)來通知`IPropertyNotifySink`所有連接的介面, 指定的控制項屬性即將變更。 如果您的控制項類別不是衍生`IPropertyNotifySink`自, 則這個方法會傳回 S_OK。

即使您的控制項不支援連接點, 此方法仍可放心呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>CComControl:: MessageBox

呼叫這個方法來建立、顯示及操作訊息方塊。

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
要顯示在訊息方塊中的文字。

*lpszCaption*<br/>
對話方塊標題。 如果為 Null (預設值), 則會使用標題 "Error"。

*nType*<br/>
指定對話方塊的內容和行為。 如需可用的不同訊息方塊清單, 請參閱 Windows SDK 檔中的[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)專案。 預設會提供簡單的 **[確定]** 按鈕。

### <a name="return-value"></a>傳回值

傳回整數值, 指定 Windows SDK 檔的[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)底下列出的其中一個功能表項目值。

### <a name="remarks"></a>備註

`MessageBox`在開發期間很有用, 而且可讓您輕鬆地向使用者顯示錯誤或警告訊息。

## <a name="see-also"></a>另請參閱

[CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[CComControlBase 類別](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl 類別](../../atl/reference/ccomcompositecontrol-class.md)
