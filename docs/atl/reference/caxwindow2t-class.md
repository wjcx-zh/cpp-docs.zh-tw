---
title: CAxWindow2T 類別
ms.date: 11/04/2016
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
ms.openlocfilehash: 14080b624132979df533135bc1eef108dc793398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318704"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T 類別

此類提供了用於操作承載 ActiveX 控制項的視窗的方法,並且還支援託管許可的 ActiveX 控制件。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>參數

*TBase*<br/>
衍生的類別`CAxWindowT`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|建構 `CAxWindow2T` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T::建立](#create)|創建主機視窗。|
|[CAxWindow2T::建立控制](#createcontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[CAxWindow2T::建立控制](#createcontrollicex)|創建許可的 ActiveX 控制件,初始化它,在指定的視窗中託管它,並從控制項中檢索介面指標(或指標)。|
|[CAxWindow2T::獲取wndClass名稱](#getwndclassname)|檢索視窗類名稱的靜態方法。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T::運算符 |](#operator_eq)|將 HWND 分配`CAxWindow2T`給現有 物件。|

## <a name="remarks"></a>備註

`CAxWindow2T`提供了用於操作承載 ActiveX 控制件的視窗的方法。 `CAxWindow2T`還支援託管許可的 ActiveX 控制件。 託管由 **「AtlAxWinLic80」** 提供,`CAxWindow2T`由包裝。

類`CAxWindow2`作為`CAxWindow2T`類的專業化實現。 此專業化化聲明為:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT`成員記錄在[CAxWindow](../../atl/reference/caxwindow-class.md)下。

有關使用此類成員的範例,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

建構 `CAxWindow2T` 物件。

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的句柄。

## <a name="caxwindow2tcreate"></a><a name="create"></a>CAxWindow2T::建立

創建主機視窗。

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

`CAxWindow2T::Create`呼叫[CWindow::](../../atl/reference/cwindow-class.md#create)使用 LPCTSTR *lpstrwndClass*參數創建到提供`AtlAxWinLic80`控制項宿主 ( ) 的視窗類。

有關`CWindow::Create`參數和返回值的說明,請參閱。

**注意**如果 0 用作*MenuOrID*參數的值,則必須將其指定為 0U(預設值),以避免編譯器錯誤。

### <a name="example"></a>範例

有關`CAxWindow2T::Create`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a>CAxWindow2T::建立控制

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
控制件的許可證金鑰;如果建立非許可控制項,則為 NULL。

### <a name="remarks"></a>備註

有關剩餘參數和返回值的說明,請參閱[CAxWindow:CreateControl。](../../atl/reference/caxwindow-class.md#createcontrol)

### <a name="example"></a>範例

有關`CAxWindow2T::CreateControlLic`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a>CAxWindow2T::建立控制

創建許可的 ActiveX 控制件,初始化它,在指定的視窗中託管它,並從控制項中檢索介面指標(或指標)。

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
控制件的許可證金鑰;如果建立非許可控制項,則為 NULL。

### <a name="remarks"></a>備註

有關剩餘參數和返回值的說明,請參閱[CAxWindow:createControlEx。](../../atl/reference/caxwindow-class.md#createcontrolex)

### <a name="example"></a>範例

有關`CAxWindow2T::CreateControlLicEx`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow2T::獲取wndClass名稱

檢索視窗類的名稱。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>傳回值

指向包含視窗類`AtlAxWinLic80`( ) 名稱的字串的指標,該字串可以承載許可和非許可的 ActiveX 控制件。

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a>CAxWindow2T::運算符 |

將 HWND 分配`CAxWindow2T`給現有 物件。

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的句柄。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)
