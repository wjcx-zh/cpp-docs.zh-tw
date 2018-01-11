---
title: "CUtlProps 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CUtlProps
dev_langs: C++
helpviewer_keywords: CUtlProps class
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75e92f48729d0aae9f85cc7b7c5c97e4778f96a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cutlprops-class"></a>CUtlProps 類別
會實作各種不同的 OLE DB 屬性的介面屬性 (例如， `IDBProperties`， `IDBProperties`，和`IRowsetInfo`)。  
  
## <a name="syntax"></a>語法  
  
```  
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別，其中包含`BEGIN_PROPSET_MAP`。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|從屬性集合取得的屬性。|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|用來驗證之前設定屬性的值。|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|當取用者物件建立介面上呼叫方法來處理要求的選擇性的介面。|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|設定屬性，以處理鏈結的內容之後呼叫。|  
|[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)|在屬性集中設定的屬性。|  
  
## <a name="remarks"></a>備註  
 此類別大部分是實作詳細資料。  
  
 `CUtlProps`在內部設定屬性包含兩個成員： [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)和[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)。  
  
 如需有關屬性的集合對應中使用的巨集的詳細資訊，請參閱[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)和[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)