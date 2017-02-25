---
title: "TN045：Long Varchar/Varbinary 的 MFC/資料庫支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN045"
  - "Varbinary 資料類型"
  - "Varchar 資料類型"
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN045：Long Varchar/Varbinary 的 MFC/資料庫支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 使用 MFC 資料庫類別，這個附註說明如何擷取並傳送 ODBC **SQL\_LONGVARCHAR** 和 **SQL\_LONGVARBINARY** 資料型別。  
  
## 長 Varchar\/Varbinary 支援概觀  
 ODBC **SQL\_LONG\_VARCHAR** 和 **SQL\_LONGBINARY** 資料型別 \(稱為這裡長的資料行\) 可以保留大量資料。  您可以處理這個資料的 3 種方式:  
  
-   繫結至 `CString`\/`CByteArray`。  
  
-   繫結至 `CLongBinary`。  
  
-   完全不繫結並不要手動擷取並不要傳送的資料值，資料庫類別無關。  
  
 三種方法各有其優缺點。  
  
 長的資料行不會對查詢的參數支援。  針對 outputColumns 只支援。  
  
## 繫結至 CString\/CByteArray 的長資料行  
 優點：  
  
 這個方法很容易了解，因此，您使用熟悉的類別一起使用。  架構提供 `CString``CFormView` 支援的 `DDX_Text`。  您有許多與 `CString` 和 `CByteArray` 類別的一般字串或集合的功能，因此，您可以控制記憶體區域所配置的記憶體數量表示資料值。  在 **Edit** 或 `AddNew` 函式呼叫期間，架構會維護欄位資料舊複本，因此，架構會自動偵測到資料的變更。  
  
> [!NOTE]
>  因為 `CString` 為研究的研究字元資料和 `CByteArray` 設計二進位資料，建議您將字元資料 \(**SQL\_LONGVARCHAR**\) 到 `CString`和二進位資料 \(**SQL\_LONGVARBINARY**\) 到 `CByteArray`。  
  
 `CString` 和 `CByteArray` 的 RFX 函式讓您覆寫配置記憶體的預設大小表示資料行的擷取值的其他引數。  請注意下列函式宣告的 nMaxLength 引數:  
  
```  
void AFXAPI RFX_Text(CFieldExchange* pFX, const char *szName,  
    CString& value, int nMaxLength = 255, int nColumnType =  
    SQL_VARCHAR);  
  
void AFXAPI RFX_Binary(CFieldExchange* pFX, const char *szName,   
    CByteArray& value,int nMaxLength = 255);  
```  
  
 如果您擷取長資料行至 `CString` 或 `CByteArray`，最大傳回的資料量為，根據預設， 255 個位元組。  任何在之外被忽略。  在這種情況下，架構會擲回例外狀況 **AFX\_SQL\_ERROR\_DATA\_TRUNCATED**。  幸運的是，您可以明確地加入至 nMaxLength 很大的值，由 **MAXINT**。  
  
> [!NOTE]
>  MFC 用來 nMaxLength 的值設定 **SQLBindColumn** 函式的本機緩衝區。  這是資料儲存區的本機緩衝區，並不會實際影響 ODBC 驅動程式傳回的資料量。  `RFX_Text` 和 `RFX_Binary` 只呼叫使用 **SQLFetch** 後端資料庫擷取資料。  每個 ODBC 驅動程式有在單一擷取可以傳回的數量的另一個限制資料。  在例外狀況 **AFX\_SQL\_ERROR\_DATA\_TRUNCATED** 中擲回的情況下，這項限制小於在 nMaxLength 設定的值上。  在這些情況下，使用 `RFX_LongBinary` 的參數不是 `RFX_Text` 或 `RFX_Binary` ，讓所有資料可以被擷取。  
  
 ClassWizard 會繫結至 **SQL\_LONGVARCHAR**`CString`或 **SQL\_LONGVARBINARY** 至 `CByteArray` 。  如果您想要將多則擷取您長度資料行的 255 個位元組，您可以提供 nMaxLength 的明確值。  
  
 當長資料行繫結至 `CString` 或 `CByteArray`，更新欄位工作與相同，會繫結至 SQL\_**VARCHAR** 或 SQL\_**VARBINARY**。  在 **Edit**期間，，當呼叫 **Update** 偵測到資料值的變更並正確時，設定資料行的變更和 null 值快取資料值和之後進行比較。  
  
