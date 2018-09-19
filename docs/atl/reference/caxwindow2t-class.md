---
title: CAxWindow2T 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cfb82cfa21d5cc69e66d7980c4878e1659a7a79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036224"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T 類別

這個類別提供方法，以操作裝載 ActiveX 控制項，而且也支援授權的 ActiveX 控制項裝載的視窗。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>參數

*TBase*<br/>
從中的類別`CAxWindowT`衍生。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|建構 `CAxWindow2T` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T::Create](#create)|建立主視窗。|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|建立授權的 ActiveX 控制項、 將它初始化，裝載在指定的視窗中，並從控制項擷取介面指標 （或指標）。|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|靜態方法，擷取的視窗類別名稱。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T::operator =](#operator_eq)|指派至現有的 HWND`CAxWindow2T`物件。|

## <a name="remarks"></a>備註

`CAxWindow2T` 提供方法來操作視窗裝載 ActiveX 控制項。 `CAxWindow2T` 也有提供裝載授權的 ActiveX 控制項的支援。 裝載由提供 「 **AtlAxWinLic80**"，其中會由包裝`CAxWindow2T`。

類別`CAxWindow2`實作為的特製化`CAxWindow2T`類別。 此特製化會宣告為：

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` 成員會記錄下[CAxWindow](../../atl/reference/caxwindow-class.md)。

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)的範例會使用這個類別的成員。

## <a name="inheritance-hierarchy"></a>繼承階層

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="caxwindow2t"></a>  CAxWindow2T::CAxWindow2T

建構 `CAxWindow2T` 物件。

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有的視窗控制代碼。

##  <a name="create"></a>  CAxWindow2T::Create

建立主視窗。

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="remarks"></a>備註

`CAxWindow2T::Create` 呼叫[CWindow::Create](../../atl/reference/cwindow-class.md#create)使用 LPCTSTR *lpstrWndClass*參數設定為提供控制項所裝載的視窗類別 (`AtlAxWinLic80`)。

請參閱`CWindow::Create`參數和傳回值的說明。

**附註**如果使用 0 做為值*MenuOrID*參數，它必須指定為 0U （預設值） 以避免編譯器錯誤。

### <a name="example"></a>範例

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需範例，會使用`CAxWindow2T::Create`。

##  <a name="createcontrollic"></a>  CAxWindow2T::CreateControlLic

建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>參數

*bstrLicKey*<br/>
控制項中，授權金鑰如果建立要在未經授權的控制項，則為 NULL。

### <a name="remarks"></a>備註

請參閱[CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol)剩餘的參數和傳回值的說明。

### <a name="example"></a>範例

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需範例，會使用`CAxWindow2T::CreateControlLic`。

##  <a name="createcontrollicex"></a>  CAxWindow2T::CreateControlLicEx

建立授權的 ActiveX 控制項、 將它初始化，裝載在指定的視窗中，並從控制項擷取介面指標 （或指標）。

```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```

### <a name="parameters"></a>參數

*bstrLicKey*<br/>
控制項中，授權金鑰如果建立要在未經授權的控制項，則為 NULL。

### <a name="remarks"></a>備註

請參閱[CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex)剩餘的參數和傳回值的說明。

### <a name="example"></a>範例

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需範例，會使用`CAxWindow2T::CreateControlLicEx`。

##  <a name="getwndclassname"></a>  CAxWindow2T::GetWndClassName

擷取視窗類別名稱。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>傳回值

字串，包含視窗類別名稱的指標 (`AtlAxWinLic80`) 可裝載授權和要在未經授權的 ActiveX 控制項。

##  <a name="operator_eq"></a>  CAxWindow2T::operator =

指派至現有的 HWND`CAxWindow2T`物件。

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有的視窗控制代碼。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)
