---
title: 快照
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
ms.openlocfilehash: 99e1d76f8d65def326b0514f3219cef43f695220
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512658"
---
# <a name="snapshot"></a>快照

快照集是存在於的建立快照集時，會反映資料的靜態檢視表的資料錄集。 當您開啟快照集，並移至 所有記錄時，它所包含的一組記錄，且其值不會變更之前呼叫重建快照集`Requery`。

> [!NOTE]
>  本主題適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別，而不 MFC ODBC 類別，請參閱[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)快照集類型的資料錄集的描述。

您可以建立可更新或唯讀快照集與資料庫類別。 不同於動態集，可更新的快照集不會反映記錄值的其他使用者所做的變更，但它未反映更新和刪除由您的程式。 資料錄集加入快照集不會成為可見到快照集之前呼叫`Requery`。

> [!TIP]
>  快照集是 ODBC 靜態資料指標。 靜態資料指標無法實際取得資料列直到您捲動至該記錄。 若要確保立即擷取所有的記錄，您可以捲動至您的資料錄集的結尾，然後捲動至您想要查看第一筆記錄。 不過請注意，，向下捲動到結尾需要額外的負荷，而且可能降低效能。

當您需要保持固定，您在作業期間，當您會產生一份報表，或執行計算的資料時，快照集是最有價值。 即便如此，資料來源可以開始分枝成大幅從快照集，因此您可能想要不時重建它。

快照集支援根據 ODBC 資料指標程式庫，可提供靜態資料指標以及位於任何層級 1 驅動程式的更新 （需要可更新性）。 在記憶體中的這項支援，必須載入資料指標程式庫 DLL。 當您建構`CDatabase`物件並呼叫其`OpenEx`成員函式，您必須指定`CDatabase::useCursorLib`選項*dwOptions*參數。 如果您呼叫`Open`預設會載入成員函式，資料指標程式庫。 如果您使用動態集，而不快照集，您不想造成要載入的資料指標程式庫。

快照集是已載入 ODBC 資料指標程式庫時，才提供使用`CDatabase`建構的物件，或您使用的 ODBC 驅動程式支援靜態資料指標。

> [!NOTE]
>  對於某些 ODBC 驅動程式中，快照集 （靜態資料指標） 可能不是可更新。 請檢查您的驅動程式文件，以支援資料指標類型和所支援的並行類型。 若要保證可更新的快照集，請確定您將載入資料指標程式庫到記憶體中，當您建立`CDatabase`物件。 如需詳細資訊，請參閱 < [ODBC: ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!NOTE]
>  如果您想要使用快照集和動態集，您必須根據兩個不同`CDatabase`物件 （兩個不同的連接）。

使用所有的資料錄集屬性的快照集共用的相關資訊，請參閱[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。 如需有關 ODBC 和快照集，包括 ODBC 資料指標程式庫，請參閱[ODBC](../../data/odbc/odbc-basics.md)。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)