---
title: IAxWinAmbientDispatchEx 介面
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: 3359c17996eb78c3249abc83ff2d439381f209fe
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352982"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 介面

這個介面會實作為裝載控制項的補充環境屬性。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|說明|
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|呼叫這個方法來補充具有使用者定義介面的預設環境屬性介面。|

## <a name="remarks"></a>備註

將此介面包含在以靜態方式連結到 ATL 的 ATL 應用程式中，並裝載 ActiveX 控制項，尤其是具有環境屬性的 ActiveX 控制項。 不包含此介面會產生此判斷提示：「您忘記將 LIBID 傳遞給 CComModule：： Init」

這個介面是由 ATL 的 ActiveX 控制項裝載物件所公開。 衍生自 [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)， `IAxWinAmbientDispatchEx` 加入了一個方法，可讓您補充 ATL 提供的環境屬性介面與您自己的其中一個。

<xref:System.Windows.Forms.AxHost> 將會嘗試 `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` 從包含程式碼的類型程式庫載入和的類型資訊。

如果您要連結至 ATL90.dll， **AXHost** 會從 DLL 中的類型程式庫載入類型資訊。

如需詳細資訊，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 。

## <a name="requirements"></a>需求

此介面的定義提供數種形式，如下表所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|atliface .idl|
|類型程式庫|ATL.dll|
|C++|atliface 也會包含在 Atlbase.h 中 () |

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> IAxWinAmbientDispatchEx：： SetAmbientDispatch

呼叫這個方法來補充具有使用者定義介面的預設環境屬性介面。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>參數

*pDispatch*<br/>
新介面的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

當 `SetAmbientDispatch` 使用新介面的指標呼叫時，如果 [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)尚未提供這些屬性，則會使用這個新介面叫用裝載控制項所要求的任何屬性或方法。

## <a name="see-also"></a>另請參閱

[IAxWinAmbientDispatch 介面](../../atl/reference/iaxwinambientdispatch-interface.md)
