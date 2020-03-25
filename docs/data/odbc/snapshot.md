---
title: 快照式
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
ms.openlocfilehash: 62b5952f3052a3248175ce7892b1cf4615f1dd17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212689"
---
# <a name="snapshot"></a>快照式

快照集是一種記錄檔，反映資料在建立快照集時所存在的靜態觀點。 當您開啟快照集並移至所有記錄時，它所包含的一組記錄和其值不會變更，直到您藉由呼叫 `Requery`重建快照為止。

> [!NOTE]
>  本主題適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別，而不是 MFC ODBC 類別，請參閱[CDaoRecordset：： Open](../../mfc/reference/cdaorecordset-class.md#open) ，以取得快照集類型記錄集的描述。

您可以使用資料庫類別來建立可更新或唯讀的快照集。 不同于動態集，可更新的快照不會反映其他使用者對記錄值所做的變更，但會反映程式所做的更新和刪除。 加入至快照集的記錄在您呼叫 `Requery`之前，不會顯示在快照中。

> [!TIP]
>  快照集是 ODBC 靜態資料指標。 靜態資料指標實際上不會取得資料列，直到您滾動到該記錄為止。 若要確保立即抓取所有記錄，您可以滾動到記錄集的結尾，然後流覽至您想要查看的第一筆記錄。 不過要注意的是，滾動到結尾需要額外的負荷，而且可能會降低效能。

當您需要資料在作業期間維持固定的狀態時，快照集最有價值，如同您在產生報表或執行計算時一樣。 就算如此，資料來源也可能會從您的快照集中分離，因此您可能會想要在一段時間後重建。

快照集支援是以 ODBC 資料指標程式庫為基礎，它會針對任何層級1驅動程式提供靜態資料指標和位置更新（可更新的需求）。 資料指標程式庫 DLL 必須載入記憶體中，才能進行這項支援。 當您建立 `CDatabase` 物件並呼叫其 `OpenEx` 成員函式時，您必須指定*dwOptions*參數的 `CDatabase::useCursorLib` 選項。 如果您呼叫 `Open` 成員函式，則預設會載入資料指標程式庫。 如果您使用的是動態集，而不是快照，則不會想要載入資料指標程式庫。

只有在建立 `CDatabase` 物件或您所使用的 ODBC 驅動程式支援靜態資料指標時，才可以使用快照集。

> [!NOTE]
>  對於某些 ODBC 驅動程式，快照集（靜態資料指標）可能無法更新。 請查看您的驅動程式檔，以瞭解支援的資料指標類型以及它們支援的並行類型。 若要保證可更新的快照集，請務必在建立 `CDatabase` 物件時，將資料指標程式庫載入記憶體中。 如需詳細資訊，請參閱[odbc： odbc 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!NOTE]
>  如果您想要同時使用快照集和動態連結程式庫，您必須將它們以兩個不同的 `CDatabase` 物件（兩個不同的連接）做為基礎。

如需屬性快照集與所有記錄集共用的詳細資訊，請參閱[記錄集（ODBC）](../../data/odbc/recordset-odbc.md)。 如需 ODBC 和快照集的詳細資訊，包括 ODBC 資料指標程式庫，請參閱[odbc](../../data/odbc/odbc-basics.md)。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
