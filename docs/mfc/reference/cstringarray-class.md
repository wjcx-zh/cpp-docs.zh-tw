---
title: "CStringArray Class | Microsoft Docs"
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
  - "CStringArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], 字串"
  - "CStringArray class"
  - "string arrays"
  - "字串 [C++], 集合"
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援 [CString](../../atl-mfc-shared/using-cstring.md) 物件的陣列。  
  
## 語法  
  
```  
class CStringArray : public CObject  
```  
  
## Members  
 `CStringArray` 的成員函式類似於 [CObArray](../../mfc/reference/cobarray-class.md) 類別的成員函式。  由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。  無論在何處看到 `CObject` 指標做為傳回值，請取代 [CString](../../atl-mfc-shared/using-cstring.md) 物件 \(而不是 [CString](../../atl-mfc-shared/using-cstring.md) 指標\)。  無論在何處看到 `CObject` 指標做為函式參數，請取代 `LPCTSTR`。  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 例如，轉換為  
  
 `CString CStringArray::GetAt( int <nIndex> ) const;`  
  
 和  
  
 `void SetAt( int <nIndex>, CObject* <newElement> )`  
  
 轉換為  
  
 `void SetAt( int <nIndex>, LPCTSTR <newElement> )`  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|建構空陣列。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CObArray::Add](../Topic/CObArray::Add.md)|將項目加入至陣列結尾；必要時讓陣列增長。|  
|[CObArray::Append](../Topic/CObArray::Append.md)|將其他陣列附加至該陣列；必要時讓陣列成長。|  
|[CObArray::Copy](../Topic/CObArray::Copy.md)|將其他陣列複製到該陣列；必要時讓陣列成長。|  
|[CObArray::ElementAt](../Topic/CObArray::ElementAt.md)|傳回陣列中項目指標的臨時參考。|  
|[CObArray::FreeExtra](../Topic/CObArray::FreeExtra.md)|釋放超過目前上限的所有未使用記憶體。|  
|[CObArray::GetAt](../Topic/CObArray::GetAt.md)|傳回給定索引的值。|  
|[CObArray::GetCount](../Topic/CObArray::GetCount.md)|取得此陣列中項目的數目。|  
|[CObArray::GetData](../Topic/CObArray::GetData.md)|容許存取陣列中的項目。  可以是 **NULL**。|  
|[CObArray::GetSize](../Topic/CObArray::GetSize.md)|取得此陣列中項目的數目。|  
|[CObArray::GetUpperBound](../Topic/CObArray::GetUpperBound.md)|傳回最大的有效索引。|  
|[CObArray::InsertAt](../Topic/CObArray::InsertAt.md)|在指定索引處插入項目 \(或其他陣列中的所有項目\)。|  
|[CObArray::IsEmpty](../Topic/CObArray::IsEmpty.md)|判定陣列是否是空的。|  
|[CObArray::RemoveAll](../Topic/CObArray::RemoveAll.md)|從此陣列移除所有項目。|  
|[CObArray::RemoveAt](../Topic/CObArray::RemoveAt.md)|移除特定索引處的項目。|  
|[CObArray::SetAt](../Topic/CObArray::SetAt.md)|設定給定索引的值；不容許陣列成長。|  
|[CObArray::SetAtGrow](../Topic/CObArray::SetAtGrow.md)|設定給定索引的值；必要時讓陣列成長。|  
|[CObArray::SetSize](../Topic/CObArray::SetSize.md)|設定此陣列中要包含的項目數目。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CObArray::operator](../Topic/CObArray::operator.md)|設定或取得指定索引處的項目。|  
  
## 備註  
 `CStringArray` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。  如果 `CString` 物件的陣列儲存至封存檔，請使用多載插入運算子或 `Serialize` 成員函式，依次對每一個項目進行序列化。  
  
> [!NOTE]
>  使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。  如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。  頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。  
  
 如果您需要傾印陣列中的個別字串項目，則您必須將傾印內容的深度設定為 1 或更大。  
  
 當刪除 `CString` 陣列，或者移除其項目時，會適當地釋放字串記憶體。  
  
 如需使用 `CStringArray` 的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringArray`  
  
## 需求  
 **標頭：**afxcoll.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)