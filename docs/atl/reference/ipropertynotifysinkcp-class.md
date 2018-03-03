---
title: "IPropertyNotifySinkCP 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa15ef6706010154151c696eca320d464cdfee6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 類別
這個類別會公開[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)介面做為可連接物件上的輸出介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPropertyNotifySinkCP`。  
  
 `CDV`  
 類別可管理的連接點和其接收器之間的連線。 預設值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，可讓無限制的連線。 您也可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，指定固定的數目的連線。  
  
## <a name="remarks"></a>備註  
 `IPropertyNotifySinkCP`繼承其基底類別，透過的所有方法[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)。  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)介面可讓接收有關屬性變更通知接收物件。 類別`IPropertyNotifySinkCP`此介面公開為可連接物件上的輸出介面。 用戶端必須實作`IPropertyNotifySink`接收上的方法。  
  
 衍生您的類別從`IPropertyNotifySinkCP`當您想要建立的連接點，代表`IPropertyNotifySink`介面。  
  
 如需 ATL 中使用的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
## <a name="see-also"></a>請參閱  
 [IConnectionPointImpl 類別](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl 類別](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
