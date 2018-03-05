---
title: "快照集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c31e08fdda3cef526f46946e45ef956f9ad1adaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="snapshot"></a>快照
快照集是資料錄集，以反映資料的靜態檢視表存在於快照集的建立的時間。 當您開啟了快照集，並移至的所有記錄時，它所包含的記錄集合，其值不會變更之前呼叫重建快照**Requery**。  
  
> [!NOTE]
>  本主題適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別，而不 MFC ODBC 類別，請參閱[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)快照集類型的資料錄集的描述。  
  
 您可以建立可更新或唯讀快照集與資料庫類別。 不同於動態集，可更新的快照集並不會反映記錄值的其他使用者所做的變更，但它未反映更新和刪除您的程式進行。 加入至快照集的記錄不會變成可見快照直到您呼叫**Requery**。  
  
> [!TIP]
>  快照是 ODBC 靜態游標。 靜態資料指標不實際上會收到資料的列直到您捲動至該記錄。 若要確保立即擷取的所有記錄，您可以捲動資料錄集的結尾，然後捲動至您想要查看的第一個記錄。 不過請注意，，捲動到結尾牽涉到額外負荷，並會降低效能。  
  
 當您需要保持固定的作業過程，例如當您產生一份報表或執行計算的資料時，快照集是最有價值。 即便如此，資料來源可以分離大幅從快照集，因此您可能想要時常重建它。  
  
 快照集支援會根據 ODBC 資料指標程式庫，它可提供靜態資料指標並定位為任何層級 1 驅動程式 （需要可更新性） 的更新。 在記憶體中的這項支援，必須載入資料指標程式庫 DLL。 當您建構`CDatabase`物件並呼叫其`OpenEx`成員函式，您必須指定**CDatabase::useCursorLib**選項`dwOptions`參數。 如果您呼叫**開啟**成員函式，資料指標程式庫載入。 如果您使用動態集，而不快照集，您不想要載入的資料指標程式庫。  
  
 快照集是已載入 ODBC 資料指標程式庫時，才可以使用`CDatabase`建構物件，或您使用的 ODBC 驅動程式支援靜態資料指標。  
  
> [!NOTE]
>  某些 ODBC 驅動程式，可能無法更新快照集 （靜態資料指標）。 請檢查您的驅動程式文件，以支援資料指標類型和所支援的並行類型。 若要保證可更新的快照集，確定當您建立時，將記憶體載入資料指標程式庫`CDatabase`物件。 如需詳細資訊，請參閱[ODBC: ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!NOTE]
>  如果您想要使用快照集和動態集，您必須根據兩個不同`CDatabase`物件 （兩個不同的連接）。  
  
 所有的資料錄集的內容快照集共用的相關資訊，請參閱[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。 如需有關 ODBC 和快照集，包括 ODBC 資料指標程式庫，請參閱[ODBC](../../data/odbc/odbc-basics.md)。  
  
## <a name="see-also"></a>請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)