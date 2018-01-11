---
title: "IOpenRowsetImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IOpenRowsetImpl
dev_langs: C++
helpviewer_keywords: IOpenRowsetImpl class
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5df3b7944eec73a8a261ab4e291d3be9c5d34de2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl 類別
提供實作`IOpenRowset`介面。  
  
## <a name="syntax"></a>語法  
  
```  
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### <a name="parameters"></a>參數  
 `SessionClass`  
 您的類別，衍生自`IOpenRowsetImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CreateRowset](../../data/oledb/iopenrowsetimpl-createrowset.md)|建立資料列集物件。 並非由使用者直接呼叫。|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|開啟並傳回包含單一基底資料表或索引的所有資料列的資料列集。 （不在 ATLDB。H)|  
  
## <a name="remarks"></a>備註  
 [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx)介面是必要的工作階段物件。 它會開啟，並傳回包含單一基底資料表或索引的所有資料列的資料列集。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)