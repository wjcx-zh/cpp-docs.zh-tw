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
ms.openlocfilehash: 5b4afabe2c12dff048bc6a6fb904a82b3cea4d01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539434"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 介面

這個介面會實作補充環境裝載的控制項屬性。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|會呼叫這個方法，來補充預設環境屬性介面與使用者定義的介面。|

## <a name="remarks"></a>備註

在靜態連結至 ATL 和主機 ActiveX 控制項，尤其是 ActiveX 控制項有環境屬性的 ATL 應用程式中包含這個介面。 不包含這個介面會產生這個判斷提示: 「 您是否忘記將 LIBID 傳遞給 Init 」

這個介面會公開由裝載物件的 ATL 的 ActiveX 控制項。 衍生自[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)，`IAxWinAmbientDispatchEx`將可讓您增補 ATL 提供與您自己的環境屬性介面的方法。

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)會嘗試載入的型別資訊的相關`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`從類型程式庫包含程式碼。

如果您要連結至 ATL90.dll， **AXHost**會從類型程式庫 DLL 中載入的型別資訊。

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需詳細資訊。

## <a name="requirements"></a>需求

此介面的定義有數種格式下, 表所示。

|定義類型|檔案|
|---------------------|----------|
|IDL|atliface.idl|
|型別程式庫|ATL.dll|
|C++|atliface.h （也包含在 ATLBase.h）|

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

會呼叫這個方法，來補充預設環境屬性介面與使用者定義的介面。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>參數

*pDispatch*<br/>
新的介面指標。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

當`SetAmbientDispatch`會呼叫新的介面指標，這個新介面將用來叫用的任何屬性或方法，如果系統要求的所裝載的控制項，這些屬性所未提供的[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>另請參閱

[IAxWinAmbientDispatch 介面](../../atl/reference/iaxwinambientdispatch-interface.md)
