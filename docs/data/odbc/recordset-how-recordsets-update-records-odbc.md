---
title: "資料錄集：資料錄集更新資料錄的方式 (ODBC) | Microsoft Docs"
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
  - "ODBC 資料錄集, 更新"
  - "資料錄, 更新"
  - "資料錄集, 編輯資料錄"
  - "資料錄集, 更新"
  - "更新資料錄集"
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：資料錄集更新資料錄的方式 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 資料錄集除了可自資料來源選取資料錄外，它還可 \(選擇性地\) 更新或刪除所選取的資料錄或加入資料錄。  有三個因素可決定資料錄集的可更新性：連接的資料來源是否可更新、您在建立資料錄集物件時所指定的選項和建立的 SQL。  
  
> [!NOTE]
>  `CRecordset` 物件所根據的 SQL 會影響資料錄集的可更新性。  例如，若您的 SQL 包含一個聯結或 **GROUP BY** 子句，MFC 會將可更新性設為 **FALSE**。  
  
> [!NOTE]
>  本文件適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  如果您要使用大量資料列擷取，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 這個主題說明：  
  
-   [您在資料錄集更新時的角色](#_core_your_role_in_recordset_updating)和架構所提供的功能。  
  
-   [資料錄集是編輯緩衝區](#_core_the_edit_buffer)和[動態集和快照集間的差異性](#_core_dynasets_and_snapshots)。  
  
 [資料錄集：AddNew、Edit 和 Delete 的運作方式 \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) 會從資料錄集的觀點來說明這些功能的動作。  
  
 [資料錄集：更多更新的詳細資訊 \(ODBC\)](../../data/odbc/recordset-more-about-updates-odbc.md) 是藉由說明交易如何影響更新、資料錄集的關閉或捲動如何影響更新過程，以及您的更新如何與其他使用者的更新互動，來完成資料錄集更新主題的說明。  
  
##  <a name="_core_your_role_in_recordset_updating"></a> 您在資料錄集更新時的角色  
 下表說明您在使用資料錄集加入、編輯或刪除資料錄時所扮演的角色，及架構的功能。  
  
### 資料錄集更新：您與架構  
  
|您|架構|  
|-------|--------|  
|判斷資料來源是否為可更新 \(或可附加的\)。|提供 [CDatabase](../../mfc/reference/cdatabase-class.md) 成員函式來測試資料來源的可更新性或可附加性。|  
|開啟一個可更新的資料錄集 \(任何型別的\)。||  
|藉由呼叫 `CRecordset` 內例如 `CanUpdate` 或 `CanAppend` 的更新函式，來決定資料錄集是否可更新。||  
|呼叫資料錄集成員函式來加入、編輯和刪除資料錄。|管理在您的資料錄集物件和資料來源間的資料交換機制。|  
|選擇性地使用交易來控制更新過程。|提供 `CDatabase` 成員函式來支援交易。|  
  
 如需交易的詳細資訊，請參閱[交易 \(ODBC\)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_the_edit_buffer"></a> 編輯緩衝區  
 將資料錄集內的欄位資料成員集合起來，當做包含一筆資料錄 \-\- 即目前資料錄的編輯緩衝區。  更新作業會使用這個緩衝區來運作目前資料錄。  
  
-   當您加入一筆資料錄時，編輯緩衝區會用來建立一筆新資料錄。  當您完成加入資料錄的動作時，先前為目前資料錄的資料錄會再次變為目前資料錄。  
  
-   當您更新 \(編輯\) 一筆資料錄時，編輯緩衝區會用來將資料錄集欄位資料成員設為新值。  當您完成更新動作，目前資料錄仍是所更新的資料錄。  
  
 當呼叫 [AddNew](../Topic/CRecordset::AddNew.md) 或 [Edit](../Topic/CRecordset::Edit.md) 時，會儲存目前的資料錄，然後在稍後可以視需要還原。  當呼叫 [Delete](../Topic/CRecordset::Delete.md) 時，不會儲存目前的資料錄，但會標記為已刪除，您必須捲動至其他的資料錄。  
  
> [!NOTE]
>  編輯緩衝區在資料錄刪除時不扮演任何角色。  當您刪除目前的資料錄，該資料錄會標記成已刪除，且資料錄集是「不在一筆資料錄上」，直到您捲動至不同的資料錄。  
  
##  <a name="_core_dynasets_and_snapshots"></a> 動態集和快照集  
 [動態集](../../data/odbc/dynaset.md)會在捲動至資料錄時重新整理資料錄的內容。  [快照集](../../data/odbc/snapshot.md)是資料錄的靜態表示，所以要等到呼叫 [Requery](../Topic/CRecordset::Requery.md) 之後，才會重新整理資料錄的內容。  若要使用動態集的所有功能，您必須使用與正確層級的 ODBC API 支援一致的 ODBC 驅動程式。  如需詳細資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md) 和[動態集](../../data/odbc/dynaset.md)。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：AddNew、Edit 和 Delete 的運作方式 \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)