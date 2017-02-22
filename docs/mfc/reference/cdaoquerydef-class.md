---
title: "CDaoQueryDef Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoQueryDef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoQueryDef class"
  - "查詢 [Visual Studio], 定義"
  - "QueryDef objects"
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDaoQueryDef Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示查詢定義 querydef」或「，儲存在資料庫中的通常是一個。  
  
## 語法  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDaoQueryDef::CDaoQueryDef](../Topic/CDaoQueryDef::CDaoQueryDef.md)|**CDaoQueryDef** 建構物件。  下一個呼叫 **開啟** 或 **建立**，根據您的需求。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDaoQueryDef::Append](../Topic/CDaoQueryDef::Append.md)|querydef 附加至資料庫的 QueryDefs 集合，已儲存的查詢。|  
|[CDaoQueryDef::CanUpdate](../Topic/CDaoQueryDef::CanUpdate.md)|如果查詢可以更新資料庫，則會傳回非零。|  
|[CDaoQueryDef::Close](../Topic/CDaoQueryDef::Close.md)|關閉 querydef 物件。  當您完成使用後，請終結 C\+\+ 物件。|  
|[CDaoQueryDef::Create](../Topic/CDaoQueryDef::Create.md)|建立基礎 DAO querydef 物件。  使用 querydef 為暫存查詢或呼叫 **附加** 儲存在資料庫中。|  
|[CDaoQueryDef::Execute](../Topic/CDaoQueryDef::Execute.md)|執行 querydef 物件定義的查詢。|  
|[CDaoQueryDef::GetConnect](../Topic/CDaoQueryDef::GetConnect.md)|傳回連接字串與 querydef。  連接字串會識別資料來源。  \(為 SQL 傳遞只查詢;則為空字串\)。|  
|[CDaoQueryDef::GetDateCreated](../Topic/CDaoQueryDef::GetDateCreated.md)|傳回已儲存的查詢建立的日期。|  
|[CDaoQueryDef::GetDateLastUpdated](../Topic/CDaoQueryDef::GetDateLastUpdated.md)|傳回已儲存的查詢上次修改檔案的日期。|  
|[CDaoQueryDef::GetFieldCount](../Topic/CDaoQueryDef::GetFieldCount.md)|傳回 querydef 定義的欄位數目。|  
|[CDaoQueryDef::GetFieldInfo](../Topic/CDaoQueryDef::GetFieldInfo.md)|傳回關於在查詢定義中指定之欄位的詳細資訊。|  
|[CDaoQueryDef::GetName](../Topic/CDaoQueryDef::GetName.md)|傳回 querydef 的名稱。|  
|[CDaoQueryDef::GetODBCTimeout](../Topic/CDaoQueryDef::GetODBCTimeout.md)|傳回使用 ODBC 的逾時值 \(適用於 ODBC 查詢\)，當 querydef 執行時。  這個多久判斷所允許查詢執行的動作完成。|  
|[CDaoQueryDef::GetParameterCount](../Topic/CDaoQueryDef::GetParameterCount.md)|傳回之查詢所定義的參數數目。|  
|[CDaoQueryDef::GetParameterInfo](../Topic/CDaoQueryDef::GetParameterInfo.md)|傳回所指定的參數資訊來查詢。|  
|[CDaoQueryDef::GetParamValue](../Topic/CDaoQueryDef::GetParamValue.md)|傳回指定之參數的值指派給查詢。|  
|[CDaoQueryDef::GetRecordsAffected](../Topic/CDaoQueryDef::GetRecordsAffected.md)|傳回行動查詢影響的資料錄數目。|  
|[CDaoQueryDef::GetReturnsRecords](../Topic/CDaoQueryDef::GetReturnsRecords.md)|如果 querydef 定義查詢傳回資料錄，傳回非零。|  
|[CDaoQueryDef::GetSQL](../Topic/CDaoQueryDef::GetSQL.md)|傳回指定 querydef 定義查詢的 SQL 字串。|  
|[CDaoQueryDef::GetType](../Topic/CDaoQueryDef::GetType.md)|傳回查詢類型:刪除，更新，附加，製成資料表，依此類推。|  
|[CDaoQueryDef::IsOpen](../Topic/CDaoQueryDef::IsOpen.md)|如果 querydef 隨即開啟，而且可以執行，傳回非零。|  
|[CDaoQueryDef::Open](../Topic/CDaoQueryDef::Open.md)|開啟資料庫中的 QueryDefs 集合中所儲存的現有 querydef。|  
|[CDaoQueryDef::SetConnect](../Topic/CDaoQueryDef::SetConnect.md)|設定 SQL Pass\-Through Query\) 的連接字串在 ODBC 資料來源。|  
|[CDaoQueryDef::SetName](../Topic/CDaoQueryDef::SetName.md)|當 querydef 建立，將已儲存的查詢名稱，取代使用特定的名稱。|  
|[CDaoQueryDef::SetODBCTimeout](../Topic/CDaoQueryDef::SetODBCTimeout.md)|ODBC 使用設定的逾時值 \(適用於 ODBC 查詢\)，當 querydef 執行時。|  
|[CDaoQueryDef::SetParamValue](../Topic/CDaoQueryDef::SetParamValue.md)|設定指定之參數的值來查詢。|  
|[CDaoQueryDef::SetReturnsRecords](../Topic/CDaoQueryDef::SetReturnsRecords.md)|指定 querydef 是否傳回資料錄。  設定為 **是** 的這個屬性為 SQL Pass\-Through Query\) 才有效。|  
|[CDaoQueryDef::SetSQL](../Topic/CDaoQueryDef::SetSQL.md)|設定指定 querydef 定義查詢的 SQL 字串。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDaoQueryDef::m\_pDAOQueryDef](../Topic/CDaoQueryDef::m_pDAOQueryDef.md)|為 OLE 介面的指標基礎 DAO querydef 物件的。|  
|[CDaoQueryDef::m\_pDatabase](../Topic/CDaoQueryDef::m_pDatabase.md)|與關聯的 `CDaoDatabase` querydef 物件的指標。  querydef 可能儲存在資料庫中。|  
  
