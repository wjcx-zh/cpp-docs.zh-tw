---
title: "資料錄集：捲動 (ODBC) | Microsoft Docs"
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
  - "Move 方法 (資料錄集)"
  - "巡覽 [C++], 資料錄集"
  - "ODBC 資料錄集, 捲動"
  - "資料錄集 [C++], 開頭"
  - "資料錄集 [C++], 結尾"
  - "資料錄集 [C++], 移動至資料錄"
  - "資料錄集 [C++], 巡覽"
  - "捲動 [C++], 資料錄集"
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：捲動 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 在您開啟一個資料錄集後，您需要存取資料錄以便顯示其值、做計算、產生報表等作業。  捲動讓您可以在資料錄集的資料錄間移動。  
  
 這個主題說明：  
  
-   [如何在資料錄集內從一個資料錄捲動至另一個資料錄](#_core_scrolling_from_one_record_to_another)  
  
-   [各種捲動與不支援的情形](#_core_when_scrolling_is_supported)  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a> 從一個資料錄捲動至另一個資料錄  
 `CRecordset` 類別提供可在資料錄集內捲動的 **Move** 成員函式。  這些函式是依資料列集 \(Rowset\) 來移動目前的資料錄。  若您已實作大量資料列擷取，**Move** 作業會依資料列集的大小來重新定位資料錄集。  若您未實作大量資料列擷取，呼叫的 **Move** 函式每次便只會重新定位一個資料錄集。  如需關於大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  在資料錄集之間移動時，可能不會略過已刪除的資料錄。  如需詳細資訊，請參閱 [IsDeleted](../Topic/CRecordset::IsDeleted.md) 成員函式。  
  
 除了 **Move** 函式，`CRecordset` 可提供用來檢查您的捲動是否有超出資料錄集的結尾或比資料錄集的開頭還前面的成員函式。  
  
 若要決定您的資料錄集是否能夠捲動，請呼叫 `CanScroll` 成員函式。  
  
#### 若要捲動  
  
1.  向前一筆資料錄或資料列集：呼叫 [MoveNext](../Topic/CRecordset::MoveNext.md) 成員函式。  
  
2.  向後一筆資料錄或資料列集：呼叫 [MovePrev](../Topic/CRecordset::MovePrev.md) 成員函式。  
  
3.  至資料錄集的第一筆資料錄：呼叫 [MoveFirst](../Topic/CRecordset::MoveFirst.md) 成員函式。  
  
4.  至資料錄集的最後一筆資料錄或資料列集：呼叫 [MoveLast](../Topic/CRecordset::MoveLast.md) 成員函式。  
  
5.  相對於目前位置的 *N* 筆資料錄：呼叫 [Move](../Topic/CRecordset::Move.md) 成員函式。  
  
#### 若要測試資料錄集的結尾或開頭  
  
1.  您有超過最後一筆資料錄嗎？  呼叫 [IsEOF](../Topic/CRecordset::IsEOF.md) 成員函式。  
  
2.  您有捲動到第一個資料錄的前面嗎 \(往後移動\)？  呼叫 [IsBOF](../Topic/CRecordset::IsBOF.md) 成員函式。  
  
 下列的程式碼範例中使用 `IsBOF` 和 `IsEOF` 來偵測任意捲動方向時的資料錄集限制。  
  
```  
// Open a recordset; first record is current  
CCustSet rsCustSet( NULL );  
rsCustSet.Open( );  
  
if( rsCustSet.IsBOF( ) )  
    return;  
    // The recordset is empty  
  
// Scroll to the end of the recordset, past  
// the last record, so no record is current  
while ( !rsCustSet.IsEOF( ) )  
    rsCustSet.MoveNext( );  
  
// Move to the last record  
rsCustSet.MoveLast( );  
  
// Scroll to beginning of the recordset, before  
// the first record, so no record is current  
while( !rsCustSet.IsBOF( ) )  
    rsCustSet.MovePrev( );  
  
// First record is current again  
rsCustSet.MoveFirst( );  
```  
  
 如果資料錄集的位置超過最後一筆資料錄，則 `IsEOF` 會傳回非零的值。  如果資料錄集的位置是在第一筆資料錄之前 \(在所有資料錄的前面\)，`IsBOF` 也會傳回非零的值。  在這兩種狀況下，沒有目前的資料錄可作業。  如果您在 `IsBOF` 已經為 **TRUE** 時呼叫 `MovePrev`，或在 `IsEOF` 已經為 **TRUE** 時呼叫 `MoveNext`，架構就會擲回 `CDBException`。  您也可使用 `IsBOF` 和 `IsEOF` 來檢查一個空的資料錄集。  
  
 如需資料錄巡覽的詳細資訊，請參閱[資料錄集：書籤和絕對位置 \(ODBC\)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="_core_when_scrolling_is_supported"></a> 何時支援捲動  
 依照原始設計，SQL 只有提供順向捲動，但 ODBC 擴充了捲動的功能。  根據您的應用程式所使用的 ODBC 驅動程式、驅動程式的 ODBC API 一致性層級和 ODBC 資料指標程式庫 \(Cursor Library\) 是否已載入至記憶體而定，捲動的可用支援層級會有所不同。  如需詳細資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md) 和 [ODBC：ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!TIP]
>  您可控制是否使用指標 \(Cursor\) 程式庫。  請參閱 [CDatabase::Open](../Topic/CDatabase::Open.md) 的 `bUseCursorLib` 和 `dwOptions` 參數。  
  
> [!NOTE]
>  不同於 MFC DAO 類別，MFC ODBC 類別不提供一組可尋找下一個 \(或前一個\) 符合指定條件的資料錄的 **Find** 函式。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../Topic/CRecordset::CanScroll.md)   
 [CRecordset::CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)   
 [資料錄集：篩選資料錄 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)