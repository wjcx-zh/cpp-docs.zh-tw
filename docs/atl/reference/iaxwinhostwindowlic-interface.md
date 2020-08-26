---
title: IAxWinHostWindowLic 介面
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: 55a96e27e58d844ec6fabec689dc2aedf536a9a7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835450"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic 介面

此介面提供操作授權控制項和其主物件的方法。

## <a name="syntax"></a>語法

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|-|-|
|[CreateControlLic](#createcontrollic)|建立授權的控制項，並將它附加至主機物件。|
|[CreateControlLicEx](#createcontrollicex)|建立授權的控制項、將其附加至主機物件，並選擇性地設定事件處理常式。|

## <a name="remarks"></a>備註

`IAxWinHostWindowLic` 繼承自 [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) ，並新增支援授權控制項建立的方法。

請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) ，以取得使用此介面成員的範例。

## <a name="requirements"></a>規格需求

此介面的定義可作為 IDL 或 c + +，如下所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|ATLIFace .idl|
|C++|ATLIFace 也會包含在 Atlbase.h 中 () |

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a> IAxWinHostWindowLic：： CreateControlLic

建立授權的控制項、將它初始化，然後將它裝載在所識別的視窗中 `hWnd` 。

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>參數

*bstrLic*<br/>
在包含控制項授權金鑰的 BSTR。

### <a name="remarks"></a>備註

如需其餘參數和傳回值的描述，請參閱 [IAxWinHostWindow：： CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) 。

呼叫這個方法相當於呼叫 [IAxWinHostWindowLic：： CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) `IAxWinHostWindowLic::CreateControlLic` 。

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a> IAxWinHostWindowLic：： CreateControlLicEx

建立授權的 ActiveX 控制項、將它初始化，然後將它裝載于指定的視窗中，類似于 [IAxWinHostWindow：： CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol)。

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

*bstrLic*<br/>
在包含控制項授權金鑰的 BSTR。

### <a name="remarks"></a>備註

如需其餘參數和傳回值的描述，請參閱 [IAxWinHostWindow：： CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) 。

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) `IAxWinHostWindowLic::CreateControlLicEx` 。
