---
title: IAxwinHost 視窗介面
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: 561a65702f1d4f57b4db1afc75769ce4cc523c1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329915"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxwinHost 視窗介面

此介面提供操作許可控件及其主機物件的方法。

## <a name="syntax"></a>語法

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[建立控制](#createcontrollic)|創建許可控制項並將其附加到主機物件。|
|[建立控制](#createcontrollicex)|創建許可控制項,將其附加到主機物件,並可以選擇設定事件處理程式。|

## <a name="remarks"></a>備註

`IAxWinHostWindowLic`從[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)繼承,並添加支援創建許可控制項的方法。

有關使用此介面的成員的範例,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="requirements"></a>需求

此介面的定義可作為 IDL 或C++,如下所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (也包含在 ATLBase.h 中)|

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostwindowlic::建立控制

建立許可控制項,初始化它,並將其託管在識別的`hWnd`視窗中。

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>參數

*bstrLIC*<br/>
[在]包含控制項的授權金鑰的 BSTR。

### <a name="remarks"></a>備註

有關剩餘參數和返回值的說明,請參閱[IAxWinHostWindow:建立控制](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。

呼叫此方法等效於呼叫[IAxWinHostWindowlic::建立控制](#createcontrollicex)

### <a name="example"></a>範例

有關`IAxWinHostWindowLic::CreateControlLic`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHost視窗::建立控制

建立授權的 ActiveX 控制件,初始化它,並將其託管在指定的視窗中,類似於[IAxWinHostWindow::建立控制](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>參數

*bstrLIC*<br/>
[在]包含控制項的授權金鑰的 BSTR。

### <a name="remarks"></a>備註

有關剩餘參數和返回值的說明,請參閱[IAxWinHostWindow:創建ControlEx。](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex)

### <a name="example"></a>範例

有關`IAxWinHostWindowLic::CreateControlLicEx`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。
