---
title: "IRowsetCreatorImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
dev_langs: C++
helpviewer_keywords: IRowsetCreatorImpl class
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3a1a1c17ad9469ff31b5520ffadb3349f86827ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl 類別
執行相同的函式做為`IObjectWithSite`但也可讓 OLE DB 屬性**DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**。  
  
## <a name="syntax"></a>語法  
  
```  
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別衍生自**IRowsetCreator**。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[SetSite](../../data/oledb/irowsetcreatorimpl-setsite.md)|設定站台，其中包含資料列集物件。|  
  
## <a name="remarks"></a>備註  
 此類別繼承自[IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765)和覆寫[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。 當提供者命令或工作階段物件會建立一個資料列集時，它會呼叫`QueryInterface`尋找資料列集物件上`IObjectWithSite`和呼叫`SetSite`傳遞資料列集物件**IUnkown**為站台介面的介面。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)