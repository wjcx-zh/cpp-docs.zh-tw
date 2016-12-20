---
title: "CMapStringToOb Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMapStringToOb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMapStringToOb class"
  - "集合類別, string mapping"
  - "字串 [C++], class for mapping"
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMapStringToOb Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

該字典集合的類別。 `CObject` 指標的對應唯一的 `CString` 物件。  
  
## 語法  
  
```  
class CMapStringToOb : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMapStringToOb::CMapStringToOb](../Topic/CMapStringToOb::CMapStringToOb.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMapStringToOb::GetCount](../Topic/CMapStringToOb::GetCount.md)|傳回的元素數目。這個對應的。|  
|[CMapStringToOb::GetHashTableSize](../Topic/CMapStringToOb::GetHashTableSize.md)|判斷項目的目前數目在雜湊資料表中。|  
|[CMapStringToOb::GetNextAssoc](../Topic/CMapStringToOb::GetNextAssoc.md)|取得可逐一查看的下一個項目。|  
|[CMapStringToOb::GetSize](../Topic/CMapStringToOb::GetSize.md)|傳回的元素數目。這個對應的。|  
|[CMapStringToOb::GetStartPosition](../Topic/CMapStringToOb::GetStartPosition.md)|傳回第一個項目的位置。|  
|[CMapStringToOb::HashKey](../Topic/CMapStringToOb::HashKey.md)|計算指定之索引鍵的雜湊值。|  
|[CMapStringToOb::InitHashTable](../Topic/CMapStringToOb::InitHashTable.md)|初始化雜湊資料表。|  
|[CMapStringToOb::IsEmpty](../Topic/CMapStringToOb::IsEmpty.md)|命名空間對應情況的 \(沒有項目\) 的測試。|  
|[CMapStringToOb::Lookup](../Topic/CMapStringToOb::Lookup.md)|查詢是以 null 指標索引鍵的 null 指標。  指向 ，它的索引鍵比較使用的指標值，而不是實體。|  
|[CMapStringToOb::LookupKey](../Topic/CMapStringToOb::LookupKey.md)|傳回索引鍵的參考與指定之索引鍵值。|  
|[CMapStringToOb::RemoveAll](../Topic/CMapStringToOb::RemoveAll.md)|從這個對應移除所有項目。|  
|[CMapStringToOb::RemoveKey](../Topic/CMapStringToOb::RemoveKey.md)|移除指定索引鍵的項目。|  
|[CMapStringToOb::SetAt](../Topic/CMapStringToOb::SetAt.md)|將項目插入映像;，如果找到的話，會取代任何現有項目相符的金鑰。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CMapStringToOb::operator](../Topic/CMapStringToOb::operator.md)|將元素插入至對應的 `SetAt`—運算子取代。|  
  
## 備註  
 一旦插入一個 `CString`\-`CObject*` 至 \(項目\) 的對應，您可以有效地擷取或刪除至使用字串或 `CString` 值做為索引鍵。  您也可以逐一查看對應中的所有項目。  
  
 型別的 **位置** 變數做為替代的輸入存取使用在所有對應變化。  您可以使用 **位置** 「記住」輸入和透過對應逐一查看。  您可以把這個反覆項目的索引鍵值是連續的，它不是。  擷取的項目序列不確定。  
  
 `CMapStringToOb` 合併 `IMPLEMENT_SERIAL` 巨集支援序列化和傾印其項目。  每個項目依次序列化，如果對應儲存到檔案，則會有多載的外掛程式**\<\<**\(\) 運算子的或 `Serialize` 成員函式的。  
  
 如果您在對應 \( `CString` 值和 `CObject` 內容\) 需要個別項目的診斷傾印，您必須將傾印內容的深度為 1 或更大。  
  
 當 `CMapStringToOb` 刪除物件時，或在移除項目時，其元素，移除 `CString` 物件和 `CObject` 指標。  不會終結 `CObject` 指標所參考的物件。  
  
 對應類別衍生類似清單衍生。  針對特殊用途的清單類別衍生的圖參閱本文 [集合](../../mfc/collections.md) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## 需求  
 **Header:** afxcoll.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr Class](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord Class](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapStringToPtr Class](../../mfc/reference/cmapstringtoptr-class.md)   
 [CMapStringToString Class](../../mfc/reference/cmapstringtostring-class.md)   
 [CMapWordToOb Class](../../mfc/reference/cmapwordtoob-class.md)   
 [CMapWordToPtr Class](../../mfc/reference/cmapwordtoptr-class.md)