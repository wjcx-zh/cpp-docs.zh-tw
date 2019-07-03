---
title: IDocHostUIHandlerDispatch 介面
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: a60c178eff1e02c3032e792f9a0420dfeab82388
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552160"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 介面

介面的 Microsoft HTML 剖析和轉譯引擎。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

> [!NOTE]
>  下表中的連結是成員 INet SDK 參考主題[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))介面。 `IDocHostUIHandlerDispatch` 具有相同的功能`IDocUIHostHandler`，差異在於使用`IDocHostUIHandlerDispatch`是分配介面，而`IDocUIHostHandler`是一種自訂介面。

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|從 MSHTML 實作的呼叫[IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)。 也稱為 MSHTML 顯示強制回應 UI 時。|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|若要允許主機替換 MSHTML 的資料物件的 MSHTML 主機上呼叫。|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|當它用做為置放目標，讓主機提供另一個呼叫 MSHTML [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)。|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|取得主機的 IDispatch 介面 MSHTML 呼叫。|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|擷取 MSHTML 主機的 UI 功能。|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|傳回在其下 MSHTML 儲存使用者喜好設定的登錄機碼。|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|MSHTML 移除其功能表與工具列時呼叫。|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Ondocwindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)。|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Onframewindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)。|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Resizeborder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)。|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|從顯示的內容功能表的 MSHTML 呼叫。|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|允許主機替換 MSHTML 功能表和工具列。|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|由 MSHTML 呼叫，當[:: Translateaccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)或是[iolecontrolsite:: Translateaccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)呼叫。|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|呼叫 MSHTML，讓主機有機會修改要載入的 URL。|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|通知主機命令狀態已變更。|

## <a name="remarks"></a>備註

主機可以取代功能表、 工具列和由 Microsoft HTML 剖析和轉譯引擎 (MSHTML) 來實作這個介面的操作功能表。

## <a name="requirements"></a>需求

此介面的定義可從 IDL 或C++，如下所示。

|定義類型|檔案|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h （也包含在 ATLBase.h）|

## <a name="see-also"></a>另請參閱

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
