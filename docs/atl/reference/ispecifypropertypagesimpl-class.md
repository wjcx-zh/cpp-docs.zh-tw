---
title: "ISpecifyPropertyPagesImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs: C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 716e3ba5d48d39cd189da8d92cca694f09508e42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl 類別
這個類別會實作**IUnknown**和提供的預設實作[ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217)介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`ISpecifyPropertyPagesImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|填滿計算 UUID 陣列值。 每個 UUID 會對應至其中一個可以顯示物件的屬性工作表中的屬性頁 CLSID。|  
  
## <a name="remarks"></a>備註  
 [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217)介面可讓用戶端取得的物件所支援之屬性頁 Clsid 的清單。 類別`ISpecifyPropertyPagesImpl`提供此介面的預設實作，並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
> [!NOTE]
>  不會公開**ISpecifyPropertyPages**介面，如果您的物件不支援屬性頁。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages  
 填入陣列[CAUUID](http://msdn.microsoft.com/library/windows/desktop/ms680048)結構具有可以顯示物件的屬性工作表中的屬性頁的 Clsid。  
  
```
STDMETHOD(GetPages)(CAUUID* pPages);
```  
  
### <a name="remarks"></a>備註  
 ATL 會擷取每個 CLSID 使用物件的屬性對應。  
  
 請參閱[ISpecifyPropertyPages::GetPages](http://msdn.microsoft.com/library/windows/desktop/ms687276) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [IPropertyPageImpl 類別](../../atl/reference/ipropertypageimpl-class.md)   
 [IPerPropertyBrowsingImpl 類別](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
