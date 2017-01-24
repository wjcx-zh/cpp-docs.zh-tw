---
title: "TN043：RFX 常式 | Microsoft Docs"
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
  - "RFX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RFX (資料錄欄位交換)"
  - "RFX (資料錄欄位交換), 架構"
  - "TN043"
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN043：RFX 常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個會描述資料錄欄位交換 \(RFX\) 結構。  它也說明如何撰寫 **RFX\_** 程序。  
  
## 資料錄欄位交換概觀  
 所有資料錄集欄位函式完成與 C\+\+ 程式碼。  沒有特殊資源或不需要什麼特別的巨集。  這個機制的核心是在每個衍生資料錄集類別必須覆寫的虛擬函式。  永遠會以這種形式:  
  
```  
void CMySet::DoFieldExchange(CFieldExchange* pFX)  
{  
  //{{AFX_FIELD_MAP(CMySet)  
  <recordset exchange field type call>  
  <recordset exchange function call>  
  //}}AFX_FIELD_MAP  
}  
```  
  
 特殊格式 AFX 註解允許 ClassWizard 尋找和編輯此函式中的程式碼。  程式碼與 ClassWizard 相容應該放置在特殊格式註解外。  
  
 在上述範例中， \<recordset\_exchange\_field\_type\_call\> 表單:  
  
```  
pFX->SetFieldType(CFieldExchange::outputColumn);  
```  
  
 然後 \<recordset\_exchange\_function\_call\> 表單:  
  
```  
RFX_Custom(pFX, "Col2", m_Col2);  
```  
  
 大部分 **RFX\_** 函式有三個引數如上所述，不過，陣列 \(也就是。  `RFX_Text` 和 `RFX_Binary`\) 具有不同的選擇性引數。  
  
 多個 **RFX\_** 在每個 `DoDataExchange` 函式可能包括。  
  
 為所有資料錄欄位交換常式清單參閱「afxdb.h」隨附 MFC。  
  
 資料錄集呼叫欄位是註冊記憶體位置模式 \(通常是資料成員\) 儲存欄位資料為 **CMySet** 類別。  
  
## 備註  
 資料錄集欄位函式被設計只與 `CRecordset` 類別一起使用。  它們由其他 MFC 類別通常無法使用。  
  
 原始資料在 Standard C\+\+ 建構函式設定，通常在具有 `//{{AFX_FIELD_INIT(CMylSet)` 和 `//}}AFX_FIELD_INIT` 的註解區塊。  
  
 每個 **RFX\_** 函式必須支援各種作業，範圍從傳回欄位的廢棄狀況對封存欄位為準備編輯欄位。  
  
 呼叫 `DoFieldExchange` 的每個函式 \(例如 `SetFieldNull`\)，則為 `IsFieldDirty`，在呼叫前後執行其初始設定為 `DoFieldExchange`。  
  
