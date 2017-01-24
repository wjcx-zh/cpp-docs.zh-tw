---
title: "OLE DB 物件模型 | Microsoft Docs"
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
  - "OLE DB, 物件模型"
  - "資料列集, OLE DB 物件模型"
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 物件模型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 物件模型包含下列物件或元件。  前四個列出的物件或元件 \(資料來源、工作階段、命令和資料列集\) 允許您連接至某個資料來源並檢視它。  其餘從存取子 \(Accessor\) 開始的元件或物件，與資料顯示時的使用有關。  
  
## 資料來源  
 資料來源物件允許您連接至資料來源，例如檔案或 DBMS。  資料來源物件會建立和管理這個連接，並且包含了使用權限和驗證 \(Authentication\) 的資訊 \(例如登入名稱和密碼\)。  一個資料來源物件可以建立一或多個工作階段。  
  
## 工作階段  
 工作階段會管理與資料來源的特定互動，以便查詢和擷取資料。  每一個工作階段是一筆單一交易。  一筆交易是由 ACID 測試所定義之不可分割的工作單位。  如需 ACID 定義的資訊，請參閱[交易](#vcconoledbcomponents_transactions)。  
  
 工作階段會執行重要的工作，例如：開啟資料列集和傳回建立工作階段的資料來源物件。  工作階段也可以傳回中繼資料 \(Metadata\) 或資料來源本身的資訊 \(例如資料表資訊\)。  
  
 一個工作階段可以建立一或多個命令。  
  
## 命令  
 命令會執行一段文字命令，例如一個 SQL 陳述式 \(Statement\)。  如果文字命令指定了一個資料列集 \(例如一個 SQL **SELECT** 陳述式\)，則命令會建立此資料列集。  
  
 命令只是文字命令的容器。文字命令是一個從消費者傳遞至資料來源物件，在提供者的基礎資料存放區執行的字串 \(例如 SQL 陳述式\)。  一般而言，此文字命令是一個 SQL **SELECT** 陳述式 \(在這種情況下，命令會自動建立一個資料列集，因為 SQL **SELECT** 指定了一個資料列集\)。  
  
## 資料列集  
 資料列集以表格格式公開資料。  索引是資料列集的一個特例。  您可以從工作階段或命令中建立資料列集。  
  
### 結構描述資料列集  
 結構描述 \(Schema\) 包含資料庫的中繼資料 \(結構的資訊\)。  結構描述資料列集是包含結構描述資訊的資料列集。  有些 DBMS 的 OLE DB 提供者支援結構描述資料列集物件。  如需結構描述資料列集的詳細資訊，請參閱[使用結構描述資料列集取得中繼資料](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)和[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)。  
  
### 檢視物件  
 檢視物件定義了資料列集內資料列或資料行的一個子集合。  它並不包含自身的資料。  檢視物件無法合併來自多個資料列集的資料。  
  
## 存取子  
 只有 OLE DB 使用存取子 \(Accessor\) 概念。  存取子描述資料在消費者中的儲存方式。  它包含一組介於資料列集欄位 \(資料行\) 和您在消費者中宣告的資料成員之間的繫結 \(稱之為資料行對應\)。  
  
##  <a name="vcconoledbcomponents_transactions"></a> 異動  
 在最低層級以外進行認可或中止巢狀交易的時後可以使用交易物件。  一筆交易是由 ACID 測試所定義之不可分割的工作單位。  ACID 代表：  
  
-   完整性：無法被分割成較小的工作單位。  
  
-   並行性：可同時發生一個以上交易。  
  
-   獨立性：一筆交易對另一筆交易所做的變更了解有限。  
  
-   永久性：交易產生的變更。  
  
## 列舉程式  
 列舉程式會搜尋可用的資料來源和其他的列舉程式。  沒有針對特定資料來源進行自訂的消費者會使用列舉程式來搜尋要使用的資料來源。  
  
 根列舉程式 \(附於 Microsoft Data Access SDK\) 周遊在登錄之中以尋找資料來源和其他的列舉程式。  其他的列舉程式會周遊在登錄之中或以提供者特定的方式來進行搜尋。  
  
## 錯誤  
 任何位於 OLE DB 物件上的介面都可能產生錯誤。  錯誤包含了某個錯誤的額外資訊，選擇性自訂錯誤物件也包括在其中。  這項資訊包含在 HRESULT 中。  
  
## 告知  
 告知是由一群共用資料列集且相互合作的消費者所使用 \(「共用」在此是假設消費者在同一個交易內工作\)。  告知讓共用資料列集且相互合作的消費者能夠得知其同儕在資料列集上所執行的動作。  
  
## 請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)