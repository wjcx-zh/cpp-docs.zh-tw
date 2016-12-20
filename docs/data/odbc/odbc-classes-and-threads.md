---
title: "ODBC 類別和執行緒 | Microsoft Docs"
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
  - "ODBC 類別, 和執行緒"
  - "ODBC, 多執行緒應用程式"
  - "執行緒 [MFC], ODBC 支援"
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 類別和執行緒
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 MFC 4.2 版以後便具有對 MFC ODBC 類別的多執行緒 \(Multithread\) 支援。  請注意，MFC 並未提供 DAO 類別的多執行緒支援。  
  
 ODBC 類別的多執行緒支援具有某些限制。  由於這些類別包裝了 ODBC API，因此他們已被限制在建立此多執行緒支援的元件上。  例如，許多 ODBC 驅動程式並不是安全執行緒 \(Thread\-Safe\)，所以如果您使用了其中一種驅動程式，MFC ODBC 類別就不會是安全執行緒。  您應該驗證您的特定驅動程式是否為安全執行緒。  
  
 您應該在建立一個多執行緒應用程式時，非常小心地使用多執行緒來操作相同的物件。  例如，在兩個執行緒中使用相同的 `CRecordset` 物件可能會在擷取資料時造成問題，其中一個執行緒的擷取作業可能會覆寫另一個執行緒所擷取的資料。  在不同執行緒中使用 MFC ODBC 類別的常見方式，是在跨執行緒中共用一個開啟的 `CDatabase` 物件，以便讓每個執行緒的個別 `CRecordset` 物件使用相同的 ODBC 連接。  請注意，不要將一個未開啟的 `CDatabase` 物件傳遞到另一個執行緒中的 `CRecordset` 物件。  
  
> [!NOTE]
>  如果您一定要使用多執行緒來操作相同物件，就應該實作適當的同步處理機制 \(Synchronization Mechanism\)，例如關鍵區段 \(Critical Section\)。  請確認某些特定作業 \(例如 **Open**\) 並未受到保護。  您應該確定這些作業不會同時被不同的執行緒呼叫。  
  
 如需建立多執行緒的詳細資訊，請參閱[多執行緒主題](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Data Access Programming \(MFC\/ATL\)](../../data/data-access-programming-mfc-atl.md)