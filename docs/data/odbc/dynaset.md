---
title: "動態集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f0f2f7ddd4a1b4021dfff8d533bb81acd84129a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dynaset"></a>動態集
本主題描述動態集，並討論其[可用性](#_core_availability_of_dynasets)。  
  
> [!NOTE]
>  本主題適用於 MFC ODBC 類別，包括[CRecordset](../../mfc/reference/crecordset-class.md)。 在 DAO 類別中的動態集的相關資訊，請參閱[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。 在 DAO 中，您可以開啟動態類型的資料錄集。  
  
 動態集是動態屬性的資料錄集。 在其存留期中，動態資料模式 （通常稱為動態集） 中的資料錄集物件會保持與資料來源同步處理方式如下。 在多使用者環境中，其他使用者可能編輯或刪除的記錄在動態集，或將記錄新增至您的動態呈現的資料表。 您的應用程式新增或刪除資料錄集的記錄會反映在動態集。 其他使用者加入至資料表的記錄將不會反映在動態集之前呼叫重建動態集其**Requery**成員函式。 當其他使用者刪除記錄時，MFC 程式碼會略過資料錄集中的刪除作業。 捲動至受影響的記錄時，其他使用者的編輯現有的記錄變更會反映在動態集。  
  
 同樣地，編輯您對動態集的記錄會在使用中的動態集反映其他使用者。 重新查詢其動態集之前，您新增的記錄不會反映在其他使用者的動態集。 您刪除的記錄標示為 「 刪除 」 在其他使用者的資料錄集。 如果您有多個連接至相同的資料庫 (多個`CDatabase`物件)，這些連接相關聯的資料錄集具有相同狀態為其他使用者的資料錄集。  
  
 當資料必須是動態的 （例如） 為航空保留系統中，動態集是最有價值。  
  
> [!NOTE]
>  若要使用動態集，您必須的 ODBC 驅動程式支援動態集的資料來源，並不會載入 ODBC 資料指標程式庫。 如需詳細資訊，請參閱[動態集可用性](#_core_availability_of_dynasets)。  
  
 若要指定資料錄集是動態集時，傳遞**CRecordset::dynaset**的第一個參數為**開啟**資料錄集物件的成員函式。  
  
> [!NOTE]
>  可更新的動態集的 ODBC 驅動程式必須支援任一定位的 update 陳述式或**:: SQLSetPos** ODBC API 函式。 如果兩者都有支援，MFC 會使用**:: SQLSetPos**為了提高效率。  
  
##  <a name="_core_availability_of_dynasets"></a>動態集的可用性  
 MFC 資料庫類別支援動態集，如果符合下列需求：  
  
-   ODBC 資料指標程式庫 DLL 不能在使用此資料來源。  
  
     如果使用資料指標程式庫時，它會遮罩的基礎的 ODBC 驅動程式所需的動態集支援某些功能。 如果您想要使用動態集 （和 ODBC 驅動程式有動態集，所需的功能，此章節的其餘部分中所述），您可能會導致無法載入資料指標程式庫，當您建立的 MFC`CDatabase`物件。 如需詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)和[OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[開啟](../../mfc/reference/cdatabase-class.md#open)類別成員函式`CDatabase`。  
  
     在 ODBC 術語中，動態集和快照集被指資料指標。 資料指標是一種機制，用於追蹤的資料錄集中的位置。  
  
-   您的資料來源的 ODBC 驅動程式必須支援索引鍵集驅動資料指標。  
  
     索引鍵集驅動資料指標管理資料的資料表中取得和儲存一組索引鍵。 這些金鑰會用來在使用者捲動至特定資料錄時，從資料表中取得目前的資料。 若要判斷您的驅動程式是否提供這項支援，請呼叫**:: SQLGetInfo** ODBC API 函式與**SQL_SCROLL_OPTIONS**參數。  
  
     如果您嘗試開啟不含索引鍵集支援動態集，您會收到`CDBException`傳回碼值**AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED**。  
  
-   您的資料來源的 ODBC 驅動程式必須支援擴充擷取。  
  
     擴充擷取是向右捲動，以及透過您的 SQL 查詢的結果資料錄將轉送的能力。 若要判斷您的驅動程式是否支援這項功能，請呼叫**:: SQLGetFunctions** ODBC API 函式與**SQL_API_SQLEXTENDEDFETCH**參數。  
  
 如果您想更新的動態集 （或快照集，就此而言），ODBC 驅動程式必須也支援**:: SQLSetPos** ODBC API 函式或定位的更新。 **:: SQLSetPos**函式可讓 MFC 不會傳送的 SQL 陳述式更新資料來源。 如果使用這項支援，MFC 會使用它而非進行使用 SQL 更新。 若要判斷您的驅動程式是否支援**:: SQLSetPos**，呼叫**:: SQLGetInfo**與**SQL_POS_OPERATIONS**參數。  
  
 定位的更新使用 SQL 語法 (表單的**WHERE CURRENT OF** \<current >) 來識別資料來源上的資料表中的特定資料列。 若要判斷您的驅動程式是否支援定位的更新，請呼叫**:: SQLGetInfo**與**SQL_POSITIONED_STATEMENTS**參數。  
  
 一般而言，MFC 動態集 （但不是順向資料錄集） 需要以層級 2 API 一致性的 ODBC 驅動程式。 如果您的資料來源驅動程式符合層級 1 API 集，您仍然可以使用可更新和唯讀快照集和順向資料錄集，但不是使用動態集。 不過，層級 1 驅動程式可支援動態集支援擴充擷取和索引鍵集驅動資料指標。 如需有關 ODBC 一致性層級的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)。  
  
> [!NOTE]
>  如果您想要使用快照集和動態集，您必須根據兩個不同`CDatabase`物件 （兩個不同的連接）。  
  
 與快照集，使用 ODBC 資料指標程式庫中的中繼存放區維護，不同的是動態集提取記錄直接從資料來源只要在捲動到它。 這會保留原本選取由資料來源同步處理的動態集的記錄。  
  
 包含在這個版本的 Visual c + + 中的 ODBC 驅動程式清單以及取得其他驅動程式的相關資訊，請參閱[ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
## <a name="see-also"></a>請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)