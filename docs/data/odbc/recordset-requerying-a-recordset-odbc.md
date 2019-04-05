---
title: 資料錄集：重新查詢資料錄集 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: 7edc1c04da617f96165b25a47ce169b266ae0003
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024591"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>資料錄集：重新查詢資料錄集 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明如何使用資料錄集物件，以及在重新查詢 （也就是重新整理） 本身從資料庫和您可能想要透過達成[Requery](../../mfc/reference/crecordset-class.md#requery)成員函式。

重新查詢資料錄集的主要理由是：

- 將最新狀態相對於您或其他使用者新增的記錄和記錄 （那些您刪除已反映在資料錄集） 的其他使用者刪除資料錄集。

- 重新整理資料錄集根據變更的參數值。

##  <a name="_core_bringing_the_recordset_up_to_date"></a> 資料錄集向上帶入日期

通常，您會想要重新查詢您的資料錄集物件，使其最新狀態。 在多使用者的資料庫環境中，其他使用者可以變更資料的資料錄集生命期限內。 如需有關資料錄集反映其他使用者所做的變更時，與其他使用者的資料錄集時反映您的變更的詳細資訊，請參閱[資料錄集：資料錄集更新資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)並[動態集](../../data/odbc/dynaset.md)。

##  <a name="_core_requerying_based_on_new_parameters"></a> 重新查詢根據新的參數

另一種常用 — 也同樣重要的 — 利用[Requery](../../mfc/reference/crecordset-class.md#requery)是選取一組新的記錄是依據變更的參數值。

> [!TIP]
>  查詢速度獲得可能大幅提升，如果您呼叫`Requery`變更參數值，如果您呼叫比`Open`一次。

##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> 重新查詢動態集 vs。快照

因為動態集，為了呈現一組記錄，以動態的最新資料，您會想要重新查詢動態集，通常是如果您想要反映其他使用者的新增功能的時候。 快照集，相反地，會非常實用，因為您可以安全地仰賴其靜態內容時準備報告、 計算總計，以及等等。 儘管如此，您有時可能會想要重新查詢的快照集。 在多使用者環境中，快照集的資料可能會遺失與資料來源的同步處理，因為其他使用者變更的資料庫。

#### <a name="to-requery-a-recordset-object"></a>若要重新查詢資料錄集物件

1. 呼叫[Requery](../../mfc/reference/crecordset-class.md#requery)之物件的成員函式。

或者，您可以關閉並重新開啟原始的資料錄集。 在任一情況下，新的資料錄集代表資料來源的目前狀態。

如需範例，請參閱[資料錄檢視：填入清單方塊從第二個資料錄集](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。

> [!TIP]
>  若要最佳化`Requery`效能，避免變更資料錄集的[篩選](../../data/odbc/recordset-filtering-records-odbc.md)或是[排序](../../data/odbc/recordset-sorting-records-odbc.md)。 只能變更參數值然後再呼叫`Requery`。

如果`Requery`呼叫就會失敗，您可以重試呼叫; 否則您的應用程式應該依正常程序終止。 呼叫`Requery`或`Open`多種原因所造成的任何可能會失敗。 也許發生網路錯誤;或者，您也可以在呼叫期間，發行現有的資料之後，但之前會取得新的資料，另一位使用者可能會取得獨佔存取權;或無法刪除資料錄集所相依的資料表。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：動態繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)