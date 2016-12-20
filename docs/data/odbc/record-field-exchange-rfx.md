---
title: "資料錄欄位交換 (RFX) | Microsoft Docs"
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
  - "資料 [MFC]"
  - "資料 [MFC], 在來源和資料錄集之間移動"
  - "資料庫類別 [C++], RFX"
  - "ODBC [C++], RFX"
  - "RFX (ODBC) [C++]"
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄欄位交換 (RFX)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC ODBC 資料庫類別會自動在資料來源和[資料錄集](../../data/odbc/recordset-odbc.md)物件之間移動資料。  當您從 [CRecordset](../../mfc/reference/crecordset-class.md) 衍生出類別，且不使用大量資料列擷取 \(Bulk Row Fetching\) 時，資料會經由資料錄欄位交換 \(Record Field Exchange，RFX\) 機制來轉換。  
  
> [!NOTE]
>  如果您已在衍生的 `CRecordset` 類別內實作大量資料列擷取，架構就會使用大量資料錄欄位交換 \(Bulk Record Field Exchange，Bulk RFX\) 機制來轉換資料。  如需詳細資訊，請參閱文件[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 RFX 類似於對話資料交換 \(Dialog Data Exchange，DDX\)。  在資料來源和資料錄集的欄位資料成員 \(Field Data Member\) 之間移動資料，會需要多次呼叫資料錄集的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 函式，以及需要架構和 [ODBC](../../data/odbc/odbc-basics.md) 之間相當程度的互動。  RFX 機制是型別安全的且幫您省去呼叫諸如 **::SQLBindCol** 的 ODBC 函式。  如需有關 DDX 的詳細資訊，請參閱[對話資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
 RFX 大部分對您而言都是顯而易見的。  如果您使用 MFC 應用程式精靈或 **Add Class** \(如[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所說明的\) 來宣告資料錄集類別，RFX 就會自動建置 \(Build\) 於其中。  您的資料錄集類別必須衍生自架構提供的 `CRecordset` 基底類別。  MFC 應用程式精靈可讓您建立一個初始資料錄集類別。  **Add Class** 可讓您在需要其他資料錄集類別時將其加入。  如需詳細資訊和範例，請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 在三種狀況中，您必須手動加入少量的 RFX 程式碼 ─ 那就是當您想要：  
  
-   使用參數型查詢。  如需詳細資訊，請參閱[資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
-   執行聯結 \(Join\) \(對兩個以上的資料表之資料行使用一個資料錄集\)。  如需詳細資訊，請參閱[資料錄集：執行聯結 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
-   動態地繫結資料行。  這比參數化還少見。  如需詳細資訊，請參閱[資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 如果您需要進一步了解 RFX，請參閱[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 下列的主題會詳細說明使用資料錄集物件 \(Recordset Object\)：  
  
-   [資料錄欄位交換：RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [資料錄欄位交換：RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)