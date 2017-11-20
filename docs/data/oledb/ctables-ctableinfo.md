---
title: "CTables、 CTableInfo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szCatalog
- TABLE_SCHEMA
- CTables
- TABLE_NAME
- TABLE_CATALOG
- CTableInfo
- m_guidTable
- m_szType
- m_szSchema
- m_szName
- TABLE_GUID
dev_langs: C++
helpviewer_keywords:
- DESCRIPTION class data member
- m_szSchema
- TABLE_CATALOG
- m_szType
- m_szCatalog
- TABLE_NAME
- TABLE_SCHEMA
- TABLE_GUID
- m_szName
- m_szDescription
- CTables typedef class
- m_guidTable
- CTableInfo parameter class
ms.assetid: 57670f1b-ba99-43b0-b406-4c75b44f14f6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bb693d549420d0fac28e2952ea96789d8d23989
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ctables-ctableinfo"></a>CTables、CTableInfo
呼叫 typedef 類別**CTables**來實作其參數類別**CTableInfo**。  
  
## <a name="remarks"></a>備註  
 請參閱[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)如需使用 typedef 類別的詳細資訊。  
  
 這個類別會識別在資料表上，定義在目錄中，可用來或給定使用者所授與的權限。  
  
 下表列出類別資料成員和其相對應的 OLE DB 資料行。 請參閱[TABLES 資料列集](https://msdn.microsoft.com/en-us/library/ms716980.aspx)中*OLE DB 程式設計人員參考*如需有關結構描述和資料行。  
  
|資料成員|OLE DB 資料行|  
|------------------|--------------------|  
|m_szCatalog|TABLE_CATALOG|  
|m_szSchema|TABLE_SCHEMA|  
|m_szName|TABLE_NAME|  
|m_szType|TABLE_TYPE|  
|m_guidTable|TABLE_GUID|  
|m_szDescription|DESCRIPTION|  
  
## <a name="requirements"></a>需求  
 **標頭：** atldbsch.h  
  
## <a name="see-also"></a>另請參閱  
 [CRestrictions 類別](../../data/oledb/crestrictions-class.md)