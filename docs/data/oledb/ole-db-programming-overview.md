---
title: "OLE DB 程式設計概觀 | Microsoft Docs"
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
  - "OLE DB, 關於 OLE DB"
  - "通用資料存取"
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 程式設計概觀
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

什麼是 OLE DB？它與其他資料庫技術有何不同？  OLE DB 是 Microsoft 所提供之高效能、以 COM 為基礎的技術。  OLE DB 不同於其他 Microsoft 資料庫技術的原因在於它提供了通用資料存取。  
  
## 通用資料存取  
 通用資料存取提供了存取資料的常見方法，無論資料儲存的形式為何。  在一般的商用情況中，大量的資訊不儲存於企業組織資料庫。  這個資訊可在檔案系統 \(例如 FAT 或 NTFS\)、索引循序檔、個人資料庫 \(例如 Access\)、試算表 \(例如 Excel\)、專案規劃應用程式 \(例如 Project\) 和電子郵件 \(例如 Outlook\) 中找到。  
  
 使用各種相關的應用程式存取資料時，在工作流程上會產生較大的瓶頸，或者至少也是件惱人的事。  很多公司發現它們處於此種情況，而將資訊合併在資料庫管理系統 \(DBMS\) 中來解決問題。  然而，這樣的變動於成本和時間上都所費不貲，且在許多情況下並不切實際。  
  
 另一種解決方法是開發一個通用資料存取方案。  OLE DB 和 ADO 提供通用資料存取的能力。  兩者之中，OLE DB 具有較佳的效能，且建議搭配 Visual C\+\+ 應用程式來使用。  
  
 通用資料存取意味著兩種能力，第一種是分散式查詢或多個 \(分散\) 資料來源的制式存取，第二種是使非 DBMS 資料來源可供資料庫應用程式存取的能力。  
  
-   分散式查詢  
  
     使用制式方式存取多個 \(也就是分散式的\) 資料來源的能力。  資料來源可以是相同的種類 \(例如兩個不同的 Access 資料庫\)，或不同的種類 \(例如一個是 SQL Server 資料庫而另一個是 Access 資料庫\)。  制式方式表示您可以在所有的資料來源上，有意義地執行相同的查詢。  
  
-   非 DBMS 存取  
  
     使非 DBMS 的資料來源可供資料庫應用程式存取的能力。  DBMS 資料來源範例包括 IMS、DB2、Oracle、SQL Server、Access 和 Paradox。  非 DBMS 資料來源範例包含檔案系統、電子郵件、試算表和專案管理工具的資訊。  
  
 請試想一個案例：銷售部門需要找出某地區的客戶在一星期內的所有電子郵件。  這項查詢可能需要搜尋某個電子郵件應用程式的信箱檔，以及在 Access 客戶資料表中指定客戶的名稱進行搜尋。  Access 是一個 DBMS 應用程式，然而 Outlook 並不是。  
  
 OLE DB 讓您可以開發存取不同資料來源的應用程式，不論它們是不是資料庫管理系統。  OLE DB 使用的 COM 支援介面支援了適用於指定資料來源的 DBMS 功能，讓您可以進行通用存取。  COM 減少了不必要的重複服務，也提供資料來源間以及其他應用程式間最佳的互通性 \(Interoperability\)。  
  
## COM 的優點  
 這就是 COM 存在的原因。  OLE DB 是一組 COM 介面。  透過一組制式的介面存取資料，您可以將資料庫組織成合作元件的矩陣。  
  
 OLE DB 根據 COM 的規格，定義了一個可擴充和維護的介面集合，此集合可將 DBMS 的功能分解並包裝成一致、可重複使用的部分。  這些介面定義了 DBMS 元件 \(例如：資料列容器、查詢處理器和交易協調器\) 的界限，使得不同的資訊來源可由制式交易存取。  
  
 一般我們會將 OLE DB 應用程式撰寫成 DLL。但隨著元件化程式碼的使用，OLE DB 的 COM 實作已克服了 DLL 的缺點 \(例如命名和版本問題\)。  在 OLE DB 中，您可以使用介面或元件的全域唯一識別項 \(GUID\) 來呼叫該介面或存取其他元件。  
  
 最後，COM 會使用參考計數來追蹤元件的使用。  當您在介面上呼叫方法時，參考計數會遞增；當方法傳回時，參考計數會遞減。  當計數等於零時，方法所屬的元件會被釋放。  
  
## 請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 樣板](../../data/oledb/ole-db-templates.md)