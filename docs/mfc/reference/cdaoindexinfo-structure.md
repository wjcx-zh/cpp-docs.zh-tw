---
title: "CDaoIndexInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 92206d8d8f9b2315fb859e2712a83d32a4c293ad
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo 結構
`CDaoIndexInfo`結構包含定義資料存取物件 (DAO) 的索引物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoIndexInfo {  
    CDaoIndexInfo();
*// Constructor  
    CString m_strName;  // Primary  
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
    short m_nFields;    // Primary  
    BOOL m_bPrimary;    // Secondary  
    BOOL m_bUnique;     // Secondary  
    BOOL m_bClustered;  // Secondary  
    BOOL m_bIgnoreNulls;                // Secondary  
    BOOL m_bRequired;   // Secondary  
    BOOL m_bForeign;    // Secondary  
    long m_lDistinctCount;              // All  
 *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};   
```  
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 唯一名稱的欄位物件。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 名稱屬性 」。  
  
 `m_pFieldInfos`  
 陣列的指標[CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md)指出哪些 tabledef 或資料錄集欄位在索引中的索引鍵欄位的物件。 每個物件識別在索引中的一個欄位。 預設索引順序為遞增。 索引物件可以有一或多個代表每一筆記錄的索引鍵的欄位。 這些可以遞增、 遞減或組合。  
  
 `m_nFields`  
 儲存在中的欄位數目`m_pFieldInfos`。  
  
 *m_bPrimary*  
 如果主要屬性為**TRUE**，index 物件代表主索引鍵。 主索引鍵是由唯一識別預先定義的順序中的資料表中的所有記錄的一個或多個欄位所組成。 索引欄位必須是唯一的因為索引物件的唯一屬性也會被設**TRUE**在 DAO 中。 如果主索引鍵是由多個欄位所組成，每個欄位可以包含重複的值，但每個索引的所有欄位的值組合必須是唯一。 主要索引包含資料表的索引鍵，而通常包含主索引鍵相同的欄位。  
  
 當您將資料表的主索引鍵時，主索引鍵會自動定義為資料表的主索引。 如需詳細資訊，請參閱 「 主要屬性 」 和 DAO 說明中的 「 唯一屬性 」 主題。  
  
> [!NOTE]
>  可以有，最多一個資料表的主索引鍵。  
  
 *m_bUnique*  
 表示索引的物件是否表示資料表的唯一索引。 如果這個屬性是**TRUE**，index 物件代表的是唯一的索引。 以邏輯方式排列的資料表中唯一的預先定義順序中的所有記錄的一個或多個欄位包含唯一的索引。 如果索引包含一個欄位，該欄位中的值必須是唯一的整個資料表。 如果索引是由多個欄位所組成，每個欄位可以包含重複的值，但每個索引的所有欄位的值組合必須是唯一。  
  
 如果索引物件的唯一和主要屬性設定為**TRUE**，索引是唯一的且主要︰ 它會唯一識別預先定義的邏輯順序中的資料表中的所有記錄。 如果主要屬性設定為**FALSE**，索引是次要索引。 次要索引 （索引鍵和非索引鍵） 以邏輯方式排列預先定義的順序中的記錄，而不做為資料表中記錄的識別碼。  
  
 如需詳細資訊，請參閱 「 主要屬性 」 和 DAO 說明中的 「 唯一屬性 」 主題。  
  
 *m_bClustered*  
 表示索引的物件是否表示資料表的叢集的索引。 如果這個屬性是**TRUE**，index 物件表示非叢集的索引，否則它並不會。 叢集的索引包含一或多個非索引鍵欄位、 數位簽章排列預先定義的順序中的資料表中的所有記錄。 具有叢集索引，資料表中的資料會逐字儲存在叢集索引所指定的順序。 叢集的索引可有效率地存取資料表中的記錄。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 叢集屬性 」。  
  
> [!NOTE]
>  使用 Microsoft Jet 資料庫引擎，因為 Jet 資料庫引擎不支援叢集的索引的資料庫，會忽略 [叢集] 內容。  
  
 *m_bIgnoreNulls*  
 指出是否有 Null 值的記錄及其索引欄位的索引項目。 如果這個屬性是**TRUE**，Null 值的欄位沒有索引項目。 若要使搜尋速度使用欄位的記錄，您可以定義欄位的索引。 如果您允許 Null 索引的欄位中的項目，而且預期許多 null 項目，您可以設定忽略 Null 屬性的索引物件的**TRUE**來減少索引所使用的儲存空間量。 忽略 Null 屬性設定和必要的屬性一起判斷是否為 Null 的索引值的記錄索引項目，如下表所示。  
  
|忽略 Null|必要項|在索引欄位為 null|  
|-----------------|--------------|-------------------------|  
|True|False|允許 null 值加入沒有索引項目。|  
|False|False|允許 null 值加入索引的項目。|  
|True 或 False|True|不允許 null 值加入沒有索引項目。|  
  
 如需詳細資訊，請參閱本主題說明 DAO 中的 「 忽略 Null 屬性 」。  
  
 `m_bRequired`  
 指出 DAO index 物件是否需要非 Null 值。 如果這個屬性是**TRUE**，index 物件不允許 Null 值。 如需詳細資訊，請參閱主題 DAO 說明中的 「 必要屬性 」。  
  
> [!TIP]
>  當您可以將這個欄位物件 （包含 tabledef、 資料錄集，或 querydef 物件） 或 DAO 索引物件的屬性時，將它設定欄位的物件。 索引物件的前，會檢查欄位物件的屬性設定的有效性。  
  
 *m_bForeign*  
 表示索引物件是否表示資料表的外部索引鍵。 如果這個屬性是**TRUE**，索引會代表資料表的外部索引鍵。 外部索引鍵是由一或多個外部資料表中唯一識別欄位的主要資料表中的資料列所組成。 Microsoft Jet 資料庫引擎會建立外部資料表的索引物件，並且設定外部索引的屬性，當您建立的強制執行參考完整性的關聯性。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 外部索引屬性 」。  
  
 *m_lDistinctCount*  
 指出索引的物件相關聯的資料表中包含的唯一值數目。 請檢查 DistinctCount 屬性，若要判斷唯一值或索引鍵數目。 任何索引鍵是只計算一次，即使如果可能會有多個項目值的索引允許重複的值。 這項資訊適用於嘗試最佳化資料存取，藉由評估索引資訊的應用程式。 唯一值的數目也就是索引物件的基數。 DistinctCount 屬性將不一定會反映實際的金鑰數目在特定時間。 例如，交易回復所造成的變更將不會立即反映在 DistinctCount 屬性。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 DistinctCount 屬性 」。  
  
## <a name="remarks"></a>備註  
 主要、 次要資料庫，且上述所有參考表示資訊由`GetIndexInfo`類別中的成員函式[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)。  
  
 索引物件不會顯示由 MFC 類別。 相反地，DAO 物件類別的基礎 MFC 物件[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)包含稱為索引集合的索引物件的集合。 這些類別提供成員函式來存取索引資訊的個別項目，或是您可以存取它們全部一次使用`CDaoIndexInfo`物件呼叫`GetIndexInfo`包含物件的成員函式。  
  
 `CDaoIndexInfo`有一個建構函式和解構函式，以便適當地配置和解除配置中的索引欄位資訊`m_pFieldInfos`。  
  
 所擷取的資訊`GetIndexInfo`tabledef 物件的成員函式會儲存在`CDaoIndexInfo`結構。 呼叫`GetIndexInfo`包含 tabledef 物件的索引集合中儲存的索引物件的成員函式。 `CDaoIndexInfo`也會定義`Dump`成員函式中偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoIndexInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)


