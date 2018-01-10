---
title: "資料錄集： 捲動 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34dcfb9cb1d45710accba2ee6155e3c741b727be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-scrolling-odbc"></a>資料錄集：捲動 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 開啟資料錄集之後，您需要存取的記錄，來顯示值，計算、 產生報告，等等。 捲動可讓您記錄從移動資料錄集內。  
  
 本主題說明：  
  
-   [如何從一個資料錄捲動到資料錄集中的另一個](#_core_scrolling_from_one_record_to_another)。  
  
-   [內容捲動的情況下，並不支援在](#_core_when_scrolling_is_supported)。  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a>從一個資料錄捲動到另一個  
 類別`CRecordset`提供**移動**捲動資料錄集內的成員函式。 這些函式移動目前的記錄資料列集。 如果您已實作大量資料列擷取**移動**作業會資料錄集重新定位的資料列集大小。 如果您未實作大量資料列擷取，呼叫**移動**函式重新定位資料錄集的一筆記錄的每一次。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  當您移動的資料錄集，已刪除的記錄可能不會略過。 如需詳細資訊，請參閱[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成員函式。  
  
 除了**移動**函式，`CRecordset`提供成員函式檢查是否有捲動超過結尾或預先資料錄集的開頭。  
  
 若要判斷是否可捲動資料錄集，請呼叫`CanScroll`成員函式。  
  
#### <a name="to-scroll"></a>若要捲動  
  
1.  轉送一筆記錄或一個資料列集： 呼叫[MoveNext](../../mfc/reference/crecordset-class.md#movenext)成員函式。  
  
2.  向後一筆記錄或一個資料列集： 呼叫[MovePrev](../../mfc/reference/crecordset-class.md#moveprev)成員函式。  
  
3.  資料錄集中第一個記錄： 呼叫[MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)成員函式。  
  
4.  資料錄集中的最後一個記錄或最後一個資料列集： 呼叫[MoveLast](../../mfc/reference/crecordset-class.md#movelast)成員函式。  
  
5.  *N*相對於目前位置的記錄： 呼叫[移動](../../mfc/reference/crecordset-class.md#move)成員函式。  
  
#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>若要測試的結尾或資料錄集的開頭  
  
1.  您有超過最後一筆資料錄捲動嗎？ 呼叫[IsEOF](../../mfc/reference/crecordset-class.md#iseof)成員函式。  
  
2.  您有捲動預先 （向後移動） 的第一個記錄嗎？ 呼叫[IsBOF](../../mfc/reference/crecordset-class.md#isbof)成員函式。  
  
 下列程式碼範例使用`IsBOF`和`IsEOF`偵測任一方向的捲動資料錄集的限制。  
  
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
  
 `IsEOF`如果資料錄集位於過去的最後一筆記錄，則傳回非零值。 `IsBOF`如果資料錄集位於晚於第一筆記錄 （在之前的所有記錄），則傳回非零值。 在任一情況下，沒有要處理的目前記錄。 如果您呼叫`MovePrev`時`IsBOF`已經**TRUE**或呼叫`MoveNext`時`IsEOF`已經**TRUE**，架構就會擲回`CDBException`。 您也可以使用`IsBOF`和`IsEOF`檢查空的資料錄集。  
  
 如需有關資料錄集瀏覽的詳細資訊，請參閱[資料錄集： 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="_core_when_scrolling_is_supported"></a>當支援捲動  
 做為原始設計，SQL 提供僅向前捲動，但 ODBC 延伸捲動的功能。 可捲動的支援層級取決於您的應用程式的運作方式與驅動程式的 ODBC API 的一致性層級的 ODBC 驅動程式和 ODBC 資料指標程式庫會載入記憶體。 如需詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)和[ODBC: ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!TIP]
>  您可以控制是否要使用資料指標程式庫。 請參閱`bUseCursorLib`和`dwOptions`參數[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)。  
  
> [!NOTE]
>  與 MFC DAO 類別中，不同的是 MFC ODBC 類別不提供一組**尋找**尋找下一個 （或舊版） 記錄符合指定準則的函式。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)   
 [CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)   
 [資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)