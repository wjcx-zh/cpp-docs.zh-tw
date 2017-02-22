---
title: "CMapWordToOb Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMapWordToOb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "16-bit word mapping"
  - "CMapWordToOb class"
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMapWordToOb Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援 `CObject` 指標對應 16 位元金鑰的文字。  
  
## 語法  
  
```  
class CMapWordToOb : public CObject  
```  
  
## Members  
 `CMapWordToOb` 的成員函式類似於類別 [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)的成員函式。  因此相似，您可以使用成員的函式特定使用 `CMapStringToOb` 參考文件。  不論您在何處參閱 `CString` 或 **const** 指標 `char` 做為函式參數或傳回值， **字**替代。  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 例如，轉譯  
  
 `BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`  
  
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
 `CMapWordToOb` 合併 `IMPLEMENT_SERIAL` 巨集支援序列化和傾印其項目。  每個項目依次序列化，如果對應儲存到檔案，則會有多載的外掛程式**\<\<**\(\) 運算子的或 `Serialize` 成員函式的。  
  
 如果您需要傾印個別 **字**\-`CObject` 項目，您必須將傾印內容的深度為 1 或更大。  
  
 當 `CMapWordToOb` 刪除物件時，或在移除項目時，其元素，移除 `CObject` 指標。  不會終結 `CObject` 指標所參考的物件。  
  
 如需 `CMapWordToOb`的詳細資訊，請參閱本文 [集合](../../mfc/collections.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapWordToOb`  
  
## 需求  
 **Header:** afxcoll.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)