---
title: IRowsetCreatorImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0492994193130ffa6a547691490b4da1ae557c8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102133"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl 類別
執行相同的函式做為`IObjectWithSite`但也可讓 OLE DB 屬性**DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**。  
  
## <a name="syntax"></a>語法

```cpp
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
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)