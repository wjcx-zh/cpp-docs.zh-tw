---
title: "IQuickActivateImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
dev_langs:
- C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4f6b75da64efa12e43fa160c57da4291acae03ca
ms.lasthandoff: 02/24/2017

---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl 類別
這個類別會結合成單一呼叫容器的控制項初始化。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IQuickActivateImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|擷取目前的顯示大小執行控制項。|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|執行快速初始化的控制項正在載入。|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|通知控制項的容器已指派給它的顯示空間。|  
  
## <a name="remarks"></a>備註  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146)介面可幫助避免延遲載入控制項結合的單一呼叫中初始化時的容器。 `QuickActivate`方法可讓容器將指標傳遞至[QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630)需要控制項保存所有的介面指標的結構。 在傳回時，控制權會傳遞回指標[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)保留它自己的介面，容器會使用指標的結構。 類別`IQuickActivateImpl`提供的預設實作**IQuickActivate**並實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent  
 擷取目前的顯示大小執行控制項。  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>備註  
 大小適用於完整呈現控制項，並指定以 himetric 為單位。  
  
 請參閱[IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="quickactivate"></a>IQuickActivateImpl::QuickActivate  
 執行快速初始化的控制項正在載入。  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>備註  
 此結構包含控制項和一些環境屬性的值所需的介面指標。 傳回時，控制權會傳遞指標[QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721)結構，其中包含容器需要，自己介面和額外的狀態資訊的指標。  
  
 請參閱[IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent  
 通知控制項的容器已指派給它的顯示空間。  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>備註  
 以 himetric 為單位指定大小。  
  
 請參閱[IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

