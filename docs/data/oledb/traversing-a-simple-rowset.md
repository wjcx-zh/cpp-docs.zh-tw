---
title: 往返簡單資料列集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data access [C++], rowsets
- rowsets [C++], accessing
- simple rowsets
- OLE DB consumers [C++], database attributes
- accessors [C++], rowsets
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9a127b5cd611177c28e6e434b04060edf3bdcb55
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028632"
---
# <a name="traversing-a-simple-rowset"></a>往返簡單資料列集

下列範例顯示不包含命令的快速簡便的資料庫存取。 下列的取用者程式碼，在 ATL 專案中，從呼叫資料表擷取資料錄*演出者*在 Microsoft Access 資料庫中使用 Microsoft OLE DB Provider for ODBC。 程式碼會建立[CTable](../../data/oledb/ctable-class.md)存取子使用的資料表物件會根據使用者記錄類別`CArtists`。 它會開啟連接、 開啟連線時，工作階段並開啟工作階段上的資料表。  
  
```cpp  
#include <atldbcli.h>  
  
CDataSource connection;  
CSession session;  
CTable<CAccessor<CArtists>> artists;  
  
// Open the connection, session, and table, specifying authentication   
// using Windows NT integrated security. Hard-coding a password is a major  
// security weakness.  
connection.Open(CLSID_MSDASQL, "NWind", NULL, NULL, DBPROP_AUTH_INTEGRATED);  

session.Open(connection);  

artists.Open(session, "Artists");  
  
// Get data from the rowset  
while (artists.MoveNext() == S_OK)  
{  
   cout << artists.m_szFirstName;  
   cout << artists.m_szLastName;  
}  
```  
  
使用者資料錄`CArtists`，看起來像這樣：  
  
```cpp  
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
```  
  
## <a name="see-also"></a>另請參閱  

[使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)