## 它的運作方式?  
 您不需要了解下列才能使用資料錄欄位交換。  不過，了解這項處理在幕後作業可協助您撰寫交換程序。  
  
 `DoFieldExchange` 成員函式非常類似 `Serialize` 成員函式 \(它會取得或設定從外部表單 \(在此情況下從 ODBC 查詢結果的資料行資料負責\) 從\/至類別中的成員資料。  `pFX` 參數是對資料交換內容類似 `CArchive` 參數的 `CObject::Serialize`。  `pFX` \( `CFieldExchange` 物件\) 有作業指示器，類似，不過， `CArchive` 方向旗標的一般化。  RFX 函式可能必須支援下列作業:  
  
-   **BindParam** —指示 ODBC 應該擷取參數資料的位置。  
  
-   **BindFieldToColumn** —指示 ODBC 必須擷取\/內建 outputColumn 資料的位置。  
  
-   **Fixup** —集合 **CString\/CByteArray** 長度，集合空白狀態位元  
  
-   如果值已變更，因為上呼叫，**MarkForAddNew** —標記變更  
  
-   如果值已變更，因為編輯呼叫，**MarkForUpdate** —標記變更  
  
-   **Name** —附加欄位名稱欄位標記為變更。  
  
-   **NameValue** —附加行 name\=\>「\<?」對於欄位標記為變更。  
  
-   \[**值**\] —附加「?」後面接著分隔符號，例如「，」或"  
  
-   `SetFieldDirty` —集合狀態位元已變更 \(例如變更\) 欄位  
  
-   `SetFieldNull` —集合狀態位元所表示欄位的 null 值。  
  
-   `IsFieldDirty` —傳回值已變更的狀態位元  
  
-   `IsFieldNull` —傳回值 null 狀態位元  
  
-   `IsFieldNullable` —傳回則為 true，如果欄位可能表示 null 值。  
  
-   **StoreField** —封存欄位值  
  
-   **LoadField** —重新載入封存的欄位值。  
  
-   **GetFieldInfoValue** —有關欄位傳回一般資訊  
  
-   **GetFieldInfoOrdinal** —有關欄位傳回一般資訊  
  
## 使用者擴充功能。  
 有幾個方式擴充預設 RFX 機制。  您可以  
  
-   加入新的資料型別。  例如：  
  
    ```  
    CBookmark  
    ```  
  
-   加入新的交換程序 \(RFX\_???\)。  
  
    ```  
    void AFXAPI RFX_Bigint(CFieldExchange* pFX, const char *szName,  
        BIGINT& value);  
    ```  
  
-   有條件地使用 `DoFieldExchange` 成員函式包含額外的 RFX 呼叫或任何其他有效 C\+\+ 陳述式。  
  
    ```  
    while (posExtraFields != NULL)  
    {  
        RFX_Text(pFX, m_listName.GetNext(posExtraFields),   
            m_listValue.GetNext(posExtraValues));  
    }  
    ```  
  
> [!NOTE]
>  這類程式碼並不是由 ClassWizard 編輯，而且只能在特殊格式註解外。  
  
## 撰寫自訂 RFX  
 若要撰寫自訂 RFX 函式，建議您複製現有的 RFX 函式並修改成您的目的。  選擇正確的 RFX 複製可能讓工作更容易。  某些 RFX 函式有您應該考慮到，在決定要複製時的一些唯一的屬性。  
  
 **RFX\_Long and RFX\_Int**:  
 這些是最簡單的 RFX 函式。  資料值不需要任何特殊解譯，因此，資料大小是固定的。  
  
 **RFX\_Single and RFX\_Double**:  
 與上面 RFX\_Long 和 RFX\_Int，這些函式是簡單，而且可能會廣泛地使用預設實作。  才明確參考時，會在 dbflt.cpp 儲存而不是 dbrfx.cpp，然而，讓載入執行階段浮點程式庫。  
  
 **RFX\_Text and RFX\_Binary**:  
 這兩個函式預先配置一個靜態緩衝區保存字串\/二進位資訊，而且必須向 ODBC SQLBindCol 的這些緩衝區而非 &登錄值。  因此，這兩個函式有許多特殊大小寫程式碼。  
  
 `RFX_Date`:  
 ODBC 傳回在自己的 TIMESTAMP\_STRUCT 資料結構的日期和時間資訊。  這個函式動態配置 TIMESTAMP\_STRUCT 為「Proxy」傳送和接收的日期時間資料。  各種作業必須將日期和時間資訊在 C\+\+ `CTime` 物件和 TIMESTAMP\_STRUCT Proxy 之間。  這相當使這個函式更為複雜，不過，它是一個好的範例為資料傳輸使用 Proxy。  
  
 `RFX_LongBinary`:  
 這是不使用資料行繫結接收和傳送資料的唯一的類別庫 RFX 函式。  這個函式在修復作業期間忽略 BindFieldToColumn 作業和，，配置儲存區保存傳入的 SQL\_LONGVARCHAR 或 SQL\_LONGVARBINARY 資料，然後執行 SQLGetData 呼叫擷取值至配置儲存區。  當準備好將資料傳回值至資料來源 \(例如 NameValue 和值作業\) 時，這個函式會使用 ODBC 的 DATA\_AT\_EXEC 功能。  請參閱 [Technical Note 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) 與 SQL\_LONGVARBINARY 和 SQL\_LONGVARCHARs 一起使用的詳細資訊。  
  
 在撰寫 **RFX\_** 函式時，您通常可以使用 **CFieldExchange::Default** 實作特定作業。  請使用預設的實作該作業。  如果它執行作業中您可以委派至 **CFieldExchange::Default.**的 **RFX\_** 函式寫入您可以呼叫在 dbrfx.cpp 的 **CFieldExchange::Default** 的範例  
  
 如果傳回 false，在您的 RFX 函式的開頭呼叫 `IsFieldType` ，並立即傳回很重要。  這個機制在 **outputColumns**防止執行參數作業，反之亦然 \(像呼叫在 **outputColumn**的 **BindParam** \)。  此外， `IsFieldType` 會自動記錄計數 **outputColumns** \(`m_nFields`\) 和參數 \(`m_nParams`\)。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)