## 繫結至 CLongBinary 的長資料行  
 如果您的資料行可能包含多個 **MAXINT** 位元組資料，您可能要考慮擷取到 `CLongBinary`。  
  
 優點：  
  
 這個擷取整個長度資料行，會受到可用記憶體的決策。  
  
 缺點：  
  
 資料在記憶體中保留。  這個方法為大量資料也是高成本。  您必須呼叫繫結資料成員的 `SetFieldDirty` 可以確保欄位在 **Update** 作業中。  
  
 如果您擷取的資料列插入 `CLongBinary`，資料庫類別會檢查長度資料行的總大小，則配置足夠大 `HGLOBAL` 記憶體中保留它整個資料值。  資料庫類別會擷取整個資料值寫入配置 `HGLOBAL`。  
  
 如果資料來源不能傳回 LONG 資料行所需的大小，架構會擲回例外狀況 **AFX\_SQL\_ERROR\_SQL\_NO\_TOTAL**。  如果嘗試將 `HGLOBAL` 失敗，標準記憶體擲回例外狀況。  
  
 ClassWizard 會繫結 **SQL\_LONGVARCHAR** 和 **SQL\_LONGVARBINARY** 至 `CLongBinary` 。  做為變數選取 `CLongBinary` 輸入加入成員變數的對話方塊。  ClassWizard 會將呼叫 `RFX_LongBinary` 加入至 `DoFieldExchange` 呼叫並將繫結欄位總數。  
  
 要更新的資料列值，請先確定配置 `HGLOBAL` 夠大呼叫 `CLongBinary`的 `m_hData` 成員的 **::GlobalSize** 保留您的新資料。  如果它太小，請將 `HGLOBAL` 並指派適當的大小。  然後反映新大小的 `m_dwDataLength` 。  
  
 否則，則為，如果 `m_dwDataLength` 大於您取代資料的大小，您可以釋放指派給 `HGLOBAL`，或是讓它配置。  確定表示用於 `m_dwDataLength`實際位元組數目。  
  
## 更新 CLongBinary 的運作方式  
 您並不需要知道更新 `CLongBinary` 的運作方式，不過，有助於個體如何傳送長度資料值至資料來源，因此，如果您選取這個第三個方法，如下。  
  
> [!NOTE]
>  為了在更新中的 `CLongBinary` 欄位，您必須明確呼叫欄位的 `SetFieldDirty` 。  如果您對欄位的任何變更，包括設定為 null，則必須呼叫 `SetFieldDirty`。  您也必須呼叫 `SetFieldNull`，第二個參數是 **FALSE**，標記欄位做為其值。  
  
 當更新 `CLongBinary` 欄位，資料庫類別使用 ODBC 的 **DATA\_AT\_EXEC** 機制時 \(請參閱 **SQLSetPos** rgbValue 引數的 ODBC 文件\)。  當架構準備插入或更新陳述式，而不是指向包含的 `HGLOBAL` 資料， `CLongBinary` 的 *位址* 設定為資料行的 *值* 和長度指標設定為 **SQL\_DATA\_AT\_EXEC**。  之後，在中，當更新陳述式傳送至資料來源， **SQLExecDirect** 會傳回 **SQL\_NEED\_DATA**。  這個警告架構 param 指出這行的實際上是 `CLongBinary`的位址。  這個框架呼叫一次 **SQLGetData** 少緩衝區，預期驅動程式傳回資料的實際長度。  如果驅動程式傳回二進位大型物件 \(BLOB\) 的實際長度， MFC 會視需要重新配置所需空間擷取 BLOB。  如果資料來源傳回 **SQL\_NO\_TOTAL**，表示它無法判斷 BLOB 的大小， MFC 會建立較小的區塊。  預設初始大小是 64K，然後，後續的區塊會為兩倍大小;例如，第二個會 128K，第三個是 256K，依此類推。  初始大小是可設定的。  
  
## 不繫結:資料擷取\/傳送直接從與 SQLGetData 的 ODBC  
 這個方法就會略過資料庫類別和處理與長度的資料行。  
  
 優點：  
  
 必要時，您可以快取到磁碟，或者動態地決定要擷取的資料。  
  
 缺點：  
  
 您無法取得框架的 **Edit** 或 `AddNew` 支援，因此，您必須來執行基本功能撰寫程式碼 \(**Delete** 雖然運作，，因為它不是資料列層級作業\)。  
  
 在這種情況下，長度資料行必須在資料錄集選取清單，不過，不應該繫結至由架構。  一種方式是提供您的 SQL 陳述式將 `GetDefaultSQL` 或做為 lpszSQL 引數給 `CRecordset`**Open** 函式和不繫結額外的資料行與 RFX\_ 函式呼叫。  ODBC 要求未繫結的欄位以繫結欄位右邊，因此，加入未繫結的資料列或資料行加入至結尾的 SELECT 清單。  
  
> [!NOTE]
>  由於您的資料行不會由架構繫結，對它所做的變更不會處理與呼叫 `CRecordset::Update` 。  您必須建立和傳送必要的 SQL **INSERT** 和 **UPDATE** 陳述式。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)