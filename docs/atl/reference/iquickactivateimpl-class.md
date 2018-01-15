---
title: "IQuickActivateImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
dev_langs: C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c6f5bc1798bc8ec40fb6f6d9d22f48c06b19745
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 類別
這個類別會結合至單一呼叫容器的控制項初始化。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IQuickActivateImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|擷取目前的顯示大小執行控制項。|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|執行快速初始化的控制項正在載入。|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|通知控制項的容器已指派給它的顯示空間。|  
  
## <a name="remarks"></a>備註  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146)介面可幫助避免延遲載入結合在單一呼叫中的初始化控制項時的容器。 `QuickActivate`方法可讓容器傳遞至指標[QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630)需要的結構，可控制保存的所有介面指標。 在傳回時，控制權會傳遞回指標[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)結構，可保存其自己的介面，容器所使用的指標。 類別`IQuickActivateImpl`提供的預設實作**IQuickActivate**並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent  
 擷取目前的顯示大小執行控制項。  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>備註  
 大小適用於完整呈現控制項，並指定以 himetric 為單位。  
  
 請參閱[IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) Windows SDK 中。  
  
##  <a name="quickactivate"></a>IQuickActivateImpl::QuickActivate  
 執行快速初始化的控制項正在載入。  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>備註  
 此結構包含控制項和一些環境屬性的值所需的介面指標。 傳回時，控制權會傳遞指標[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)結構，其中包含容器需要，自己介面和額外的狀態資訊的指標。  
  
 請參閱[IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) Windows SDK 中。  
  
##  <a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent  
 通知控制項的容器已指派給它的顯示空間。  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>備註  
 大小是以 himetric 為單位來指定。  
  
 請參閱[IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
