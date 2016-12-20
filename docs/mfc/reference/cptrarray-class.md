---
title: "CPtrArray Class | Microsoft Docs"
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
  - "CPtrArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], 泛型"
  - "CPtrArray class"
  - "generic arrays"
ms.assetid: c23b87a3-bf84-49d6-a66b-61e999d0938a
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPtrArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援某些 Null 指標。  
  
## 語法  
  
```  
class CPtrArray : public CObject  
```  
  
## 成員  
 `CPtrArray` 的成員函式類似於類別 [使用 CObArray](../../mfc/reference/cobarray-class.md)的成員函式。  因此相似，您可以使用成員的函式特定使用 `CObArray` 參考文件。  不論您在何處參閱 `CObject` 指標做為函式參數或傳回值，請用指標 `void`。  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 例如，轉譯  
  
 `void* CPtrArray::GetAt( int <nIndex> ) const;`  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|建構空白陣列。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CObArray::Add](../Topic/CObArray::Add.md)|將項目加入至陣列結尾;如果需要，擴大陣列。|  
|[CObArray::Append](../Topic/CObArray::Append.md)|附加另一個陣列的陣列;如果需要，擴大陣列。|  
|[CObArray::Copy](../Topic/CObArray::Copy.md)|複製到另一個陣列的陣列;如果需要，擴大陣列。|  
|[CObArray::ElementAt](../Topic/CObArray::ElementAt.md)|傳回項目指標的暫存參考在陣列中。|  
|[CObArray::FreeExtra](../Topic/CObArray::FreeExtra.md)|釋放在目前的上限 \(Upper Bound\) 上的所有未使用的記憶體。|  
|[CObArray::GetAt](../Topic/CObArray::GetAt.md)|傳回值是在指定的索引。|  
|[CObArray::GetCount](../Topic/CObArray::GetCount.md)|取得項目的參數數目等於陣列中的。|  
|[CObArray::GetData](../Topic/CObArray::GetData.md)|允許存取項目的存取陣列中。  可以是 `NULL`。|  
|[CObArray::GetSize](../Topic/CObArray::GetSize.md)|取得項目的參數數目等於陣列中的。|  
|[CObArray::GetUpperBound](../Topic/CObArray::GetUpperBound.md)|會傳回最大的有效索引。|  
|[CObArray::InsertAt](../Topic/CObArray::InsertAt.md)|插入項目 \(或另一個檔案中的所有元素的陣列\) 中的指定索引。|  
|[CObArray::IsEmpty](../Topic/CObArray::IsEmpty.md)|判斷陣列是否是空的。|  
|[CObArray::RemoveAll](../Topic/CObArray::RemoveAll.md)|從陣列中移除所有項目。|  
|[CObArray::RemoveAt](../Topic/CObArray::RemoveAt.md)|移除項目中的特定索引處。|  
|[CObArray::SetAt](../Topic/CObArray::SetAt.md)|設定指定之索引的值;不允許的陣列成長。|  
|[CObArray::SetAtGrow](../Topic/CObArray::SetAtGrow.md)|設定指定之索引的值;如果需要，擴大陣列。|  
|[CObArray::SetSize](../Topic/CObArray::SetSize.md)|將陣列中的元素數目。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CObArray::operator](../Topic/CObArray::operator.md)|設定或取得這個項目在指定之索引處的。|  
  
## 備註  
 `CPtrArray` 合併 `IMPLEMENT_DYNAMIC` 巨集支援的執行階段型別存取和傾印至 `CDumpContext` 物件。  如果您需要個別的指標陣列元素傾印，您必須將傾印內容的深度為 1 或更大。  
  
> [!NOTE]
>  在使用陣列，請使用 `SetSize` 建立控制項的大小和配置其記憶體。  如果您不使用 `SetSize`，將項目加入至陣列會經常被重新配置和複製。  經常重新配置和複製沒有效率，而且可能分段記憶體。  
  
 指標陣列無法序列化。  
  
 當指標陣列，或刪除時，移除其元素，，才會移除參考的指標，而不是實體。  
  
 如需使用 `CPtrArray`的詳細資訊，請參閱本文 [集合](../../mfc/collections.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrArray`  
  
## 需求  
 **Header:** afxcoll.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)