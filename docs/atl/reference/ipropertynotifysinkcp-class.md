---
title: "IPropertyNotifySinkCP 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
caps.latest.revision: 21
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: feff2467d6d72e9d0a9186dc269f48eb26cbfee2
ms.lasthandoff: 03/17/2017

---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 類別
這個類別會公開[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)介面做為輸出介面上可連接物件。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
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
 類別可管理的連接點和其接收器之間的連線。 預設值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，這允許無限制的連線。 您也可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，以指定固定的數目的連線。  
  
## <a name="remarks"></a>備註  
 `IPropertyNotifySinkCP`繼承其基底類別，透過所有方法[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)。  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)介面允許接收物件來接收有關屬性變更通知。 類別`IPropertyNotifySinkCP`做為輸出介面可連接物件上公開此介面。 用戶端必須實作`IPropertyNotifySink`接收上的方法。  
  
 衍生您的類別，從`IPropertyNotifySinkCP`當您想要建立連接點，表示`IPropertyNotifySink`介面。  
  
 如需在 ATL 中使用的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
## <a name="see-also"></a>另請參閱  
 [IConnectionPointImpl 類別](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl 類別](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

