---
title: "OLE DB 架構設計問題 | Microsoft Docs"
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
  - "OLE DB, 應用程式設計考量"
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 架構設計問題
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開始 OLE DB 應用程式之前，您應當考慮下列問題：  
  
 **您要使用何種程式設計實作來撰寫 OLE DB 應用程式？**  
 Microsoft 提供的多種程式庫可完成這項工作：OLE DB 樣板程式庫、OLE DB 屬性和 OLE DB SDK 中的原始 OLE DB 介面。  除此之外，還有可幫助您撰寫程式的精靈。  在 [OLE DB 樣板、屬性和其他實作](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)中說明了這些實作。  
  
 **您需要撰寫自己的提供者嗎？**  
 大多數開發人員不需要撰寫自己的提供者。  Microsoft 提供了數個提供者。  每當建立一個資料連接時 \(例如，使用 ATL OLE DB 消費者精靈將消費者加入至專案時\)，\[**資料連結屬性**\] 對話方塊會列出登錄在您系統上的所有可用提供者。  如果其中一個提供者適用於您自己的資料存放區和資料存取應用程式，則最簡單的方式就是使用它。  然而，如果您的資料存放區不適用於這些目錄的其中任何一種，就必須建立自己的提供者。  如需建立提供者的詳細資訊，請參閱 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)。  
  
 **您的消費者需要何種層次的支援？**  
 有些消費者是很基本的，有些則是非常複雜。  OLE DB 物件的功能由屬性 \(Property\) 所指定。  當您使用 ATL OLE DB 消費者精靈來建立消費者，或使用資料庫提供者精靈來建立提供者時，它會為您設定適當的物件屬性，提供您一組標準的功能。  然而，如果精靈產生的消費者或提供者類別不支援您的所有需求，您就需要參考 [OLE DB 樣板程式庫](../../data/oledb/ole-db-templates.md)中那些類別的介面。  這些介面包裝原始的 OLE DB 介面，並提供了額外的實作，讓您使用起來更容易。  
  
 例如，如果您想要更新資料列集內的資料，但在使用精靈建立消費者時忘記指定這項作業，則您可以在事後設定命令物件上的 **DBPROP\_IRowsetChange** 和 **DBPROP\_UPDATABILITY** 屬性來指定這項功能。  然後，在建立了資料列集以後，它會有 `IRowsetChange` 介面。  
  
 **您是否有使用另一項資料存取技術 \(ADO、ODBC 或 DAO\) 的舊程式碼？**  
 由於可能會合併使用多種技術 \(例如將 ADO 元件和 OLE DB 元件搭配在一起使用以及將 ODBC 程式碼轉換成 OLE DB\)，Visual C\+\+ 文件無法涵蓋所有的範圍。  不過，下列的 Microsoft 網站有許多涵蓋各種案例的文件：  
  
-   [Microsoft 說明及支援](http://go.microsoft.com/fwlink/?LinkId=148218)  
  
-   [Microsoft 資料存取技術文件概觀](http://go.microsoft.com/fwlink/?LinkId=148217)  
  
-   [Visual Studio 方案中心](http://go.microsoft.com/fwlink/?LinkId=148215)  
  
-   [搜尋 Microsoft.com](http://search.microsoft.com/)  
  
 執行搜尋時，請輸入最符合您專案的關鍵字組合。例如：如果您搭配使用了 ADO 物件和 OLE DB 提供者，請試著使用 **ADO AND "OLE DB"** 來進行 Boolean 搜尋。  如果您想要將舊版的 DAO 程式碼轉換成 ODBC，請選取 \[all words\]，並指定 **migrating DAO** 或 DAO legacy 這類的字串。  
  
## 請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)