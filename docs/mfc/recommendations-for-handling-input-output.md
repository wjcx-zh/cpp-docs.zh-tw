---
title: "處理輸入/輸出的建議 | Microsoft Docs"
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
  - "檔案架構的 I/O 選項"
  - "I/O [C++]"
  - "I/O [C++], 檔案架構的選項"
  - "I/O [C++], 選項"
  - "I/O [MFC], 關於 I/O"
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 處理輸入/輸出的建議
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不論您是否使用檔案架構的 I\/O 取決於您回答下列決策樹的問題:  
  
 **在應用程式的主要資料是否位於磁碟檔案?**  
  
-   是，主要資料位於磁碟檔案:  
  
     **應用程式會讀取整個檔案至記憶體中開啟檔案並寫入整個檔案回磁碟上檔案儲存?**  
  
    -   為:這是預設的 MFC 文件案例。  使用 **CDocument** 序列化。  
  
    -   不會:這通常是大小寫以交易的更新檔案。  您更新以個別交易基礎檔案，而不需要 **CDocument** 序列化。  
  
-   否，主要資料不在磁碟檔案:  
  
     **資料是否位於 ODBC 資料來源?**  
  
    -   是，資料位於 ODBC 資料來源:  
  
         使用 MFC 的資料庫支援。  這個案例的標準 MFC 實作包含儲存 `CDatabase` 物件的 **CDocument** 物件，如本文 [什麼是 MFC 資料庫程式設計模型?](../data/what-is-the-mfc-database-programming-model-q.md)所述。  應用程式可能會讀取並寫入其他檔案—應用程式精靈的目的「資料庫檢視和檔案支援」選項。  在這種情況下，您為附屬檔案。會使用序列化。  
  
    -   否，資料不位於 ODBC 資料來源。  
  
         這個的範例案例:資料位於非 ODBC DBMS;資料會以其他機制讀取，例如 OLE 或 DDE。  
  
         在這種情況下，您不會使用序列化，因此，您的應用程式不會開啟且不儲存功能表項目。  正 MFC ODBC 應用程式使用文件儲存 `CRecordset` 物件，您可能仍然要使用 **CDocument** 當做本機壘。  但是，您不會使用框架的預設檔案開啟\/儲存文件序列化。  
  
 若要支援開放，儲存和儲存為檔案功能表上的命令，這個架構的文件序列化。  序列化讀取和寫入資料，包括衍生自類別的物件 `CObject`，儲存至永久儲存體，通常磁碟檔案。  序列化容易使用並提供許多您需要的服務，不過，可能不適合在許多資料存取應用程式。  資料存取應用程式通常會更新以個別交易為基礎的資料。  這些更新這個交易的立即影響的資料錄而非讀取和寫入整個資料檔案。  
  
 如需序列化的詳細資訊，請參閱 [序列化](../mfc/serialization-in-mfc.md)。  
  
## 請參閱  
 [序列化：序列化和資料庫輸入\/輸出比較](../mfc/serialization-serialization-vs-database-input-output.md)