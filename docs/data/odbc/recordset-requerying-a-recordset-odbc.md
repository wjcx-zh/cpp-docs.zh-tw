---
title: 資料錄集： 重新查詢資料錄集 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3157f416cf6fb7e0fd3b5ad4797b83de218c9ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-requerying-a-recordset-odbc"></a>資料錄集：重新查詢資料錄集 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明如何使用資料錄集物件，以及在項目重新查詢 （也就是重新整理） 本身從資料庫和您可能想要透過達成[Requery](../../mfc/reference/crecordset-class.md#requery)成員函式。  
  
 重新查詢資料錄集的主要原因如下：  
  
-   將最新狀態新增您或其他使用者的記錄和其他使用者 （與您刪除已反映在資料錄集） 所刪除的記錄資料錄集。  
  
-   重新整理資料錄集的根據變更的參數值。  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a> 將資料錄集上的日期  
 通常，您會想要重新查詢資料錄集物件，讓它最新狀態。 在多使用者資料庫環境中，其他使用者可以變更資料的資料錄集的生命期限內。 如需有關資料錄集反映其他使用者所做的變更時，當其他使用者的資料錄集反映您的變更的詳細資訊，請參閱[資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[動態](../../data/odbc/dynaset.md).  
  
##  <a name="_core_requerying_based_on_new_parameters"></a> 重新查詢為基礎的新參數  
 另一種常用，也同樣重要的 — 使用[Requery](../../mfc/reference/crecordset-class.md#requery)是選取一組新的記錄是依據變更的參數值。  
  
> [!TIP]
>  查詢速度的速度可能明顯如果您呼叫**Requery**變更參數值，如果您呼叫比**開啟**一次。  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> 查詢動態集 vs。快照  
 因為動態集，為了呈現含有最新的動態資料的一組記錄，您會想要重新查詢動態集通常如果您想要反映其他使用者的新增項目。 快照集，相反地，會非常有用，因為您可以安全地依賴其靜態內容準備報告，計算的總計，與等等。 儘管如此，您有時可能會想要重新查詢的快照集。 在多使用者環境中，快照集資料可能遺失其他使用者變更的資料庫與資料來源的同步處理。  
  
#### <a name="to-requery-a-recordset-object"></a>若要重新查詢資料錄集物件  
  
1.  呼叫[Requery](../../mfc/reference/crecordset-class.md#requery)物件的成員函式。  
  
 或者，您可以關閉並重新開啟原始的資料錄集。 在任一情況下，新的資料錄集表示資料來源的目前狀態。  
  
 如需範例，請參閱[資料錄檢視： 填入清單方塊從第二個資料錄集](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。  
  
> [!TIP]
>  若要最佳化**Requery**效能，避免變更資料錄集的[篩選](../../data/odbc/recordset-filtering-records-odbc.md)或[排序](../../data/odbc/recordset-sorting-records-odbc.md)。 只能變更參數值然後再呼叫**Requery**。  
  
 如果**Requery**呼叫就會失敗，您可以重試該呼叫; 否則您的應用程式應該依正常程序終止。 呼叫**Requery**或**開啟**多種原因所造成的任何可能會失敗。 可能是網路發生錯誤。或者，您也可以在呼叫期間釋放現有的資料後，但取得新的資料時，另一位使用者可能會取得獨佔存取權;或無法刪除資料錄集所相依的資料表。  
  
## <a name="see-also"></a>另請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)