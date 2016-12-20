---
title: "ODBC 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料庫類別 [C++], ODBC"
  - "ODBC 類別 [C++]"
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別和其他應用程式Framework類別一起使用以提供簡易方法存取多樣化的資料庫以使開放式資料庫連接\(ODBC\)驅動程式可供使用。  
  
 使用 ODBC 資料庫的程式會使用至少一個 `CDatabase` 物件和 `CRecordset` 物件。  
  
 [CDatabase](../mfc/reference/cdatabase-class.md)  
 封裝資料來源的連接，您可以透過這個連接來操作資料來源。  
  
 [CRecordset](../mfc/reference/crecordset-class.md)  
 封裝選取自資料來源的資料錄集。  資料錄集啟用從資料列到資料列的滾動、更新資料列\(增加，編輯和刪除資料錄\)，符合篩選條件的選取範圍，排序選取和參數化的資訊的資料錄選取範圍取得或在執行階段計算。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供一個表單檢視直接連接至資料錄集物件。  在資料錄集和資料錄檢視的控制項之間的對話資料交換 \(Dialog Data Exchange，DDX\) 機制交換資料。  就像所有表單檢視，資料錄檢視根據對話方塊樣板資源。  表示這個資料錄檢視關閉時，資料錄檢視也支援移動資料錄至資料錄集的資料錄，更新資料錄和關閉相關資料錄集。  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 例外狀況造成資料存取處理失敗。  這個類別的用途以及類別庫的例外狀況處理機制的其他例外狀況類別相同。  
  
 [CFieldExchange](../mfc/reference/cfieldexchange-class.md)  
 提供支援交換資料列欄位\(RFX\)的內容資訊，在欄位資料成員和參數資料錄集物件和相對應的資料成員交換資料表在資料來源中的資料行。  類似用於對話資料交換 \(Dialog Data Exchange，DDX\) 的 [CDataExchange](../mfc/reference/cdataexchange-class.md) 類別。  
  
## 相關類別  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 封裝控制代碼至二進位大型物件 \(BLOB\) \(BLOB\) 的儲存體，例如點陣圖。  `CLongBinary` 物件會用於處理資料庫資料表中儲存的資料物件。  
  
 [CDBVariant](../mfc/reference/cdbvariant-class.md)  
 可讓您儲存值，而不用擔心值的資料型別。  `CDBVariant` 正在追蹤目前以單位儲存的值的資料型別。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)