---
title: "Oracle 連接 | Microsoft Docs"
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
  - "連接 [C++], 資料庫"
  - "資料庫連接 [C++], Oracle"
  - "資料庫 [C++], 連接至"
  - "Oracle [C++], 建立連接"
  - "Oracle 資料庫 [C++]"
  - "Oracle 資料庫 [C++], 連接"
ms.assetid: d317e763-44aa-47c9-abe8-261d513d894f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Oracle 連接
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您設定 Oracle ODBC 資料來源名稱或 OLE DB 連接的組態時，必須先安裝 Oracle SQL\*Net 用戶端元件。  SQL\*Net 為 Oracle 的網路傳輸層 \(Transport Layer\)。  大多數 Oracle ODBC 驅動程式，包括 Microsoft 的驅動程式和 Microsoft OLE DB Oracle 提供者對應在內，都會直接呼叫這個 SQL\*Net 層。  
  
 設定好 SQL\*Net 之後，請注意您的 SQL\*Net 連接字串。  一般而言，這是由 Oracle 資料庫伺服器名稱的存取規範和網路通訊協定類型 \(例如 TCP\/IP 和具名管道 \(Named Pipe\)\) 所組成。  通常，SQL\*Net 連接字串會對應至別名 \(Alias\)。  在這種情況下，您只需要記下該別名。  如需如何設定 SQL\*Net 的詳細資訊，請聯繫 Oracle DBA、參閱 SQL\*Net 文件，或參照您的 Oracle ODBC 驅動程式說明檔，以取得連接字串的範例。  
  
## 請參閱  
 [建立資料庫連接](../../data/ado-rdo/creating-database-connections.md)