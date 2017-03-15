---
title: "資料錄集：建立和關閉資料錄集 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 資料錄集, 關閉"
  - "ODBC 資料錄集, 建立"
  - "ODBC 資料錄集, 開啟"
  - "資料錄集, 關閉"
  - "資料錄集, 建立"
  - "資料錄集, 開啟"
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：建立和關閉資料錄集 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 若要使用資料錄集，請建構資料錄集物件，再呼叫其 **Open** 成員函式來執行資料錄集的查詢和選取資料錄。  在您用完資料錄集時，請關閉並終結該物件。  
  
 這個主題說明：  
  
-   [建立資料錄集物件的時機和方法](#_core_creating_recordsets_at_run_time)。  
  
-   [藉由參數化、篩選、排序或鎖定資料錄集來限定資料錄集行為的時機和方法](#_core_setting_recordset_options)。  
  
-   [關閉資料錄集物件的時機和方法](#_core_closing_a_recordset)。  
  
##  <a name="_core_creating_recordsets_at_run_time"></a> 在執行階段建立資料錄集  
 在您能於程式中建立資料錄集物件之前，通常您需要編寫特定應用程式的資料錄集類別。  如需這個初步步驟的詳細資訊，請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 當您需要選取資料來源的資料錄時，請開啟一個動態集 \(Dynaset\) 或快照集 \(Snapshot\) 物件。  建立物件的類型將根據您需要在應用程式中處理資料的方式，和您的 ODBC 驅動程式的支援型態。  如需詳細資訊，請參閱[動態集 \(Dynaset\)](../../data/odbc/dynaset.md) 和[快照集 \(Snapshot\)](../../data/odbc/snapshot.md)。  
  
#### 若要開啟資料錄集  
  
1.  建構您的 `CRecordset` 衍生類別的物件。  
  
     您可在函式的堆積 \(Heap\) 或堆疊框架 \(Stack Frame\) 上建構物件。  
  
2.  選擇性地修改預設的資料錄集行為。  如需可用選項的詳細資訊，請參閱[設定資料錄集選項](#_core_setting_recordset_options)。  
  
3.  呼叫物件的 [Open](../Topic/CRecordset::Open.md) 成員函式。  
  
 在建構函式中，傳遞 `CDatabase` 物件的指標，或傳遞 **NULL** 以使用暫時的資料庫物件，架構將根據 [GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md) 成員函式所傳回的連接字串來建構和開啟該物件。  `CDatabase` 物件可能已經連接至資料來源。  
  
 對 **Open** 的呼叫會使用 SQL 選取資料來源的資料錄。  第一個選取的資料錄 \(如果有的話\) 是目前資料錄。  這筆資料錄的欄位值會儲存在資料錄集物件的欄位資料成員中。  若選取到任何一筆資料錄，`IsBOF` 和 `IsEOF` 成員函式都會傳回 0。  
  
 在 [Open](../Topic/CRecordset::Open.md) 呼叫中，您可以：  
  
-   指定資料錄集為動態集或快照集。  資料錄集會預設地開啟成快照集。  或者您可以指定順向資料錄集，此資料錄集僅允許向前捲動，一次一個資料錄。  
  
     預設情形是，資料錄集會使用儲存於 `CRecordset` 資料成員 **m\_nDefaultType** 內的預設類型。  精靈會編寫程式碼來初始化您在精靈中選擇的資料錄集之 **m\_nDefaultType**。  您也可以不接受此預設類型，而以其他資料錄集類型替代。  
  
-   指定一個字串來取代資料錄集所建構的預設 SQL **SELECT** 陳述式。  
  
-   指定資料錄集是唯讀或僅能附加的。  資料錄集是預設成可允許所有的更新，但您將其限制成只能加入新資料錄，或是禁止所有的更新。  
  
 下面範例顯示如何開啟 `CStudentSet` 類別 \(特定應用程式類別\) 的唯讀快照集物件：  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 呼叫 **Open** 之後，請以物件的成員函式和資料成員來使用資料錄。  在某些情況下，您可能想要重新查詢或重新整理資料錄集，以便包含已經發生的資料來源變更。  如需詳細資訊，請參閱[資料錄集：重新查詢資料錄集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。  
  
> [!TIP]
>  您在開發時使用的連接字串可能不會與最後使用者所需的連接字串相同。  如需依照此方式一般化應用程式的詳細資訊，請參閱[資料來源：管理連接 \(ODBC\)](../../data/odbc/data-source-managing-connections-odbc.md)。  
  
##  <a name="_core_setting_recordset_options"></a> 設定資料錄集選項  
 在建構您的資料錄集物件之後，而在呼叫 **Open** 以選取資料錄之前，您可能會希望先設定某些選項，以控制資料錄集的行為。  對於所有的資料錄集，您可以：  
  
-   指定[篩選條件](../../data/odbc/recordset-filtering-records-odbc.md)來限制資料錄選取範圍。  
  
-   指定資料錄的[排序](../../data/odbc/recordset-sorting-records-odbc.md)順序。  
  
-   指定[參數](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，以便使用在執行階段取得或計算出來的資訊來選取資料錄。  
  
 若條件成立，您也可設定下列選項：  
  
-   若資料錄集是可更新的且支援鎖定選項，請指定使用於更新的[鎖定](../../data/odbc/recordset-locking-records-odbc.md)方法。  
  
> [!NOTE]
>  若要影響資料錄選擇，您必須在呼叫 **Open** 成員函式之前先設定這些選項。  
  
##  <a name="_core_closing_a_recordset"></a> 關閉資料錄集  
 當您用完資料錄集，您必須為其配置，並解除其記憶體配置。  
  
#### 若要關閉資料錄集  
  
1.  呼叫它的 [Close](../Topic/CRecordset::Close.md) 成員函式。  
  
2.  終結資料錄集物件。  
  
     若您是在函式的堆疊框架上宣告這個物件，則當物件超出範圍時，其會自動地終結。  否則，請使用 **delete** 運算子。  
  
 **Close** 會釋放資料錄集的 **HSTMT** 控制代碼。  它不會終結 C\+\+ 物件。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：捲動 \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md)   
 [資料錄集：加入、更新和刪除資料錄 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)