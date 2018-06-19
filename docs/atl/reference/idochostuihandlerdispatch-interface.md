---
title: IDocHostUIHandlerDispatch 介面 |Microsoft 文件
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
ms.openlocfilehash: 07d6d861bfa4a41d7d9ee6697dd72cba0da2ceda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364241"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 介面
要剖析的 Microsoft HTML 和轉譯引擎的介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
interface IDocHostUIHandlerDispatch : IDispatch
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
> [!NOTE]
>  下表中的連結是 INet SDK 參考主題的成員[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)介面。 `IDocHostUIHandlerDispatch` 具有相同的功能為**IDocUIHostHandler**，兩者的差異在於，`IDocHostUIHandlerDispatch`是 dispinterface 而**IDocUIHostHandler**是自訂的介面。  
  
|||  
|-|-|  
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|從 MSHTML 實作的呼叫[IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115)。 也稱為 MSHTML 顯示強制回應 UI 時。|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|允許主機替換 MSHTML 的資料物件的 MSHTML 主機上呼叫。|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|它正做為置放目標，讓主機提供另一個時，由 MSHTML 呼叫[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|若要取得主機的 IDispatch 介面 MSHTML 呼叫。|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|擷取 MSHTML 主機的 UI 功能。|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|傳回在其下 MSHTML 儲存使用者喜好設定的登錄機碼。|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|MSHTML 移除其功能表與工具列時呼叫。|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Ondocwindowactivate](http://msdn.microsoft.com/library/windows/desktop/ms687281)。|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Onframewindowactivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)。|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|從 MSHTML 實作的呼叫[ioleinplaceactiveobject:: Resizeborder](http://msdn.microsoft.com/library/windows/desktop/ms680053)。|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|從顯示操作功能表 MSHTML 呼叫。|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|允許主機替換 MSHTML 功能表和工具列。|  
|[Translateaccelerator 呼叫](https://msdn.microsoft.com/library/aa753266.aspx)|由 MSHTML 呼叫時[:: Translateaccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360)或[iolecontrolsite:: Translateaccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756)呼叫。|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|呼叫 mshtml 呼叫，讓主機有機會修改要載入的 URL。|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|通知主機命令狀態已變更。|  
  
## <a name="remarks"></a>備註  
 主機可以取代功能表、 工具列和操作功能表和所使用之剖析 Microsoft HTML (MSHTML) 的轉譯引擎實作這個介面。  
  
## <a name="requirements"></a>需求  
 此介面的定義可做為 IDL 或 c + +，如下所示。  
  
|定義類型|檔案|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h （也包含在 ATLBase.h）|  
  
## <a name="see-also"></a>另請參閱  
 [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)









