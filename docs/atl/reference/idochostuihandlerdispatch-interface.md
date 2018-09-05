---
title: IDocHostUIHandlerDispatch 介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs:
- C++
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58029305ead376217b589c6dd05c1dc660cd5749
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758640"
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
>  下表中的連結是成員 INet SDK 參考主題[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)介面。 `IDocHostUIHandlerDispatch` 具有相同的功能`IDocUIHostHandler`，差異在於使用`IDocHostUIHandlerDispatch`是分配介面，而`IDocUIHostHandler`是一種自訂介面。

|||
|-|-|
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|從 MSHTML 實作的呼叫[IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)。 也稱為 MSHTML 顯示強制回應 UI 時。|
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|若要允許主機替換 MSHTML 的資料物件的 MSHTML 主機上呼叫。|
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|當它用做為置放目標，讓主機提供另一個呼叫 MSHTML [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)。|
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|取得主機的 IDispatch 介面 MSHTML 呼叫。|
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|擷取 MSHTML 主機的 UI 功能。|
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|傳回在其下 MSHTML 儲存使用者喜好設定的登錄機碼。|
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|MSHTML 移除其功能表與工具列時呼叫。|
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Ondocwindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)。|
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Onframewindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)。|
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Resizeborder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)。|
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|從顯示的內容功能表的 MSHTML 呼叫。|
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|允許主機替換 MSHTML 功能表和工具列。|
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|由 MSHTML 呼叫，當[:: Translateaccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)或是[iolecontrolsite:: Translateaccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)呼叫。|
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|呼叫 MSHTML，讓主機有機會修改要載入的 URL。|
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|通知主機命令狀態已變更。|

## <a name="remarks"></a>備註

主機可以取代功能表、 工具列和由 Microsoft HTML 剖析和轉譯引擎 (MSHTML) 來實作這個介面的操作功能表。

## <a name="requirements"></a>需求

此介面的定義做為 IDL 或 c + +，如下所示。

|定義類型|檔案|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h （也包含在 ATLBase.h）|

## <a name="see-also"></a>另請參閱

[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)

