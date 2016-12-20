---
title: "往返簡單資料列集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "存取子 [C++], 資料列集"
  - "資料存取 [C++], 資料列集"
  - "OLE DB 消費者 [C++], 資料庫屬性"
  - "資料列集 [C++], 存取"
  - "簡單資料列集"
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 往返簡單資料列集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例顯示一種不包含命令的快速且容易執行的資料庫存取方式。  下列位於 ATL 專案中的消費者程式碼，會使用 Microsoft OLE DB Provider for ODBC，自 Microsoft Access 資料庫中，擷取名為 *Artists* 的資料表資料錄。  程式碼會根據使用者資料錄類別 `CArtists` 的存取子建立 [CTable](../../data/oledb/ctable-class.md) 資料表物件。  這個物件可開啟連接、在連接上開啟一個工作階段，並在該工作階段上開啟資料表。  
  
```  
#include <atldbcli.h>  
  
CDataSource connection;  
CSession session;  
CTable<CAccessor<CArtists> > artists;  
  
// Open the connection, session, and table, specifying authentication   
// using Windows NT integrated security. Hard-coding a password is a major  
// security weakness.  
connection.Open(CLSID_MSDASQL, "NWind", NULL, NULL,   
DBPROP_AUTH_INTEGRATED);  
session.Open(connection);  
artists.Open(session, "Artists");  
  
// Get data from the rowset  
while (artists.MoveNext() == S_OK)  
{  
   cout << artists.m_szFirstName;  
   cout << artists.m_szLastName;  
}  
```  
  
 `CArtists` 使用者資料錄看起來像是這樣：  
  
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
```  
  
## 請參閱  
 [使用 OLE DB 消費者樣板](../../data/oledb/working-with-ole-db-consumer-templates.md)