---
title: IDocHostUIHandlerDispatch 介面
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: a9e672144160528e6a2fbfe4cb702c4d211ef720
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495913"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 介面

Microsoft HTML 剖析和轉譯引擎的介面。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

> [!NOTE]
>  下表中的連結適用于[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))介面成員的 INet SDK 參考主題。 `IDocHostUIHandlerDispatch`的功能`IDocUIHostHandler`與相同, 差別在於`IDocHostUIHandlerDispatch`它是一個分配介面, 而`IDocUIHostHandler`是自訂介面。

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|從[IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)的 MSHTML 執行呼叫。 當 MSHTML 顯示強制回應 UI 時也會呼叫。|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|由 MSHTML 在主機上呼叫, 以允許主機取代 MSHTML 的資料物件。|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|當 MSHTML 做為放置目標使用, 以允許主機提供替代[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)時, 會呼叫此方法。|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|由 MSHTML 呼叫以取得主機的 IDispatch 介面。|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|抓取 MSHTML 主機的 UI 功能。|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|傳回 MSHTML 用來儲存使用者喜好設定的登錄機碼。|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|當 MSHTML 移除其功能表和工具列時呼叫。|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|從[IOleInPlaceActiveObject:: ondocwindowactivate 呼叫](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)的 MSHTML 執行呼叫。|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|從[IOleInPlaceActiveObject:: onframewindowactivate 呼叫](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)的 MSHTML 執行呼叫。|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|從[IOleInPlaceActiveObject:: resizeborder 呼叫](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)的 MSHTML 執行呼叫。|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|從 MSHTML 呼叫以顯示內容功能表。|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|允許主機取代 MSHTML 功能表和工具列。|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|當呼叫[IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)或[IOleControlSite:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)時, 由 MSHTML 呼叫。|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|由 MSHTML 呼叫, 讓主機有機會修改要載入的 URL。|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|通知主機命令狀態已變更。|

## <a name="remarks"></a>備註

主機可以藉由執行此介面來取代 Microsoft HTML 剖析和轉譯引擎 (MSHTML) 所使用的功能表、工具列和操作功能表。

## <a name="requirements"></a>需求

此介面的定義可做為 IDL 或C++, 如下所示。

|定義類型|檔案|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace (也包含在 Atlbase.h 中)|

## <a name="see-also"></a>另請參閱

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
