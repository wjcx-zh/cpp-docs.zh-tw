---
title: "我應該使用 DAO 或是 ODBC？ | Microsoft Docs"
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
  - "DAO [C++], 和 ODBC 的比較"
  - "資料庫類別 [C++], DAO"
  - "資料庫類別 [C++], ODBC"
  - "ODBC [C++], 和 DAO 比較"
ms.assetid: 9f67613f-0056-4ece-8c3a-9872e9563d57
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 我應該使用 DAO 或是 ODBC？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  從 Visual C\+\+ .NET 開始，Visual C\+\+ 環境和精靈不再支援 DAO \(但該版本中仍包含 DAO 類別，您仍然可以使用這些類別\)。  Microsoft 建議您針對新的專案使用 OLE DB 樣板或是 ODBC。  請在維護現有應用程式時再使用 DAO。  
  
 您應該使用哪一組 MFC 類別？  這將視您的需要而定：  
  
-   如果您只能使用 ODBC 資料來源，請使用 ODBC 類別，特別是在主從架構的狀況中，在此狀況下 MFC ODBC 類別將提供較佳的效能。  
  
-   如果您主要使用 Microsoft Jet \(.mdb\) 資料庫，或是 Microsoft Jet 資料庫引擎可直接讀取的其他資料庫格式，則使用 DAO 類別。  如需這些項目的清單，請參閱[我可使用 DAO 和 ODBC 存取什麼資料庫？](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)  
  
-   當需要加速 Microsoft Jet 資料庫引擎和 DAO 類別的其他功能時，可透過 DAO 類別來存取 ODBC 資料來源。  
  
    > [!NOTE]
    >  DAO 需要額外的硬碟空間。  
  
 DAO 類別具有以下優點：  
  
-   在某些情況下可提供較佳的效能，特別是在使用 Microsoft Jet \(.mdb\) 資料庫時。  
  
-   可與 ODBC 類別和 Microsoft Access Basic 和 Microsoft Visual Basic 一致。  
  
-   存取驗證規則 \(Rule\)。  
  
-   可指定資料表之間的關係。  
  
-   更多樣化的資料存取模型，可支援資料定義語言 \(Data Definition Language，DDL\) 和資料操作語言 \(Data Manipulation Language，DML\)。  如需詳細資訊，請參閱[資料庫定義和管理](../data/are-ddl-and-dml-supported-q.md)。  
  
 下表摘要出主要差異以協助您選擇。  
  
### 在 MFC DAO 和 ODBC 類別之間選擇  
  
|是否可以|使用 DAO 類別？|使用 ODBC 類別？|  
|----------|----------------|-----------------|  
|存取 .MDB 檔|有|有|  
|存取 ODBC 資料來源|有|有|  
|可用於 16 位元|沒有|有|  
|可用於 32 位元|有|有|  
|可用於 64 位元|沒有|有|  
|資料庫壓縮|有|沒有|  
|資料庫引擎支援|Microsoft Jet 資料庫引擎|目標 DBMS|  
|DDL 支援|有|只能透過直接的 ODBC 呼叫|  
|DML 支援|有|有|  
|MFC 實作性質|DAO 核心函式的「包裝函式」|簡化的抽象層，而非 ODBC API 的「包裝函式」|  
|最佳化|.mdb 檔 \(Microsoft Access\)|您擁有驅動程式的任何 DBMS，特別是在主從架構的狀況中|  
|交易支援|每個解決方案，或針對 ODBC 資料、每個資料庫|每個資料庫|  
  
 請切住，ODBC 驅動程式的功能都不相同。  如需詳細資訊，請參閱《ODBC 程式設計人員參考》和 ODBC 驅動程式的說明檔。  
  
## 請參閱  
 [資料存取常見問題集](../data/data-access-frequently-asked-questions-mfc-data-access.md)