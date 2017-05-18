---
title: "IPropertyPage2Impl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 43680d12febbd94137009f66242198129d4b3630
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl 類別
這個類別會實作**IUnknown**和繼承的預設實作[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPropertyPage2Impl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IPropertyPage2Impl::EditProperty](#editproperty)|指定哪一個屬性控制項來接收焦點時就會啟動 [屬性] 頁面。 ATL 實作會傳回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>備註  
 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996)介面會擴充[IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)加`EditProperty`方法。 這個方法可讓用戶端在屬性頁物件中選取特定的屬性。  
  
 類別`IPropertyPage2Impl`只會傳回**E_NOTIMPL**的**IPropertyPage2::EditProperty**。 不過，它會繼承的預設實作[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)並實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 當您建立屬性頁時，您的類別通常衍生自`IPropertyPageImpl`。 若要提供額外的支援**IPropertyPage2**，修改您的類別定義，並覆寫`EditProperty`方法。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="editproperty"></a>IPropertyPage2Impl::EditProperty  
 指定哪一個屬性控制項來接收焦點時就會啟動 [屬性] 頁面。  
  
```
HRESULT EditProperty(DISPID dispID);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage2::EditProperty](http://msdn.microsoft.com/library/windows/desktop/ms690353)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [IPerPropertyBrowsingImpl 類別](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl 類別](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

