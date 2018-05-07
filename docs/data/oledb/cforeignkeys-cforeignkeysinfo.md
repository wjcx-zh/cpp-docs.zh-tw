---
title: CForeignKeys、 CForeignKeysInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- m_nOrdinal
- m_szPKColumnName
- FK_TABLE_NAME
- m_guidFKColumn
- FK_COLUMN_NAME
- m_guidPKColumn
- DELETE_RULE
- m_szPKTableSchema
- FK_COLUMN_PROPID
- m_nFKColumnPropID
- m_szFKTableCatalog
- CForeignKeysInfo
- FK_TABLE_SCHEMA
- m_szPKTableCatalog
- m_szDeleteRule
- m_szUpdateRule
- m_szPKTableName
- m_szFKTableSchema
- ORDINAL
- m_nPKColumnPropID
- m_szFKColumnName
- FK_TABLE_CATALOG
- FK_COLUMN_GUID
- m_szFKTableName
- CForeignKeys
dev_langs:
- C++
helpviewer_keywords:
- m_szPKTableCatalog
- FK_COLUMN_GUID
- m_szPKColumnName
- m_szFKTableName
- ORDINAL data member
- m_nPKColumnPropID
- m_szDeleteRule
- DELETE_RULE
- m_guidFKColumn
- FK_COLUMN_PROPID
- m_szPKTableSchema
- m_szFKTableCatalog
- CForeignKeysInfo parameter class
- m_szFKTableSchema
- FK_TABLE_SCHEMA
- FK_COLUMN_NAME
- m_szUpdateRule
- m_szFKColumnName
- FK_TABLE_CATALOG
- m_nOrdinal
- m_szPKTableName
- CForeignKeys typedef class
- m_nFKColumnPropID
- m_guidPKColumn
- FK_TABLE_NAME
ms.assetid: 1c401a4a-0827-4255-9214-bc893e1cd79d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e15b4a855375161f15ff9fa872a700f93b817a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cforeignkeys-cforeignkeysinfo"></a>CForeignKeys、CForeignKeysInfo
呼叫 typedef 類別**CForeignKeys**來實作其參數類別**CForeignKeysInfo**。  
  
## <a name="remarks"></a>備註  
 請參閱[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)如需使用 typedef 類別的詳細資訊。  
  
 這個類別會識別在目錄中由指定使用者定義的外部索引鍵資料行。  
  
 下表列出類別資料成員和其相對應的 OLE DB 資料行。 請參閱[FOREIGN_KEYS 資料列集](https://msdn.microsoft.com/en-us/library/ms711276.aspx)中*OLE DB 程式設計人員參考*如需有關結構描述和資料行。  
  
|資料成員|OLE DB 資料行|  
|------------------|--------------------|  
|m_szPKTableCatalog|PK_TABLE_CATALOG|  
|m_szPKTableSchema|PK_TABLE_SCHEMA|  
|m_szPKTableName|PK_TABLE_NAME|  
|m_szPKColumnName|PK_COLUMN_NAME|  
|m_guidPKColumn|PK_COLUMN_GUID|  
|m_nPKColumnPropID|PK_COLUMN_PROPID|  
|m_szFKTableCatalog|FK_TABLE_CATALOG|  
|m_szFKTableSchema|FK_TABLE_SCHEMA|  
|m_szFKTableName|FK_TABLE_NAME|  
|m_szFKColumnName|FK_COLUMN_NAME|  
|m_guidFKColumn|FK_COLUMN_GUID|  
|m_nFKColumnPropID|FK_COLUMN_PROPID|  
|m_nOrdinal|序數|  
|m_szUpdateRule|UPDATE_RULE|  
|m_szDeleteRule|DELETE_RULE|  
  
## <a name="requirements"></a>需求  
 **標頭：** atldbsch.h  
  
## <a name="see-also"></a>另請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)