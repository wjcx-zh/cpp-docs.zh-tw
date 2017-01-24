---
title: "CDaoFieldInfo 結構 | Microsoft Docs"
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
  - "CDaoFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoFieldInfo 結構"
  - "DAO (資料存取物件), 欄位集合"
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoFieldInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoFieldInfo` 結構中為資料存取物件定義的物件包含欄位的資訊 \(DAO\)。  
  
## 語法  
  
```  
  
      struct CDaoFieldInfo  
{  
   CString m_strName;           // Primary  
   short m_nType;               // Primary  
   long m_lSize;                // Primary  
   long m_lAttributes;          // Primary  
   short m_nOrdinalPosition;    // Secondary  
   BOOL m_bRequired;            // Secondary  
   BOOL m_bAllowZeroLength;     // Secondary  
   long m_lCollatingOrder;      // Secondary  
   CString m_strForeignName;    // Secondary  
   CString m_strSourceField;    // Secondary  
   CString m_strSourceTable;    // Secondary  
   CString m_strValidationRule; // All  
   CString m_strValidationText; // All  
   CString m_strDefaultValue;   // All  
};  
```  
  
#### 參數  
 `m_strName`  
 唯一命名欄位物件。  如需詳細資訊，請參閱本主題「Name 屬性 DAO 說明。  
  
 `m_nType`  
 表示欄位的資料型別的值。  如需詳細資訊，請參閱本主題「型別屬性」DAO 說明。  這個屬性的值可以是下列其中一項：  
  
-   是或不是，**dbBoolean**和 **TRUE**和**FALSE**  
  
-   **dbByte** 位元組  
  
-   簡短**dbInteger**  
  
-   **dbLong** Long  
  
-   **dbCurrency** 貨幣;請參閱 MFC 類別 [COleCurrency](../../mfc/reference/colecurrency-class.md)  
  
-   唯一的**dbSingle**  
  
-   **dbDouble** 雙  
  
-   **dbDate** 日期\/時間;請參閱 MFC 類別 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  
  
-   **dbText** 文字;請參閱 MFC 類別 [CString](../../atl-mfc-shared/reference/cstringt-class.md)  
  
-   **dbLongBinary** 長二進位 \(OLE 物件\);，因為 `CByteArray` 是更豐富、更容易使用，您可能要使用 MFC 類別 [CByteArray](../../mfc/reference/cbytearray-class.md) 而不是類別中的 `CLongBinary` 。  
  
-   **dbMemo** 備忘目錄;請參閱 MFC 類別 `CString`  
  
-   **dbGUID** 全域唯一識別項\/通用唯一地識別項與遠端程序呼叫。  如需詳細資訊，請參閱本主題中的「型別屬性」DAO幫助。  
  
> [!NOTE]
>  不要為二進位資料使用字串資料型別。  這會讓資料通過 Unicode\/ANSI 轉譯層，造成增加額外負荷和可能未預期的轉譯。  
  
 *m\_lSize*  
 表示的最大大小，以位元組為單位\)， DAO 欄位物件的值包含文字或固定大小的物件欄位包含文字或數值。  如需詳細資訊，請參閱本主題「大小屬性」DAO 說明。  大小可以是下列其中一個值：  
  
|型別|大小 \(位元組\)|說明|  
|--------|----------------|--------|  
|**dbBoolean**|1 個位元組|是或不是 \(和 True\/False 相同\)|  
|**dbByte**|1|Byte|  
|**dbInteger**|2|Integer|  
|**dbLong**|4|Long|  
|**dbCurrency**|8|貨幣 \([COleCurrency](../../mfc/reference/colecurrency-class.md)\)|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Double|  
|**dbDate**|8|日期\/時間 \([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)\)|  
|**dbText**|1 \- 255|文字 \([CString](../../atl-mfc-shared/reference/cstringt-class.md)\)|  
|**dbLongBinary**|0|長二進位 \(OLE 物件; [CByteArray](../../mfc/reference/cbytearray-class.md);取代 `CLongBinary`的使用\)|  
|**dbMemo**|0|備忘目錄 \([CString](../../atl-mfc-shared/reference/cstringt-class.md)\)|  
|**dbGUID**|16|dbGUID 全域唯一識別項\/通用唯一地識別項與遠端程序呼叫。|  
  
 `m_lAttributes`  
 指定 tabledef、資料錄集、querydef 或索引物件包含的欄位物件的特性。  傳回的值可以是這些常數的總和，建立 C\+\+ 位元 OR \(  **&#124;**\)運算子:  
  
-   **dbFixedField** 欄位大小都已固定 \(數字欄位的預設值\)。  
  
-   **dbVariableField** 欄位大小是變數 \(僅限文字欄位\)。  
  
-   **dbAutoIncrField** 新資料錄的欄位值就會自動將無法變更的唯一的長整數。  只支援 Microsoft Jet 資料庫資料表。  
  
-   可以變更**dbUpdatableField** 欄位值。  
  
-   **dbDescending** 欄位會依遞減 \(Z \-或 100 \- 0\) 順序排序 \(僅適用於在索引物件的欄位集合的欄位物件;在 MFC 中，索引物件本身在 tabledef 物件包含了\)。  如果省略這個常數，欄位以遞增 \(A\-Z 或 0 \- 100\) 順序 \(預設值\) 排序。  
  
 當檢查這個屬性設定時，您可以使用 C\+\+ 位元 AND 運算子 \(**&**\) 來測試特定屬性。  當設定多個屬性時，您可以透過加入適當的常數結合它們使用位元 OR \(  **&#124;**\) 運算子。  如需詳細資訊，請參閱本主題「特性屬性」DAO 說明。  
  
 *m\_nOrdinalPosition*  
 指定數值命令需要欄位的值是由顯示的 DAO 欄位所表示相對於其他欄位。  您可以使用 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)來設定此屬性。  如需詳細資訊，請參閱本主題「序號位置屬性」DAO 說明。  
  
 `m_bRequired`  
 指示 DAO 欄位物件是否需要非 null 值。  如果這個屬性是 **TRUE**，欄位不允許 null 值。  如果必須設定為 **FALSE**，欄位可能包含符合 AllowZeroLength 和 ValidationRule 屬性指定的條件設定的空值以及值。  如需詳細資訊，請參閱本主題「需要屬性」DAO 說明。  您可以設定一 tabledef 的這個屬性與 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 *m\_bAllowZeroLength*  
 表示空字串 \(""\) 是否為 DAO 欄位物件的有效值與文字或備忘中資料型別的。  如果這個屬性是 **TRUE**，空字串是有效的值。  您可以將這個屬性設定為 **FALSE** 確保您無法使用空字串設定欄位的值。  如需詳細資訊，請參閱本主題「允許零長度的屬性」DAO 說明。  您可以設定一 tabledef 的這個屬性與 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 `m_lCollatingOrder`  
 在文字指定排序順序的序列為字串比較或排序。  如需詳細資訊，請參閱本主題 \< 自訂 Windows 資料存取的登錄設定 DAO 說明。  對於可能值的清單，請傳回 [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) 結構的 **m\_lCollatingOrder** 成員。  您可以設定一 tabledef 的這個屬性與 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 `m_strForeignName`  
 位於關聯，外部資料表中指定 DAO 欄位物件名稱在主要資料表中對應欄位的值。  如需詳細資訊，請參閱本主題「外文名字屬性」DAO 說明。  
  
 *m\_strSourceField*  
 表示為資料原始來源為 tabledef、資料錄集或 querydef 物件包含的 DAO 欄位物件欄位的名稱。  這個屬性表示原始欄位名稱與欄位物件。  例如，您可以使用這個屬性決定資料的原始來源在名稱與欄位名稱是無關的在基底資料表中的查詢欄位。  如需詳細資訊，請參閱本主題 「SourceField ， SourceTable 屬性」 DAO 說明。  您可以設定一 tabledef 的這個屬性與 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 *m\_strSourceTable*  
 表示為資料原始來源為 tabledef、資料錄集或 querydef 物件包含的 DAO 欄位物件欄位的名稱。  這個屬性表示原始表名稱與欄位物件。  例如，您可以使用這個屬性決定資料的原始來源在名稱與欄位名稱是無關的在基底資料表中的查詢欄位。  如需詳細資訊，請參閱本主題 「SourceField ， SourceTable 屬性」 DAO 說明。  您可以設定一 tabledef 的這個屬性與 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 `m_strValidationRule`  
 在欄位驗證資料的值，則變更或加入資料表。  如需詳細資訊，請參閱本主題「ValidationRule 屬性」DAO 說明。  您可以設定一 tabledef 的這個屬性與 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 如需 tabledefs 的相關資訊，請參閱 [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) 結構的 **m\_strValidationRule** 成員。  
  
 `m_strValidationText`  
 指定訊息文字應用程式顯示的值，如果 DAO 欄位物件的值不符合 ValidationRule 屬性設定為指定的驗證規則。  如需詳細資訊，請參閱本主題「ValidationText 屬性」DAO 說明。  您可以設定一 tabledef 的這個屬性與 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
 *m\_strDefaultValue*  
 DAO 欄位物件的預設值。  當新資料錄時，會建立 DefaultValue 屬性設定自動輸入，欄位的值。  如需詳細資訊，請參閱本主題「DefaultValue 屬性」DAO 說明。  您可以設定一 tabledef 的這個屬性與 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md)。  
  
## 備註  
 對主要，次要參考和所有在指令的資訊如何由類別 [CDaoTableDef](../Topic/CDaoTableDef::GetFieldInfo.md)、 [CDaoQueryDef](../Topic/CDaoQueryDef::GetFieldInfo.md)和 [CDaoRecordset](../Topic/CDaoRecordset::GetFieldInfo.md)的 `GetFieldInfo` 成員函式所傳回。  
  
 欄位物件不是由 MFC 類別表示。  相反地，基礎下列類別的 MFC 物件的 DAO 參考欄位的物件的集合: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)、 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)和 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。  這些類別提供成員函式存取欄位資訊一些個別項目也可以同時存取它們與 `CDaoFieldInfo` 物件藉由呼叫包含的 `GetFieldInfo` 物件的成員函式。  
  
 除了其檢查物件的屬性使用以外，您也可以使用 `CDaoFieldInfo` 來建立新的欄位中輸入參數 tabledef 的。  較簡單的選項為這項工作才能使用，但是，如果您想要更細微的控制項，您可以使用採用 `CDaoFieldInfo` 參數之 [CDaoTableDef::CreateField](../Topic/CDaoTableDef::CreateField.md) 的版本。  
  
 `GetFieldInfo` 成員函式來擷取的資訊\(包含欄位的類別\)在 `CDaoFieldInfo` 結構中。  呼叫欄位集合欄位物件儲存所包含之物件的 `GetFieldInfo` 成員函式中。  `CDaoFieldInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoFieldInfo` 物件的內容。  
  
## 需求  
 **標頭：** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../Topic/CDaoTableDef::GetFieldInfo.md)   
 [CDaoRecordset::GetFieldInfo](../Topic/CDaoRecordset::GetFieldInfo.md)   
 [CDaoQueryDef::GetFieldInfo](../Topic/CDaoQueryDef::GetFieldInfo.md)