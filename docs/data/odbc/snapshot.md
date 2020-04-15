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
ms.openlocfilehash: e487b5abcc5eee4e3f4b1941100980eac4a040c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366913"
---
# <a name="snapshot"></a>快照式

快照是一個記錄集,反映創建快照時存在的數據的靜態視圖。 當您打開快照並移動到所有記錄時,它包含的記錄集及其值不會更改,直到通過調用`Requery`重新生成快照。

> [!NOTE]
> 本主題適用於 MFC ODBC 類別。 如果使用 MFC DAO 類而不是 MFC ODBC 類,請參閱[CDaoRecordset::打開](../../mfc/reference/cdaorecordset-class.md#open)以說明快照類型的記錄集。

您可以使用資料庫類創建可更新或唯讀快照。 與動態集不同,可更新的快照不反映其他使用者對記錄值所做的更改,但它確實反映了程式所做的更新和刪除。 添加到快照的記錄在調用`Requery`之前不會對快照可見。

> [!TIP]
> 快照是 ODBC 靜態游標。 在滾動到該記錄之前,靜態游標實際上不會獲取一行數據。 為了確保立即檢索所有記錄,可以滾動到記錄集的末尾,然後滾動到要查看的第一個記錄。 但是請注意,滾動到末尾需要額外的開銷,並且會降低性能。

當您需要數據在操作期間保持固定時(如生成報表或執行計算時)時,快照最有價值。 即便如此,數據源也可能與快照有很大差異,因此您可能需要不時重建它。

快照支援基於 ODBC 游標庫,該庫為任何級別 1 驅動程式提供靜態游標和定位更新(更新性需要)。 必須將游標庫 DLL 載入到記憶體中才能獲得此支援。 建構`CDatabase`物件並調用`OpenEx`其 成員函數時,必須指定*dwOptions*`CDatabase::useCursorLib`參數的選項。 如果調用`Open`成員函數,則默認情況下將載入游標庫。 如果使用動態集而不是快照,則不希望導致載入游標庫。

僅當建`CDatabase`譯 物件時載入了 ODBC 游標庫或您使用的 ODBC 驅動程式支援靜態游標時,快照才可用。

> [!NOTE]
> 對於某些 ODBC 驅動程式,快照(靜態游標)可能無法更新。 檢查驅動程式文件,瞭解支援的游標類型及其支援的併發類型。 為了保證可更新的快照,請確保在建立物件時將游標庫載入到記憶體中`CDatabase`。 有關詳細資訊,請參閱[ODBC:ODBC 游標庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!NOTE]
> 如果要同時使用快照和動態集,則必須將它們基於兩個不同的`CDatabase`物件(兩個不同的連接)。

有關快照共用所有記錄集的屬性的詳細資訊,請參閱[記錄集 (ODBC)。](../../data/odbc/recordset-odbc.md) 有關 ODBC 和快照的詳細資訊(包括 ODBC 游標庫),請參閱[ODBC](../../data/odbc/odbc-basics.md)。

## <a name="see-also"></a>另請參閱

[開放資料庫連線 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
