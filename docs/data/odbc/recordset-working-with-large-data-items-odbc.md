---
title: "資料錄集：使用大型的資料項目 (ODBC) | Microsoft Docs"
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
  - "二進位大型物件"
  - "BLOB (二進位大型物件), 資料錄集"
  - "CLongBinary 類別, 使用於資料錄集"
  - "ODBC 資料錄集, 二進位大型物件"
  - "資料錄集, 二進位大型物件"
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：使用大型的資料項目 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題適用於 MFC ODBC 類別和 MFC DAO 類別。  
  
> [!NOTE]
>  如果您正在使用 MFC DAO 類別，請使用 [CByteArray](../../mfc/reference/cbytearray-class.md) 類別來管理大型資料項目，而不要使用 [CLongBinary](../../mfc/reference/clongbinary-class.md) 類別。  如果您正在使用 MFC ODBC 類別與大量資料列擷取，請使用 `CLongBinary` 而不要使用 `CByteArray`。  如需關於大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 假設您的資料庫可儲存大型的資料片段，諸如點陣圖 \(員工照片、地圖、產品圖片、OLE 物件等等\)。  這類的資料經常以二進位大型物件 \(或 BLOB\) 引用，因為：  
  
-   每個欄位值是大型的。  
  
-   不同於數字或其他簡單的資料型別，它無法預期大小。  
  
-   從您的程式觀點，資料是不規則的。  
  
 這個主題說明資料庫類別提供給使用這類物件的支援。  
  
##  <a name="_core_managing_large_objects"></a> 管理大型物件  
 資料錄集具有兩種方法可解決管理二進位大型物件的特殊困難。  您可使用 [CByteArray](../../mfc/reference/cbytearray-class.md) 類別或 [CLongBinary](../../mfc/reference/clongbinary-class.md) 類別。  一般而言，`CByteArray` 是較好的大型二進位資料管理方法。  
  
 `CByteArray` 需要的負荷比 `CLongBinary` 多，但功能也更多，在 [CByteArray 類別](#_core_the_cbytearray_class)中有說明。  在 [CLongBinary 類別](#_core_the_clongbinary_class)中則簡短說明 `CLongBinary`。  
  
 如需以 `CByteArray` 來使用大型資料項目的詳細資訊，請參閱 [技術提示 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_cbytearray_class"></a> CByteArray 類別  
 `CByteArray` 是一種 MFC 集合類別。  `CByteArray` 物件會儲存動態的位元組陣列 \-\- 此陣列可視需要擴充。  類別與內建 C\+\+ 陣列一起，藉由索引提供快速存取。  為了診斷用途，可序列化和傾印 `CByteArray` 物件。  類別可以提供成員函式，以取得和設定特定位元組、插入和附加位元組，及移除一個位元組或所有位元組。  這些設施可以讓您更輕易地剖析二進位資料。  例如，如果二進位物件是一個 OLE 物件，您可能必須透過某些標頭位元組來觸及實質的物件。  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a> 在資料錄集中使用 CByteArray  
 您可以給定您的資料錄集一個型別為 `CByteArray` 型別的欄位資料成員，提供一個固定的基底，讓 [RFX](../../data/odbc/record-field-exchange-rfx.md) 可管理在您的資料錄集和資料來源間傳輸的這類物件，且您可透過它來處理物件內的資料。  RFX 需要一個擷取資料的特定位置，而您需要一個能存取其下資料的方法。  
  
 如需以 `CByteArray` 來使用大型資料項目的詳細資訊，請參閱 [技術提示 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_clongbinary_class"></a> CLongBinary 類別  
 [CLongBinary](../../mfc/reference/clongbinary-class.md) 物件是從 `HGLOBAL` 控制代碼到配置在堆積上的儲存體區塊附近的簡單 Shell。  當它繫結一個包含二進位大型物件的資料表資料行時，RFX 會在其需要傳輸資料至資料錄集時，配置 `HGLOBAL` 控制代碼，並在資料錄集的 `CLongBinary` 欄位內儲存控制代碼。  
  
 您可以依序使用 `HGLOBAL` 控制代碼、`m_hData`，來使用其資料，以其他控制代碼資料操作方式進行操作。  [CByteArray](../../mfc/reference/cbytearray-class.md) 在此處加入功能。  
  
> [!CAUTION]
>  CLongBinary 物件無法用來當做函式呼叫內的參數。  除此之外，它們在呼叫 **::SQLGetData** 的實作 \(Implementation\) 部分，對一個可捲動的快照集來說必然會使得捲動效能減慢。  當您自己使用 **::SQLGetData** 呼叫來擷取動態結構描述資料行時，可能也會出現這種情形。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：取得 SUM 和其他彙總結果 \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)