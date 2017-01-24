---
title: "CDaoIndexInfo 結構 | Microsoft Docs"
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
  - "CDaoIndexInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoIndexInfo 結構"
  - "DAO (資料存取物件), Indexes 集合"
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoIndexInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoIndexInfo` 結構中為資料存取物件定義的物件包含一個索引物件的資訊 \(DAO\)。  
  
## 語法  
  
```  
  
      struct CDaoIndexInfo {  
   CDaoIndexInfo( );                   // Constructor  
   CString m_strName;                  // Primary  
   CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
   short m_nFields;                    // Primary  
   BOOL m_bPrimary;                    // Secondary  
   BOOL m_bUnique;                     // Secondary  
   BOOL m_bClustered;                  // Secondary  
   BOOL m_bIgnoreNulls;                // Secondary  
   BOOL m_bRequired;                   // Secondary  
   BOOL m_bForeign;                    // Secondary  
   long m_lDistinctCount;              // All  
  
   // Below the // Implementation comment:  
   // Destructor, not otherwise documented  
};   
```  
  
#### 參數  
 `m_strName`  
 唯一命名欄位物件。  如需詳細資訊，請參閱本主題「Name 屬性」 DAO 說明。  
  
 `m_pFieldInfos`  
 陣列的指標 [CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md) 物件表示哪些 tabledef 或資料錄集欄位為索引鍵欄位。  每個物件會識別索引的欄位。  預設索引遞增排序。  索引物件可能會表示每個資料錄的一個或多個欄位索引鍵。  這些可以遞增，遞減或組合。  
  
 `m_nFields`  
 在 `m_pFieldInfos`中的欄位數目。  
  
 *m\_bPrimary*  
 如果主要屬性是 **TRUE**，索引物件表示主索引鍵。  主索引鍵包含兩個資料表的唯一識別所有資料錄的預先定義順序的一個或多個欄位。  由於索引欄位必須是唯一的，索引物件的唯一屬性也設為 DAO 的 **TRUE** 。  如果主索引鍵是由多個欄位，每個欄位可以包含重複的值，不過值的每個組合所有的欄位必須是唯一的。  包含主索引鍵資料表的索引鍵而且通常包含欄位和主索引鍵相同。  
  
 當您將資料表的主索引鍵，主索引鍵會自動定義為資料表的主索引鍵。  如需詳細資訊，請參閱主題 「主要屬性」和「唯一屬性」 DAO 說明。  
  
> [!NOTE]
>  在資料表最多可以有一個主索引鍵。  
  
 *m\_bUnique*  
 這個物件是否代表資料表的唯一索引。  如果這個屬性是 **TRUE**，索引物件代表是唯一索引。  唯一索引包含兩個資料表的邏輯都記錄在唯一的一個或多個欄位，預先定義的命令。  如果索引包含欄位，值會在該欄位中必須是唯一的整個資料表。  如果索引鍵是由多個欄位，每個欄位可以包含重複的值，不過值的每個組合所有的欄位必須是唯一的。  
  
 如果該物件的唯一和主要屬性設定為 **TRUE**，索引是唯一且主要的:在資料表中唯一識別所有資料錄的預先定義且有邏輯順序。  如果主要屬性設定為 **FALSE**，索引為次要索引。  次要索引 \(兩個按鍵和非索引鍵\) 在資料表中以邏輯方式將資料錄的預先定義順序，而不會有識別項做為資料錄。  
  
 如需詳細資訊，請參閱主題 「主要屬性」和「唯一屬性」 DAO 說明。  
  
 *m\_bClustered*  
 這個物件是否代表資料表的叢集索引。  如果這個屬性是 **TRUE**，索引物件代表叢集索引。  叢集索引中，一起使用時，在資料表中的所有資料錄的預先定義順序的一或多個非索引鍵欄位。  叢集索引，在資料表中的叢集索引所指定的順序會照字面進行儲存。  叢集索引提供對資料錄的有效率存取資料表中。  如需詳細資訊，請參閱本主題中的 "叢集屬性" 在 「DAO Help」 中。  
  
> [!NOTE]
>  叢集屬性為使用 Microsoft Jet 資料庫引擎的資料庫會忽略，因為 Jet 資料庫引擎不支援叢集索引。  
  
 *m\_bIgnoreNulls*  
 指示是否具有 null 值在其索引欄位之資料錄的索引標籤。  如果這個屬性是 **TRUE**，具有 null 值的欄位沒有索引標籤。  若要進行更快速搜尋記錄使用欄位，您可以定義欄位的索引。  如果您在索引資料行允許 null 輸入並預期許多項目是空的，您可以設定物件的 IgnoreNulls 屬性對 **TRUE** 減少索引使用數量的儲存空間。  設定 IgnoreNulls 的屬性和設定必要的屬性判斷具有空索引值的資料錄是否有索引標籤，如下表所示。  
  
|IgnoreNulls|必要項|空間索引欄位|  
|-----------------|---------|------------|  
|True|False|允許 null 值;不會加入的索引標籤。|  
|False|False|允許 null 值;會加入的索引標籤。|  
|True 或 False|True|不允許 null 值;不會加入的索引標籤。|  
  
 如需詳細資訊，請參閱本主題中的 「IgnoreNulls 屬性」 在 DAO Help。  
  
 `m_bRequired`  
 指示 DAO 索引物件是否需要非 null 值。  如果這個屬性是 **TRUE**，索引物件不允許 null 值。  如需詳細資訊，請參閱本主題中的 「需求屬性」在 DAO Help 中。  
  
> [!TIP]
>  當您設定 DAO 索引物件或欄位物件的這個屬性 \(包含由 tabledef、資料錄集或 querydef 物件\)，將該物件設為欄位物件。  設定為索引物件的欄位物件的屬性是否有效之前檢查。  
  
 *m\_bForeign*  
 這個物件是否在資料表中的外部索引鍵。  如果這個屬性是 **TRUE**索引，在資料表中的外部索引鍵。  外部索引鍵外部資料表包含在主要資料表中唯一識別資料列的一個或多個欄位。  Microsoft Jet 資料庫引擎建立外部資料表的索引物件並設定外部屬性，就會強制使用參考完整性的關係時。  如需詳細資訊，請參閱本主題中的「Foreign Property」在 DAO Help 中。  
  
 *m\_lDistinctCount*  
 表示在關聯資料表中包含唯一值的數目索引的物件。  在索引檢查 DistinctCount 屬性決定唯一值或索引鍵的數目。  任何鍵只一次計數，即使可能具有該值的多個項目如果索引允許重複值。  這項資訊適用於嘗試藉由評估索引資訊最佳化資料存取的應用程式。  唯一值的也稱為數目是之物件的基數。  DistinctCount 屬性在指定的時間不一定會反映索引鍵的實際數目。  例如，交易復原造成的變更不會立即反映在 DistinctCount 屬性上。  如需詳細資訊，請參閱本主題中的 「DistinctCount 屬性」 在 DAO Help。  
  
## 備註  
 對主要，次要參考和所有在指令的資訊如何由類別 [CDaoTableDef](../Topic/CDaoTableDef::GetIndexInfo.md)、 [CDaoQueryDef](../Topic/CDaoRecordset::GetIndexInfo.md)和 CDaoRecordset的 `GetIndexInfo` 成員函式所傳回。  
  
 索引物件不是由 MFC 類別表示。  相反地，基礎類別 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 中的 MFC 物件 DAO 物件中之物件的集合，稱為索引集合。  這些類別提供成員函式存取索引資訊一些個別項目也可以同時存取它們與 `CDaoIndexInfo` 物件藉由呼叫包含的 `GetIndexInfo` 物件的成員函式。  
  
 `CDaoIndexInfo` 有建構函式和一個解構函式以便適當配置和解除配置 `m_pFieldInfos`中的資料行資訊。  
  
 tabledef 物件的 `GetIndexInfo` 成員函式來擷取的資訊在 `CDaoIndexInfo` 結構中。  呼叫索引集合索引物件儲存包含的 tabledef 物件的 `GetIndexInfo` 成員函式中。  `CDaoIndexInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoIndexInfo` 物件的內容。  
  
## 需求  
 **標頭：** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)