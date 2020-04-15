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
ms.openlocfilehash: 3518de3596748fa284c1f898b69d1576903e9510
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320759"
---
# <a name="ccomcontrol-class"></a>CComControl 類別

此類提供用於創建和管理 ATL 控制項的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>參數

*T*<br/>
實現控件的類。

*溫基*<br/>
實現視窗函數的基類。 預設值為[CWindowImpl](../../atl/reference/cwindowimpl-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom控制:CCom控制](#ccomcontrol)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom控制::控制查詢介面](#controlqueryinterface)|擷取所要求介面的指標。|
|[CCom 控制:建立控制視窗](#createcontrolwindow)|為控制項創建一個視窗。|
|[CComControl:火通](#fireonchanged)|通知容器的接收器控制件屬性已更改。|
|[CComControl::火對請求編輯](#fireonrequestedit)|通知容器的接收器控制件屬性即將更改,並且物件正在詢問接收器如何繼續。|
|[CComControl:訊息框](#messagebox)|呼叫此方法以建立、顯示和操作訊息框。|

## <a name="remarks"></a>備註

`CComControl`是一組有用的控制幫助器功能和 ATL 控件的基本數據成員。 使用 ATL 控制件精靈建立標準控制項或 DHTML 控制件時,嚮導`CComControl`將自動從派生類。 `CComControl`它的大部分方法來自[CComControlBase。](../../atl/reference/ccomcontrolbase-class.md)

有關建立控制項的詳細資訊,請參閱[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 有關 ATL 專案精靈的詳細資訊,請參閱創建[ATL 專案](../../atl/reference/creating-an-atl-project.md)的文章。

有關方法和數據成員`CComControl`的演示,請參閱[中國保監會](../../overview/visual-cpp-samples.md)示例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ccomcontrolccomcontrol"></a><a name="ccomcontrol"></a>CCom控制:CCom控制

建構函式。

```
CComControl();
```

### <a name="remarks"></a>備註

調用[CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase)建構函數`m_hWnd`,傳遞 透過[CWindowImpl](../../atl/reference/cwindowimpl-class.md)繼承的資料成員。

## <a name="ccomcontrolcontrolqueryinterface"></a><a name="controlqueryinterface"></a>CCom控制::控制查詢介面

擷取所要求介面的指標。

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]請求的介面的 GUID。

*Ppv*<br/>
[出]指向*iid*識別的介面指標,如果找不到介面,則指向 NULL 的指標。

### <a name="remarks"></a>備註

僅處理 COM 地圖表中的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

## <a name="ccomcontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CCom 控制:建立控制視窗

默認情況下,通過調用`CWindowImpl::Create`為控制項創建一個視窗。

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
[在]處理父視窗或擁有者視窗。 必須提供有效的視窗句柄。 控制視窗限制在其父視窗的區域。

*rcPos*<br/>
[在]要建立的視窗的初始大小和位置。

### <a name="remarks"></a>備註

如果要執行創建單個視窗以外的操作,例如創建兩個視窗,其中一個視窗將成為控制項的工具列,請重寫此方法。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

## <a name="ccomcontrolfireonchanged"></a><a name="fireonchanged"></a>CComControl:火通

通知容器的接收器控制件屬性已更改。

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>參數

*脫從ID*<br/>
[在]已更改的屬性的標識碼。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

如果控件類派生自[IPropertyNotifySink,](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)則此方法調用[CFirePropNotifyEvent::FireOnS,](cfirepropnotifyevent-class.md#fireonchanged)用於`IPropertyNotifySink`通知所有連接的介面指定的控制項屬性已更改。 如果控件類不派生自`IPropertyNotifySink`,則此方法返回S_OK。

即使您的控制項不支援連接點,也安全地調用此方法。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

## <a name="ccomcontrolfireonrequestedit"></a><a name="fireonrequestedit"></a>CComControl::火對請求編輯

通知容器的接收器控制件屬性即將更改,並且物件正在詢問接收器如何繼續。

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>參數

*脫從ID*<br/>
[在]要更改的屬性的標識碼。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

如果控件類派生自[IPropertyNotifySink,](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)則此方法調用[CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit)以`IPropertyNotifySink`通知所有 連接的介面指定的控制項屬性即將更改。 如果控件類不派生自`IPropertyNotifySink`,則此方法返回S_OK。

即使您的控制項不支援連接點,也安全地調用此方法。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

## <a name="ccomcontrolmessagebox"></a><a name="messagebox"></a>CComControl:訊息框

呼叫此方法以建立、顯示和操作訊息框。

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
要在消息框中顯示的文本。

*lpszCaption*<br/>
對話框標題。 如果為 NULL(預設值),則使用標題" 錯誤"

*nType*<br/>
指定對話框的內容和行為。 有關可用的不同消息框的清單,請參閱 Windows SDK 文檔中的[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)條目。 默認值提供了一個簡單的 **「確定」** 按鈕。

### <a name="return-value"></a>傳回值

返回一個整數值,指定 Windows SDK 文檔中[MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)下列出的功能表項值之一。

### <a name="remarks"></a>備註

`MessageBox`在開發過程中非常有用,並且作為向使用者顯示錯誤或警告消息的簡便方法。

## <a name="see-also"></a>另請參閱

[CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComControlBase 類別](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CCom 複合控制類](../../atl/reference/ccomcompositecontrol-class.md)
