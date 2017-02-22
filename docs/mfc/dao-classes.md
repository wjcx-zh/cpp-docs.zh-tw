---
title: "DAO 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "DAO [C++], 類別"
  - "資料庫類別 [C++], DAO"
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# DAO 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別與其他應用程式架構類別一起使用使的存取資料存取物件 \(DAO\) 資料庫變的簡易，它使用 Microsoft Visual Basic 和 Microsoft Access 相同的資料庫引擎。  DAO 類別也可以存取多種不同 Open Database Connectivity \(ODBC\) 驅動程式可供使用的資料庫。  
  
 使用 DAO 資料庫的程式會使用至少一個 `CDaoDatabase` 物件和 `CDaoRecordset` 物件。  
  
> [!NOTE]
>  從 Visual C\+\+ .NET 開始，Visual C\+\+ 環境和精靈不再支援 DAO \(但該版本中仍包含 DAO 類別，您仍然可以使用這些類別\)。  Microsoft 建議於新 MFC 專案使用 ODBC。  請在維護現有應用程式時再使用 DAO。  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 從登入到登出，管理受密碼保護的具名資料庫工作階段。  大部分程式使用預設工作區。  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 您可以透過資料庫的連接來操作資料。  
  
 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)  
 表示選取自資料來源的資料錄集。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 在控制項中顯示資料庫記錄的檢視。  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 表示查詢定義，通常是儲存在資料庫中的定義。  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 表示儲存的基底資料表或附加資料表定義。  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 表示 DAO 類別引發的例外狀況。  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 \(DFX\) 常式。  您不會直接使用這個類別。  
  
## 相關類別  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 封裝控制代碼至二進位大型物件 \(BLOB\) \(BLOB\) 的儲存體，例如點陣圖。  `CLongBinary` 物件會用於處理資料庫資料表中儲存的資料物件。  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 OLE Automation 型別的 **CURRENCY** 的包裝函式，定點算術型別，它在小數點前有 15 位數及之後有 4 位數。  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 OLE Automation 型別 **DATE**的包裝函式。  表示日期和時間值。  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 OLE Automation 型別 **VARIANT**的包裝函式。  在 **VARIANT**的資料可以用許多格式加以儲存。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)