---
title: 'ODBC: ODBC 資料指標程式庫 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 83b09d836422cbf32b70ac904aa31fcff2ad00bb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078254"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC：ODBC 資料指標程式庫

本主題描述 ODBC 資料指標程式庫，並說明如何使用它。 如需詳細資訊，請參閱:

- [資料指標程式庫和層級 1 ODBC 驅動程式](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [定位的更新 」 和 「 時間戳記資料行](#_core_positioned_updates_and_timestamp_columns)

- [使用資料指標程式庫](#_core_using_the_cursor_library)

ODBC 資料指標程式庫是位於 ODBC 驅動程式管理員和驅動程式之間的動態連結程式庫 (DLL)。 在 ODBC 詞彙中，驅動程式會維護來追蹤其位置在資料錄集資料指標。 資料指標會標記中，您已捲動資料錄集的位置，目前的記錄。

##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> 資料指標程式庫和層級 1 ODBC 驅動程式

ODBC 資料指標程式庫提供下列新功能的層級 1 的驅動程式：

- 向前及向後捲動。 因為它們已經是可捲動層級 2 的驅動程式不需要資料指標程式庫。

- 快照集的支援。 資料指標程式庫管理緩衝區，包含快照集的記錄。 這個緩衝區會反映您的程式刪除和編輯記錄，但不是新增、 刪除或編輯的其他使用者。 因此，快照集只會做為資料指標程式庫的緩衝區。 緩衝區也不會反映您自己新增項目直到您呼叫`Requery`。 動態集不會使用資料指標程式庫。

資料指標程式庫會提供快照集 （靜態資料指標） 即使它們通常不支援您的驅動程式。 如果您的驅動程式已經支援靜態資料指標，則您不需要載入的資料指標程式庫，來取得快照集支援。 如果您使用資料指標程式庫，您可以只使用快照集和順向資料錄集。 如果您的驅動程式支援動態集 （KEYSET_DRIVEN 資料指標），而且您想要使用它們，您必須不使用資料指標程式庫。 如果您想要使用快照集和動態集，您必須根據兩個不同`CDatabase`物件 （兩個不同的連接），除非您的驅動程式同時支援。

##  <a name="_core_positioned_updates_and_timestamp_columns"></a> 定位的更新 」 和 「 時間戳記資料行

> [!NOTE]
>  ODBC 資料來源是透過 MFC ODBC 類別，如本主題中所述，或透過 MFC 資料存取物件 (DAO) 類別存取。

> [!NOTE]
>  如果您的 ODBC 驅動程式支援`SQLSetPos`、 如果有的話，會使用 MFC，本主題不適用於您。

大部分的層級 1 驅動程式不支援定位的更新。 這類驅動程式必須仰賴資料指標程式庫，在這方面模擬層級 2 驅動程式的功能。 資料指標程式庫執行作業不會變更欄位的搜尋的更新模擬定位的 update 的支援。

在某些情況下，資料錄集可能包含時間戳記資料行，做為其中一個未變更的欄位。 在使用 MFC 的資料錄集，其中的資料表含有時間戳記資料行，會引發兩個的問題。

第一個問題是有關可更新的快照集時間戳記資料行之資料表上。 如果您的快照集繫結至資料表中包含時間戳記資料行，您應該呼叫`Requery`呼叫之後`Edit`和`Update`。 如果沒有，您可能會無法再次編輯同一筆記錄。 當您呼叫`Edit`，然後`Update`、 記錄寫入至資料來源和更新時間戳記資料行。 如果您不能呼叫`Requery`，在快照中記錄的時間戳記值不再符合對應資料來源上的時間戳記。 當您嘗試一次更新記錄時，資料來源可能不允許更新，因為不相符。

第二個問題是有關類別的限制[CTime](../../atl-mfc-shared/reference/ctime-class.md)搭配使用時`RFX_Date`傳輸至或從資料表的日期和時間資訊的函式。 處理`CTime`物件加諸的其他中繼資料傳輸期間的處理形式的一些額外負荷。 日期範圍的`CTime`物件可能也是相當大的限制某些應用程式。 新版`RFX_Date`函式會採用 ODBC *TIMESTAMP_STRUCT*參數，而不是`CTime`物件。 如需詳細資訊，請參閱 <<c0> `RFX_Date` 中[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)中*MFC 參考 》*。

##  <a name="_core_using_the_cursor_library"></a> 使用資料指標程式庫

當您連接到資料來源，藉由呼叫[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)或是[Openex](../../mfc/reference/cdatabase-class.md#open) — 您可以指定是否要使用資料來源的資料指標程式庫。 如果您將該資料來源上建立快照集，指定`CDatabase::useCursorLib`選項`dwOptions`參數來`OpenEx`指定為 TRUE，或*bUseCursorLib*參數`Open`（預設值是為 TRUE)。 如果您的 ODBC 驅動程式支援動態集，而且您想要開啟資料來源上的動態集，請勿使用 （它會遮罩某些驅動程式的功能所需的動態集） 資料指標程式庫。 在此情況下，未指定`CDatabase::useCursorLib`中`OpenEx`指定為 FALSE 或*bUseCursorLib*中的參數`Open`。

## <a name="see-also"></a>另請參閱

[ODBC 基本概念](../../data/odbc/odbc-basics.md)