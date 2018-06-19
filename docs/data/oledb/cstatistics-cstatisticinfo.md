---
title: CStatistics、 CStatisticInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CStatistics
- m_szTableSchema
- CStatisticInfo
- m_szTableCatalog
- m_nCardinality
- m_szTableName
dev_langs:
- C++
helpviewer_keywords:
- m_nCardinality
- m_szTableSchema
- TABLE_CATALOG
- TABLE_NAME
- TABLE_SCHEMA
- CStatistics typedef class
- m_szTableCatalog
- m_szTableName
- CStatisticInfo parameter class
ms.assetid: 5822231c-6963-44a6-ae2f-29aca76e1600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ad61624077eb1c02337fdd4737853522533a8a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101493"
---
# <a name="cstatistics-cstatisticinfo"></a>CStatistics、CStatisticInfo
呼叫 typedef 類別**CStatistics**來實作其參數類別**CStatisticInfo**。  
  
## <a name="remarks"></a>備註  
 請參閱[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)如需使用 typedef 類別的詳細資訊。  
  
 這個類別會識別定義的統計資料，在目錄中，指定使用者所擁有。  
  
 下表列出類別資料成員和其相對應的 OLE DB 資料行。 請參閱[統計資料資料列集](https://msdn.microsoft.com/en-us/library/ms715957.aspx)中*OLE DB 程式設計人員參考*如需有關結構描述和資料行。  
  
|資料成員|OLE DB 資料行|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_nCardinality|CARDINALITY|  
  
## <a name="requirements"></a>需求  
 **標頭：** atldbsch.h  
  
## <a name="see-also"></a>另請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)