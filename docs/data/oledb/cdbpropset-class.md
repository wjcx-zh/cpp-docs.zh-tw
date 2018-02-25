---
title: "CDBPropSet 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropSet class
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 716b0785ba4f785063709d989eb95c5c4f390f4a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cdbpropset-class"></a>CDBPropSet 類別
繼承自**DBPROPSET**結構，並將建構函式會初始化索引鍵欄位，以及`AddProperty`存取方法。  
  
## <a name="syntax"></a>語法

```cpp
class CDBPropSet : public tagDBPROPSET  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddProperty](../../data/oledb/cdbpropset-addproperty.md)|新增屬性至屬性集。|  
|[CDBPropSet](../../data/oledb/cdbpropset-cdbpropset.md)|建構函式。|  
|[SetGUID](../../data/oledb/cdbpropset-setguid.md)|設定**guidPropertySet**欄位**DBPROPSET**結構。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator =](../../data/oledb/cdbpropset-operator-equal.md)|將指派設定為另一個屬性的內容。|  
  
## <a name="remarks"></a>備註  
 OLE DB 提供者與取用者使用**DBPROPSET**結構，以傳遞的陣列`DBPROP`結構。 每個`DBPROP`結構代表您可以將單一屬性。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)   
 [DBPROPSET 結構](https://msdn.microsoft.com/en-us/library/ms714367.aspx)   
 [DBPROP 結構](https://msdn.microsoft.com/en-us/library/ms717970.aspx)