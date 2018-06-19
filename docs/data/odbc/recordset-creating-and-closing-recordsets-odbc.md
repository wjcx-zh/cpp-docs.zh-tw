---
title: 資料錄集： 建立和關閉資料錄集 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bbf020e12151e666aa8f88098865b1624403b828
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092098"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>資料錄集：建立和關閉資料錄集 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 若要使用資料錄集，建構資料錄集物件，然後呼叫其**開啟**成員函式來執行資料錄集的查詢和選取的記錄。 當您完成資料錄集時，關閉並終結物件。  
  
 本主題說明：  
  
-   [何時以及如何建立資料錄集物件](#_core_creating_recordsets_at_run_time)。  
  
-   [時機和方式，您就可以限定所參數化、 篩選、 排序或鎖定資料錄集的行為](#_core_setting_recordset_options)。  
  
-   [何時以及如何關閉資料錄集物件](#_core_closing_a_recordset)。  
  
##  <a name="_core_creating_recordsets_at_run_time"></a> 在執行階段建立資料錄集  
 您可以在程式中建立資料錄集物件之前，您通常會撰寫應用程式特定資料錄集類別。 如需有關此開始步驟的詳細資訊，請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 當您需要從資料來源選取記錄時，請開啟動態集或快照的物件。 要建立的物件類型取決於您需要在您的應用程式和 ODBC 驅動程式支援的資料。 如需詳細資訊，請參閱[動態](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。  
  
#### <a name="to-open-a-recordset"></a>若要開啟資料錄集  
  
1.  建構的物件，而您`CRecordset`-衍生的類別。  
  
     您可以建構在堆積上，或函式的堆疊框架上的物件。  
  
2.  （選擇性） 修改預設的資料錄集行為。 如需可用的選項，請參閱[選項的設定資料錄集](#_core_setting_recordset_options)。  
  
3.  呼叫物件的[開啟](../../mfc/reference/crecordset-class.md#open)成員函式。  
  
 在建構函式，將傳遞指標`CDatabase`物件，或傳遞**NULL**使用暫存 framework 建構並開啟的資料庫物件會根據所傳回的連接字串[GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成員函式。 `CDatabase`物件可能已經連接到資料來源。  
  
 若要呼叫**開啟**使用 SQL 資料來源選取記錄。 所選取 （如果有的話） 的第一個記錄是目前的記錄。 此記錄的欄位的值會儲存在資料錄集物件的欄位資料成員。 如果未選取任何記錄，同時`IsBOF`和`IsEOF`成員函式會傳回 0。  
  
 在您[開啟](../../mfc/reference/crecordset-class.md#open)呼叫時，您可以：  
  
-   指定資料錄集是否為動態集或快照集。 根據預設，快照集以開啟資料錄集。 或者，您可以指定順向資料錄集，僅允許向前捲動，一次一筆記錄。  
  
     根據預設，資料錄集使用中儲存的預設型別`CRecordset`資料成員**m_nDefaultType**。 精靈撰寫程式碼以初始化**m_nDefaultType**您在精靈中選擇的資料錄集類型。 而不是接受此預設值，您可以取代另一個資料錄集類型。  
  
-   指定的字串來取代預設 SQL**選取**建構資料錄集的陳述式。  
  
-   指定資料錄集是唯讀，或附加專用。 資料錄集讓所有的更新，根據預設，但您可以限制成只加入新資料錄或您可以禁止所有的更新。  
  
 下列範例示範如何開啟唯讀快照集的物件類別`CStudentSet`，應用程式特定的類別：  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 在您呼叫後**開啟**，使用物件的成員函式和資料成員，才能使用記錄。 在某些情況下，您可能想要重新查詢，或重新整理資料錄集包含資料來源所發生的變更。 如需詳細資訊，請參閱[資料錄集： 重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。  
  
> [!TIP]
>  您在開發期間使用的連接字串可能無法與最終使用者所需的連接字串相同。 如需在這方面將您的應用程式的一般化，請參閱[資料來源： 管理連接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)。  
  
##  <a name="_core_setting_recordset_options"></a> 設定資料錄集選項  
 在建構資料錄集物件之後但在您呼叫之前**開啟**若要選取的記錄，您可能想要設定一些選項來控制資料錄集的行為。 所有的資料錄集，您可以：  
  
-   指定[篩選](../../data/odbc/recordset-filtering-records-odbc.md)來限制資料錄選取。  
  
-   指定[排序](../../data/odbc/recordset-sorting-records-odbc.md)記錄的順序。  
  
-   指定[參數](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)這樣您就可以選取使用取得，或是在執行階段計算資訊的記錄。  
  
 如果條件正確，您也可以設定下列選項：  
  
-   如果資料錄集是可更新，且支援鎖定選項，指定[鎖定](../../data/odbc/recordset-locking-records-odbc.md)更新所使用的方法。  
  
> [!NOTE]
>  若要影響資料錄選取，您必須設定這些選項之前您呼叫**開啟**成員函式。  
  
##  <a name="_core_closing_a_recordset"></a> 關閉資料錄集  
 當您完成資料錄集時，您必須處置它，並取消配置其記憶體。  
  
#### <a name="to-close-a-recordset"></a>若要關閉資料錄集  
  
1.  呼叫其[關閉](../../mfc/reference/crecordset-class.md#close)成員函式。  
  
2.  終結資料錄集物件。  
  
     如果您在宣告函式的堆疊框架上，物件會在當物件超出範圍時自動終結。 否則，請使用**刪除**運算子。  
  
 **關閉**釋出資料錄集的**HSTMT**處理。 它不會終結 c + + 物件。  
  
## <a name="see-also"></a>另請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)   
 [資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)