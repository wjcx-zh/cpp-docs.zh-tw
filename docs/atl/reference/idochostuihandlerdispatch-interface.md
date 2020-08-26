---
title: IDocHostUIHandlerDispatch 介面
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 4d80934a5768eda917c90345ddeeff017edf0eae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835437"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 介面

Microsoft HTML 剖析和轉譯引擎的介面。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

> [!NOTE]
> 下表中的連結是 [IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) 介面成員的 INet SDK 參考主題。 `IDocHostUIHandlerDispatch` 具有與相同的功能 `IDocUIHostHandler` ，差別在於它是一個介面介面， `IDocHostUIHandlerDispatch` 而 `IDocUIHostHandler` 是自訂介面。

|名稱|描述|
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|從 [IOleInPlaceActiveObject：： EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)的 MSHTML 執行呼叫。 也會在 MSHTML 顯示強制回應 UI 時呼叫。|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|由 MSHTML 在主機上呼叫，以允許主機取代 MSHTML 的資料物件。|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|當 MSHTML 用作為放置目標，以允許主機提供替代 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)時呼叫。|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|由 MSHTML 呼叫以取得主機的 IDispatch 介面。|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|抓取 MSHTML 主機的 UI 功能。|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|傳回 MSHTML 用來儲存使用者喜好設定的登錄機碼。|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|當 MSHTML 移除其功能表和工具列時呼叫。|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|從 [IOleInPlaceActiveObject：： OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)的 MSHTML 執行呼叫。|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|從 [IOleInPlaceActiveObject：： OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)的 MSHTML 執行呼叫。|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|從 [IOleInPlaceActiveObject：： ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)的 MSHTML 執行呼叫。|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|從 MSHTML 呼叫以顯示快顯功能表。|
|[>showui 或](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|允許主機取代 MSHTML 功能表和工具列。|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|呼叫 [IOleInPlaceActiveObject：： TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) 或 [>iolecontrolsite：： TRANSLATEACCELERATOR](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) 時由 MSHTML 呼叫。|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|由 MSHTML 呼叫，讓主機有機會修改要載入的 URL。|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|通知主機命令狀態已變更。|

## <a name="remarks"></a>備註

主機可以藉由執行這個介面，取代 Microsoft HTML 剖析和轉譯引擎 (MSHTML) 所使用的功能表、工具列和快顯功能表。

## <a name="requirements"></a>規格需求

此介面的定義可作為 IDL 或 c + +，如下所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|ATLIFace .idl|
|C++|ATLIFace 也會包含在 Atlbase.h 中 () |

## <a name="see-also"></a>另請參閱

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
