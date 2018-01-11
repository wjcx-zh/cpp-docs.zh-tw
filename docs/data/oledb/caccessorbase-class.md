---
title: "CAccessorBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CAccessorBase
dev_langs: C++
helpviewer_keywords: CAccessorBase class
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b7c12430c4e7a6872afd46e72e93a29a3189333
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="caccessorbase-class"></a>CAccessorBase 類別
OLE DB 樣板中的所有存取子是衍生自這個類別。 `CAccessorBase`可讓一個資料列集來管理多個存取子。 它也會提供繫結參數和輸出資料行。  
  
## <a name="syntax"></a>語法  
  
```  
// Replace with syntax  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[關閉](../../data/oledb/caccessorbase-close.md)|關閉存取子。|  
|[GetHAccessor](../../data/oledb/caccessorbase-gethaccessor.md)|擷取存取子控制代碼。|  
|[GetNumAccessors](../../data/oledb/caccessorbase-getnumaccessors.md)|擷取存取子類別建立的數目。|  
|[IsAutoAccessor](../../data/oledb/caccessorbase-isautoaccessor.md)|測試指定的存取子是否 autoaccessor。|  
|[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)|釋放存取子。|  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)