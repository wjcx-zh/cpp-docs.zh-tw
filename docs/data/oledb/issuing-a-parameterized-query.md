---
title: "發出參數型的查詢 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: parameter queries, running using CCommand class
ms.assetid: aedb0fce-52a4-4c97-a5c9-b2114be6c3b0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e016b6bb8c37fe24d9f1929f19904f17592e6f3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="issuing-a-parameterized-query"></a>發出參數型查詢
下列範例會發出簡單參數化的查詢，以便從 Microsoft Access 資料庫中的資料表擷取時間欄位 （亦即超過 30） 的記錄。 若要支援此參數，使用者資料錄必須擁有其他的對應。 下列程式碼，在 ATL 專案中，使用`CCommand`類別而不是`CTable`中前一個範例中，使用類別[往返簡單資料列集](../../data/oledb/traversing-a-simple-rowset.md)。  
  
```  
#include <atldbcli.h>  
  
CDataSource connection;  
CSession session;  
CCommand<CAccessor<CArtists> > artists;  
  
// Open the connection, session, and table, specifying authentication   
// using Windows NT integrated security. Hard-coding a password is a major   
// security weakness.  
connection.Open(CLSID_MSDASQL, "NWind", NULL, NULL,   
DBPROP_AUTH_INTEGRATED);  
session.Open(connection);  
  
// Set the parameter for the query  
artists.m_nAge = 30;  
artists.Open(session, "select * from artists where age > ?");  
  
// Get data from the rowset  
while (artists.MoveNext() == S_OK)  
{  
   cout << artists.m_szFirstName;  
   cout << artists.m_szLastName;  
}  
```  
  
 使用者資料錄`CArtists`，看起來像這樣：  
  
```  
class CArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_COLUMN_MAP(CArtists)  
   COLUMN_ENTRY(1, m_szFirstName)  
   COLUMN_ENTRY(2, m_szLastName)  
   COLUMN_ENTRY(3, m_nAge)  
END_COLUMN_MAP()  
  
// Parameter binding map  
BEGIN_PARAM_MAP(CArtists)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_nAge)  
END_PARAM_MAP()  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)