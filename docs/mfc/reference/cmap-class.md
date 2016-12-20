---
title: "CMap Class | Microsoft Docs"
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
  - "CMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMap class"
  - "集合類別, dictionary mapping"
  - "dictionary mapping class"
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

該字典集合的類別將唯一索引鍵的值。  
  
## 語法  
  
```  
template< class KEY, class ARG_KEY, class VALUE, class ARG_VALUE >class CMap : public CObject  
```  
  
#### 參數  
 `KEY`  
 當做索引鍵的物件類別對應。  
  
 `ARG` *\_* `KEY`  
 用來 `KEY` 引數的資料型別，通常會 `KEY`的參考。  
  
 `VALUE`  
 在對應中之物件的類別。  
  
 `ARG` *\_* `VALUE`  
 用來 `VALUE` 引數的資料型別，通常會 `VALUE`的參考。  
  
## Members  
  
### 公用結構  
  
|名稱|描述|  
|--------|--------|  
|[CMap::CPair](../Topic/CMap::CPair.md)|包含外部索引鍵值和關聯的物件值的深層巢狀結構。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMap::CMap](../Topic/CMap::CMap.md)|建構該集合索引鍵對應至值。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMap::GetCount](../Topic/CMap::GetCount.md)|傳回的元素數目。這個對應的。|  
|[CMap::GetHashTableSize](../Topic/CMap::GetHashTableSize.md)|傳回元素數目雜湊資料表中。|  
|[CMap::GetNextAssoc](../Topic/CMap::GetNextAssoc.md)|取得可逐一查看的下一個項目。|  
|[CMap::GetSize](../Topic/CMap::GetSize.md)|傳回的元素數目。這個對應的。|  
|[CMap::GetStartPosition](../Topic/CMap::GetStartPosition.md)|傳回第一個項目的位置。|  
|[CMap::InitHashTable](../Topic/CMap::InitHashTable.md)|初始化雜湊資料表並指定它的大小。|  
|[CMap::IsEmpty](../Topic/CMap::IsEmpty.md)|命名空間對應情況的 \(沒有項目\) 的測試。|  
|[CMap::Lookup](../Topic/CMap::Lookup.md)|搜尋值會對應至特定索引鍵。|  
|[CMap::PGetFirstAssoc](../Topic/CMap::PGetFirstAssoc.md)|傳回指向第一個項目。|  
|[CMap::PGetNextAssoc](../Topic/CMap::PGetNextAssoc.md)|取得指標逐一查看中的下一個項目。|  
|[CMap::PLookup](../Topic/CMap::PLookup.md)|傳回指向值符合指定之值的索引鍵。|  
|[CMap::RemoveAll](../Topic/CMap::RemoveAll.md)|從這個對應移除所有項目。|  
|[CMap::RemoveKey](../Topic/CMap::RemoveKey.md)|移除指定索引鍵的項目。|  
|[CMap::SetAt](../Topic/CMap::SetAt.md)|將項目插入映像;，如果找到的話，會取代任何現有項目相符的金鑰。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CMap::operator](../Topic/CMap::operator.md)|將元素插入至對應的 `SetAt`—運算子取代。|  
  
## 備註  
 一旦插入索引鍵\/值組中 \(項目\) 的對應，您可以有效地擷取或刪除至使用索引鍵來存取它。  您也可以逐一查看對應中的所有項目。  
  
 型別的 **位置** 變數做為輸入的替代存取。   您可以使用 **位置** 「記住」輸入和透過對應逐一查看。  您可以把這個反覆項目的索引鍵值是連續的，它不是。  擷取的項目序列不確定。  
  
 這個類別的某些成員函式的呼叫必須自訂為 `CMap` 的大部分類別會使用全域的 Helper 函式。    請參閱在 `MFC``Reference`的巨集和全域部分的 [集合類別 Helper](../../mfc/reference/collection-class-helpers.md) 。  
  
 `CMap` 覆寫 [CObject::Serialize](../Topic/CObject::Serialize.md) 支援序列化和傾印其項目。    使用 `Serialize`，如果對應儲存到檔案，每個對應項目又序列化。   `SerializeElements` Helper 函式的預設實作位元進行寫入。    如需指標集合項目的序列化資訊。 `CObject` 或其他使用者定義型別衍生的型別，請參閱 [如何：建立類型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。  
  
 如果您在對應中需要個別項目的診斷傾印 \(索引鍵和值\)，則必須將傾印內容的深度為 1 或更大。  
  
 當 `CMap` 刪除物件時，或在移除項目時，其元素，移除索引鍵和值兩者。  
  
 對應類別衍生類似清單衍生。  針對特殊用途的清單類別衍生的圖參閱本文 [集合](../../mfc/collections.md) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## 需求  
 **Header:** afxtempl.h  
  
## 請參閱  
 [MFC 範例收集](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)