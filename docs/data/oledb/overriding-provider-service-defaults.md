---
title: "覆寫提供者服務預設值 | Microsoft Docs"
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
  - "OLE DB 服務 [OLE DB], 覆寫預設"
  - "服務提供者 [OLE DB]"
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 覆寫提供者服務預設值
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供者的 **OLEDB\_SERVICES** 登錄值，將傳回做為資料來源物件的 [DBPROP\_INIT\_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx) 初始化屬性之預設值。  
  
 只要登錄項目存在，提供者的物件就會被彙總，且使用者在初始化之前，可透過設定 **DBPROP\_INIT\_OLEDBSERVICES** 屬性，為已啟用的服務覆寫提供者的預設設定。  若要啟用或停用特定服務，使用者通常都會取得 **DBPROP\_INIT\_OLEDBSERVICES** 屬性的目前值、設定或清除要啟用或停用的特定屬性位元，並重設屬性。  **DBPROP\_INIT\_OLEDBSERVICES** 可直接設定於 OLE DB 內，或在傳給 ADO 或 **IDataInitialize::GetDatasource** 的連接字串內。  下表列出了要啟用\/停用個別服務的對應值。  
  
|啟用的預設服務|DBPROP\_INIT\_OLEDBSERVICES 屬性值|連接字串的數值|  
|-------------|-------------------------------------|-------------|  
|所有服務 \(預設值\)|**DBPROPVAL\_OS\_ENABLEALL**|"OLE DB Services \= \-1;"|  
|Pooling 和 AutoEnlistment 以外的所有服務|**DBPROPVAL\_OS\_ENABLEALL&**<br /><br /> **~DBPROPVAL\_OS\_RESOURCEPOOLING &**<br /><br /> **~DBPROPVAL\_OS\_TXNENLISTMENT**|"OLE DB Services \= \-4;"|  
|Client Cursor 以外的所有服務|**DBPROPVAL\_OS\_ENABLEALL** &<br /><br /> ~**DBPROPVAL\_OS\_CLIENTCURSOR**|"OLE DB Services \= \-5;"|  
|Pooling、AutoEnlistment 和 Client Cursor 以外的所有服務|**DBPROPVAL\_OS\_ENABLEALL&**<br /><br /> **~DBPROPVAL\_OS\_TXNENLISTMENT&**<br /><br /> **~DBPROPVAL\_OS\_CLIENTCURSOR**|"OLE DB Services \= \-7;"|  
|無服務|~**DBPROPVAL\_OS\_ENABLEALL**|"OLE DB Services \= 0;"|  
  
 如果提供者的登錄項目不存在，即使使用者已明確要求，元件管理員將不會彙總提供者的物件，並且不叫用任何服務。  
  
## 請參閱  
 [Resource Pooling](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [How Consumers Use Resource Pooling](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [How Providers Work Effectively with Resource Pooling](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)