---
title: CKeyColumns、 CKeyColumnInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- m_szTableSchema
- m_szConstraintCatalog
- m_nColumnPropID
- ORDINAL_POSITION
- m_nOrdinalPosition
- COLUMN_GUID
- CKeyColumnInfo
- CONSTRAINT_NAME
- m_szColumnName
- m_szTableCatalog
- m_szConstraintSchema
- COLUMN_PROPID
- m_guidColumn
- CKeyColumns
- m_szTableName
- CONSTRAINT_CATALOG
- CONSTRAINT_SCHEMA
- m_szConstraintName
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_PROPID
- ORDINAL_POSITION
- m_szConstraintCatalog
- CONSTRAINT_CATALOG
- m_szTableSchema
- TABLE_CATALOG
- CKeyColumnInfo parameter class
- TABLE_NAME
- CONSTRAINT_NAME
- m_nOrdinalPosition
- m_nColumnPropID
- CONSTRAINT_SCHEMA
- TABLE_SCHEMA
- m_szColumnName
- COLUMN_NAME
- m_szTableCatalog
- m_szConstraintName
- CKeyColumns typedef class
- m_szTableName
- m_szConstraintSchema
- COLUMN_GUID
- m_guidColumn
ms.assetid: 40525a4f-a9cf-4e9f-886d-8a6ddd18a3d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 039af3414714b39b4ac1e26dbdb7557e4796a68f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ckeycolumns-ckeycolumninfo"></a>CKeyColumns、CKeyColumnInfo
呼叫 typedef 類別**CKeyColumns**來實作其參數類別**CKeyColumnInfo**。  
  
## <a name="remarks"></a>備註  
 請參閱[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)如需使用 typedef 類別的詳細資訊。  
  
 這個類別會識別定義的資料行，在目錄中，條件約束做為索引鍵所指定的使用者。  
  
 下表列出類別資料成員和其相對應的 OLE DB 資料行。 請參閱[KEY_COLUMN_USAGE 資料列集](https://msdn.microsoft.com/en-us/library/ms712990.aspx)中*OLE DB 程式設計人員參考*如需有關結構描述和資料行。  
  
|資料成員|OLE DB 資料行|  
|------------------|--------------------|  
|m_szConstraintCatalog|CONSTRAINT_CATALOG|  
|m_szConstraintSchema|CONSTRAINT_SCHEMA|  
|m_szConstraintName|CONSTRAINT_NAME|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
|m_nOrdinalPosition|ORDINAL_POSITION|  
  
## <a name="requirements"></a>需求  
 **標頭：** atldbsch.h  
  
## <a name="see-also"></a>另請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)