---
title: IDocHostUIHandler調度介面
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: b7072b80b738aa12635427a2604b38fb3585b452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329716"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandler調度介面

微軟 HTML 解析和呈現引擎的介面。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

> [!NOTE]
> 下表中的連結指向[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))介面成員的 INet SDK 參考主題。 `IDocHostUIHandlerDispatch`具有與 的功能相同`IDocUIHostHandler`的 功能,區別在`IDocHostUIHandlerDispatch`於是異`IDocUIHostHandler`介面,而 是自定義介面。

|||
|-|-|
|[開啟無模式](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|從[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)的 MSHTML 來執行呼叫:開啟無模式 。 MSHTML 顯示模式 UI 時也調用。|
|[篩選器資料物件](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|MSHTML 呼叫主機以允許主機替換 MSHTML 的數據物件。|
|[取得目標](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|MSHTML 呼叫時,它被用作放置目標,以允許主機提供替代[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)。|
|[取得外部](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|MSHTML 呼叫以獲取主機的 IDispatch 介面。|
|[取得Hostinfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|檢索 MSHTML 主機的 UI 功能。|
|[取得選項關鍵路徑](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|返回 MSHTML 儲存使用者首選項的註冊表項。|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|當 MSHTML 刪除其功能表和工具列時呼叫。|
|[OnDocWindow 啟用](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|從[IOleInPlace 活動物件的](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)MSHTML 來執行:onDocWindow 啟動 。|
|[在框架視窗啟動](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|從[IOleInPlace 活動物件的](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)MSHTML 實現調用:在FrameWindow啟動上。|
|[調整邊框的大小](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|從[IOleInPlace 作用物件的](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)MSHTML 來呼叫:調整邊框 。|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|從 MSHTML 呼叫以顯示上下文選單。|
|[顯示 UI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|允許主機替換 MSHTML 功能表和工具列。|
|[翻譯加速器](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|當[IOleInPlace 活動物件::翻譯加速器](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)或[IOleControlSite::調用翻譯加速器](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)時,MSHTML 呼叫。|
|[翻譯網址](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|MSHTML 呼叫以允許主機有機會修改要載入的 URL。|
|[更新 UI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|通知主機命令狀態已變更。|

## <a name="remarks"></a>備註

主機可以通過實現此介面來取代 Microsoft HTML 解析和呈現引擎 (MSHTML) 使用的功能表、工具列和上下文選單。

## <a name="requirements"></a>需求

此介面的定義可作為 IDL 或C++,如下所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (也包含在 ATLBase.h 中)|

## <a name="see-also"></a>另請參閱

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
