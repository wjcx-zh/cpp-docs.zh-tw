---
title: "資料錄集：重新查詢資料錄集 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 資料錄集, 重新查詢"
  - "資料錄集, 重新查詢"
  - "重新整理資料錄集"
  - "Requery 方法"
  - "重新查詢資料錄集"
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 資料錄集：重新查詢資料錄集 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 本主題說明如何使用資料錄集物件自資料庫來重新查詢 \(也就是自我重新整理\)，以及您可能想要使用 [Requery](../Topic/CRecordset::Requery.md) 成員函式來進行這動作的時機。  
  
 重新查詢資料錄集的主要理由是：  
  
-   依據您或其他使用者加入資料錄和其他使用者刪除資料錄 \(您所作的刪除已反映至資料錄集\) 的情況，保持資料錄集的最新狀態。  
  
-   根據變更的參數值來重新整理資料錄集。  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a> 保持資料錄集最新狀態  
 您將經常想要重新查詢您的資料錄集物件，以便保持其最新狀態。  在多使用者的資料庫環境中，其他使用者可能會在您的資料錄集存留期中變更資料。  如需資料錄集何時會反映其他使用者所做的變更，以及其他使用者的資料錄集何時會反映您的變更的詳細資訊，請參閱[資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 和[動態集](../../data/odbc/dynaset.md)。  
  
##  <a name="_core_requerying_based_on_new_parameters"></a> 根據新參數來重新查詢  
 [Requery](../Topic/CRecordset::Requery.md) 的另一種常用 \(且一樣重要\) 的方式，是根據變更的參數值選取一組新的資料錄。  
  
> [!TIP]
>  如果您使用所變更的參數值來呼叫 **Requery**，查詢速度可能會比再次呼叫 **Open**  明顯加快。  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> 重新查詢動態集與快照  
 由於動態集意謂使用動態的最新資料來展示一組資料錄，若您想要反映其他使用者的加入情形，就需要經常地重新查詢動態集。  另一方面也可以使用快照集，因為您可在準備報表、計算總額等作業時，放心地依賴其靜態內容。  且有時，您可能想要重新查詢快照集。  在多使用者的環境中，快照集資料可能會由於其他使用者變動資料庫，而失去與資料來源的同步處理。  
  
#### 若要重新查詢資料錄集物件  
  
1.  呼叫物件的 [Requery](../Topic/CRecordset::Requery.md) 成員函式。  
  
 另一種做法是，您可先關閉再重新開啟原始的資料錄集。  反正，新的資料錄集代表資料來源目前的狀態。  
  
 如需範例，請參閱[資料錄檢視：填入第二個資料錄集的清單方塊](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。  
  
> [!TIP]
>  若要最佳化 **Requery** 效能，請不要變更資料錄集的 [filter](../../data/odbc/recordset-filtering-records-odbc.md) 或 [sort](../../data/odbc/recordset-sorting-records-odbc.md)。  只變更呼叫 **Requery** 前的參數值。  
  
 若 **Requery** 呼叫失敗，您可再次嘗試呼叫，否則您的應用程式應該正常結束。  一個 **Requery** 或 **Open** 的呼叫可能會因許多理由而失敗。  也許是網路發生錯誤；或在呼叫時，現有資料已釋放但還未取得新資料，其他的使用者可能會獨佔存取；或您的資料錄集所根據的資料表已刪除。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [資料錄集：建立和關閉資料錄集 \(ODBC\)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)