## 備註  
 querydef 是包含 SQL 陳述式會描述查詢及其屬性，例如「建立日期」和「ODBC 逾時的資料存取物件」。您也可以建立暫存 querydef 物件，而不需儲存它們，不過， —、更有效率—很方便儲存在資料庫中通常會重複使用的查詢。  [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 物件維護集合，所以呼叫 QueryDefs 集合，包含儲存的 querydefs。  
  
> [!NOTE]
>  DAO 資料庫類別會根據 Open 開放式資料庫連接的 MFC 資料庫類別本身不同 \(ODBC\)。  所有 DAO 資料庫類別名稱中有「CDao」前置詞。  您仍然可以存取使用 DAO 類別的 ODBC 資料來源。  一般而言，根據的 MFC DAO 類別比 ODBC 架構的 MFC 類別功能;以 DAO 類別的類別可以存取資料，包括透過 ODBC 驅動程式，將它們自己的資料庫引擎。  DAO 架構的類別會透過類別也支援資料定義語言 \(DDL\) \(DDL\) 作業，例如，加入資料表，而不需要直接呼叫 DAO。  
  
## 使用方式  
 使用 querydef 物件使用現有的已儲存查詢來使用或建立新的已儲存查詢或暫存查詢:  
  
1.  在所有情況下，請先 `CDaoQueryDef` 建構物件，提供指標的查詢 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 所屬的物件。  
  
2.  然後根據執行下列動作，您需要:  
  
    -   若要使用現有儲存查詢，呼叫 [開啟](../Topic/CDaoQueryDef::Open.md) querydef 物件的成員函式，提供已儲存查詢的名稱。  
  
    -   若要建立新的已儲存查詢，請呼叫 [建立](../Topic/CDaoQueryDef::Create.md) querydef 物件的成員函式，提供查詢的名稱。  然後呼叫 [附加](../Topic/CDaoQueryDef::Append.md) 透過附加它將查詢儲存至資料庫中的 QueryDefs 集合。  **建立** querydef 放至處於開啟狀態，因此，在呼叫 **建立** 之後您就不會呼叫 **開啟**。  
  
    -   若要建立暫時 querydef，請呼叫 **建立**。  透過查詢名稱的空字串。  不要呼叫 **附加**。  
  
 當您完成使用 querydef 物件時，請呼叫其成員函式， [關閉](../Topic/CDaoQueryDef::Close.md) 然後終結 querydef 物件。  
  
> [!TIP]
>  最簡單的方法來建立已儲存的查詢會建立資料並儲存在資料庫中使用 Microsoft Access。  然後您可以開啟和使用它們以 MFC 程式碼。  
  
## 目的  
 您可以執行下列任何用途 querydef 物件:  
  
-   建立物件 `CDaoRecordset`  
  
-   呼叫物件的成員函式 **執行** 直接執行動作查詢或 SQL Pass\-Through Query\)  
  
 您可以為任何類型的查詢使用 querydef 物件，包括選取、，動作、crosstab、刪除、更新、附加，製成資料表、資料定義、SQL 傳遞、等位和大量查詢。  查詢類型視您提供 SQL 陳述式的內容。  如需查詢類型的詳細資訊，請參閱 **執行** 和 [GetType](../Topic/CDaoQueryDef::GetType.md) 成員函式。  資料錄集的資料列傳回的查詢，通常這些通常會使用 **選取…以關鍵字。 執行** 提供大量作業是最常用的方式。  如需詳細資訊，請參閱 [執行](../Topic/CDaoQueryDef::Execute.md) 和 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
## Querydefs 和資料錄集  
 若要使用 querydef 物件建立 `CDaoRecordset` 物件，您通常會建立或開啟上述 querydef。  然後，當您呼叫時，請 [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md)建構資料錄集物件，將指標傳遞至 querydef 物件。  您傳入的 querydef 必須處於開啟狀態。  如需詳細資訊，請參閱類別 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 您不能使用 querydef 建立資料錄集 \(最常見的 querydef\)，除非它是處於開啟狀態。  釋放 querydef 入處於開啟狀態藉由呼叫 **開啟** 或 **建立**。  
  
## 外部資料庫  
 Querydef 物件的慣用方法是使用外部資料庫引擎的原生 SQL 用語。  例如，您可以在 querydef 物件可以建立 Transact SQL 查詢 \(如使用 Microsoft SQL Server\) 並儲存它。  當您需要使用以 Microsoft Jet 資料庫引擎時的 SQL 查詢，您必須提供指向外部資料來源的連接字串。  使用有效的連接字串的查詢略過資料庫引擎和透過查詢直接加入至處理常式的外部資料庫伺服器。  
  
> [!TIP]
>  比較好的方法使用 ODBC 使用表格會附加至 Microsoft Jet \(.MDB\) 資料庫。  
  
 如需相關資訊，請參閱\< QueryDef 物件」， QueryDefs 集合」和「物件」CdbDatabase DAO SDK。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)