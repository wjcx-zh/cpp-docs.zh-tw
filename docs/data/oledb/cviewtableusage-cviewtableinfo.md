---
title: CViewTableUsage、 CViewTableInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- m_szTableSchema
- m_szCatalog
- CViewTableInfo
- m_szTableCatalog
- m_szSchema
- m_szTableName
- m_szName
- CViewTableUsage
dev_langs:
- C++
helpviewer_keywords:
- CViewTableInfo parameter class
- CViewTableUsage typedef class
- m_szSchema
- m_szTableSchema
- TABLE_CATALOG
- m_szCatalog
- TABLE_NAME
- TABLE_SCHEMA
- m_szName
- m_szTableCatalog
- m_szTableName
ms.assetid: 10b74f2a-8010-4f97-acc2-ffce07349981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b66c159e2825884ef59fbfb278b5eddd99d38c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100560"
---
# <a name="cviewtableusage-cviewtableinfo"></a>CViewTableUsage、CViewTableInfo
呼叫 typedef 類別**CViewTableUsage**來實作其參數類別**CViewTableInfo**。  
  
## <a name="remarks"></a>備註  
 請參閱[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)如需使用 typedef 類別的詳細資訊。  
  
 這個類別會識別檢視定義的資料表，在目錄中，指定使用者可存取。  
  
 下表列出類別資料成員和其相對應的 OLE DB 資料行。 請參閱[VIEW_TABLE_USAGE 資料列集](https://msdn.microsoft.com/en-us/library/ms719727.aspx)中*OLE DB 程式設計人員參考*如需有關結構描述和資料行。  
  
|資料成員|OLE DB 資料行|  
|------------------|--------------------|  
|m_szCatalog|VIEW_CATALOG|  
|m_szSchema|VIEW_SCHEMA|  
|m_szName|VIEW_NAME|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
  
## <a name="requirements"></a>需求  
 **標頭：** atldbsch.h  
  
## <a name="see-also"></a>另請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)