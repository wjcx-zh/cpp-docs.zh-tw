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
ms.openlocfilehash: cdae28f81eebe8427bc829072e0d9a83c6ec1722
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366952"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>資料錄集：重新查詢資料錄集 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題介紹如何使用記錄集對象從資料庫中重新查詢(即刷新)自身,以及何時使用[Requery](../../mfc/reference/crecordset-class.md#requery)成員函數執行此操作。

重新查詢記錄集的主要原因是:

- 將記錄設定與您或其他使用者添加的記錄以及其他使用者刪除的記錄(您刪除的記錄已反映在記錄集中)保持最新狀態。

- 根據更改的參數值刷新記錄集。

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>使記錄設定保持最新

通常,您需要重新查詢記錄集物件,使其保持最新狀態。 在多用戶資料庫環境中,其他用戶可以在記錄集的生命週期內對數據進行更改。 有關記錄集何時反映其他使用者所做的更改以及其他使用者的記錄集反映您的更改的詳細資訊,請參閱[記錄集:記錄集如何更新記錄 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[動態集](../../data/odbc/dynaset.md)。

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>基於新參數重新查詢

[重新查詢](../../mfc/reference/crecordset-class.md#requery)的另一個頻繁且同樣重要的用途是根據更改的參數值選擇一組新的記錄。

> [!TIP]
> 如果使用更改參數值進行調用,則查詢`Requery`速度可能比再次調用`Open`時快得多。

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>重新查詢動態集與快照

由於動態集旨在顯示一組具有動態最新數據的記錄,因此如果要反映其他使用者的添加內容,則經常要重新查詢動態集。 另一方面,快照很有用,因為您可以在準備報表、計算總計等時安全地依賴其靜態內容。 不過,有時您可能還需要重新查詢快照。 在多用戶環境中,當其他使用者更改資料庫時,快照數據可能會失去與數據源的同步。

#### <a name="to-requery-a-recordset-object"></a>重新查詢記錄集物件

1. 調用物件的[重新查詢](../../mfc/reference/crecordset-class.md#requery)成員函數。

或者,您可以關閉並重新打開原始記錄集。 在這兩種情況下,新記錄集表示數據源的當前狀態。

例如,請參閱[記錄檢視:從第二個紀錄集填充清單框](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。

> [!TIP]
> 要優化`Requery`效能,請避免變更紀錄集的[篩選器](../../data/odbc/recordset-filtering-records-odbc.md)或[排序](../../data/odbc/recordset-sorting-records-odbc.md)。 在調用`Requery`之前僅更改參數值。

如果`Requery`呼叫失敗,您可以重試呼叫;如果呼叫失敗,則可以重試呼叫。否則,您的應用程式應正常終止。 由於多種原因`Requery`,`Open`呼叫或可能失敗。 可能發生網路錯誤;或,在通話過程中,在現有數據發佈后,但在獲取新數據之前,其他使用者可能會獲得獨佔訪問許可權;或可以刪除記錄集所依賴的表。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
