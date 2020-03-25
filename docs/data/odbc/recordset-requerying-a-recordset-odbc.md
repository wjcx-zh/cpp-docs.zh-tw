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
ms.openlocfilehash: b7cf40ca3b0c8e415368772063aee61008a52764
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212780"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>資料錄集：重新查詢資料錄集 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明如何使用 recordset 物件，從資料庫重新查詢（也就是重新整理）本身，以及當您想要利用[requery](../../mfc/reference/crecordset-class.md#requery)成員函式來執行此動作。

重新查詢記錄集的主要原因如下：

- 將記錄集與您或其他使用者所新增的記錄（您的刪除已反映在記錄集內的其他使用者與記錄）保持在最新狀態。

- 根據變更參數值來重新整理記錄集。

##  <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>使記錄集保持在最新狀態

通常，您會想要重新查詢記錄集物件，使其保持在最新狀態。 在多使用者資料庫環境中，其他使用者可以在記錄集的生命週期內對資料進行變更。 如需當記錄集反映其他使用者所做的變更，以及其他使用者的記錄集反映您的變更時的詳細資訊，請參閱[記錄集：記錄集更新記錄（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[動態集](../../data/odbc/dynaset.md)的方式。

##  <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>根據新參數重新查詢

另一個常見的（同樣重要的是，使用[Requery](../../mfc/reference/crecordset-class.md#requery) ）是根據變更參數值來選取一組新的記錄。

> [!TIP]
>  如果您使用變更參數值來呼叫 `Requery`，而不是再次呼叫 `Open`，則查詢速度可能會大幅加快。

##  <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>重新查詢動態對應與快照集

由於動態集的目的是要呈現一組具有動態最新資料的記錄，因此如果您想要反映其他使用者的新增專案，您會想要經常重新查詢動態集。 另一方面，快照集很有用，因為您可以在準備報表、計算總計等等時，安全地依賴其靜態內容。 儘管如此，您有時可能也會想要重新查詢快照集。 在多使用者環境中，快照集資料可能會隨著其他使用者變更資料庫而遺失與資料來源的同步處理。

#### <a name="to-requery-a-recordset-object"></a>若要重新查詢記錄集物件

1. 呼叫物件的[Requery](../../mfc/reference/crecordset-class.md#requery)成員函式。

或者，您可以關閉並重新開啟原始記錄集。 不論是哪一種情況，新的記錄集都代表資料來源的目前狀態。

如需範例，請參閱[記錄 Views：從第二個記錄集填入清單方塊](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。

> [!TIP]
>  若要優化 `Requery` 效能，請避免變更記錄集的[篩選](../../data/odbc/recordset-filtering-records-odbc.md)或[排序](../../data/odbc/recordset-sorting-records-odbc.md)。 呼叫 `Requery`之前，請只變更參數值。

如果 `Requery` 呼叫失敗，您可以重試呼叫;否則，您的應用程式應該會正常終止。 `Requery` 或 `Open` 的呼叫可能會因許多原因而失敗。 可能發生網路錯誤;或者，在呼叫期間，在發行現有的資料之後，但是在取得新資料之前，另一位使用者可能會取得獨佔存取權;或是您的記錄集相依的資料表可能會遭到刪除。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
