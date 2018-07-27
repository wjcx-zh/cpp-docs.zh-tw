---
title: IGetDataSourceImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 558578a82f1906d7481abebc5e1f1719b1983724
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269933"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl 類別
提供實作[IGetDataSource](https://msdn.microsoft.com/library/ms709721.aspx)物件。  
  
## <a name="syntax"></a>語法

```cpp
template <class T>  
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`IGetDataSourceImpl`。  

## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetDataSource](#getdatasource)|在 建立工作階段資料來源物件上傳回的介面指標。|  
  
## <a name="remarks"></a>備註  
 這是必要的介面上的工作階段取得的資料來源物件的介面指標時。  

## <a name="getdatasource"></a> Igetdatasourceimpl:: Getdatasource
在 建立工作階段資料來源物件上傳回的介面指標。  
  
### <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IGetDataSource::GetDataSource](https://msdn.microsoft.com/library/ms725443.aspx)中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 如果您需要存取資料來源物件中的屬性很有用。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
