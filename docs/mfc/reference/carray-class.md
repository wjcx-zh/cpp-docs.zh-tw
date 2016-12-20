---
title: "CArray Class | Microsoft Docs"
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
  - "CArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], 類別"
  - "CArray class"
  - "集合類別, template-based"
  - "範本, 集合類別"
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

就像 C 陣列的陣列支援，不過，可動態地減少並視需要增加。  
  
## 語法  
  
```  
template < class TYPE, class ARG_TYPE = const TYPE& >   
class CArray :   
   public CObject  
```  
  
#### 參數  
 `TYPE`  
 指定物件類型的範本參數陣列中儲存的值。  `TYPE` 由 `CArray`傳回的參數。  
  
 `ARG` *\_* `TYPE`  
 指定引數型別用於存取物件中的樣板參數陣列中儲存的值。  通常會 `TYPE`的參考。  `ARG_TYPE` 是傳遞給 `CArray`的參數。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CArray::CArray](../Topic/CArray::CArray.md)|建構空白陣列。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CArray::Add](../Topic/CArray::Add.md)|將項目加入至陣列結尾;如果需要，擴大陣列。|  
|[CArray::Append](../Topic/CArray::Append.md)|附加另一個陣列的陣列;如果需要，擴大陣列|  
|[CArray::Copy](../Topic/CArray::Copy.md)|複製到另一個陣列的陣列;如果需要，擴大陣列。|  
|[CArray::ElementAt](../Topic/CArray::ElementAt.md)|傳回項目指標的暫存參考在陣列中。|  
|[CArray::FreeExtra](../Topic/CArray::FreeExtra.md)|釋放在目前的上限 \(Upper Bound\) 上的所有未使用的記憶體。|  
|[CArray::GetAt](../Topic/CArray::GetAt.md)|傳回值是在指定的索引。|  
|[CArray::GetCount](../Topic/CArray::GetCount.md)|取得項目的參數數目等於陣列中的。|  
|[CArray::GetData](../Topic/CArray::GetData.md)|允許存取項目的存取陣列中。  可以是 **NULL**。|  
|[CArray::GetSize](../Topic/CArray::GetSize.md)|取得項目的參數數目等於陣列中的。|  
|[CArray::GetUpperBound](../Topic/CArray::GetUpperBound.md)|會傳回最大的有效索引。|  
|[CArray::InsertAt](../Topic/CArray::InsertAt.md)|插入項目 \(或另一個檔案中的所有元素的陣列\) 中的指定索引。|  
|[CArray::IsEmpty](../Topic/CArray::IsEmpty.md)|判斷陣列是否是空的。|  
|[CArray::RemoveAll](../Topic/CArray::RemoveAll.md)|從陣列中移除所有項目。|  
|[CArray::RemoveAt](../Topic/CArray::RemoveAt.md)|移除項目中的特定索引處。|  
|[CArray::SetAt](../Topic/CArray::SetAt.md)|設定指定之索引的值;不允許的陣列成長。|  
|[CArray::SetAtGrow](../Topic/CArray::SetAtGrow.md)|設定指定之索引的值;如果需要，擴大陣列。|  
|[CArray::SetSize](../Topic/CArray::SetSize.md)|將陣列中的元素數目。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CArray::operator](../Topic/CArray::operator.md)|設定或取得這個項目在指定之索引處的。|  
  
## 備註  
 陣列索引永遠從位置 0 開始。  當您將傳遞目前繫結的項目時，您可以決定是否修正此上限或讓陣列展開。  記憶體連續配置給這個上限，，即使有些項目是空的。  
  
> [!NOTE]
>  調整大小 `CArray` 物件或將項目加入至使用 [memcpy\_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) 至移動項目的方法。  這會造成問題，因為 `memcpy_s` 與需要建構函式呼叫的任何物件相容。  如果在 `CArray` 的項目與 `memcpy_s`相容，您必須建立適當大小的新 `CArray` 。  因為這些方法會使用一個指派運算子 \(而不是 `memcpy_s`，您必須使用 [CArray::Copy](../Topic/CArray::Copy.md) 和 [CArray::SetAt](../Topic/CArray::SetAt.md) 填入新陣列。  
  
 與 C 語言 . 陣列， `CArray` 索引項目的存取時間是常數也是陣列大小無關。  
  
> [!TIP]
>  在使用陣列，請使用 [SetSize](../Topic/CArray::SetSize.md) 建立控制項的大小和配置其記憶體。  如果您不使用 `SetSize`，將項目加入至陣列會經常被重新配置和複製。  經常重新配置和複製沒有效率，而且可能分段記憶體。  
  
 如果您在陣列需要個別項目傾印，您必須設定 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 物件的深度為 1 或更大。  
  
 這個類別的某些成員函式的呼叫必須自訂為 `CArray` 的大部分類別會使用全域的 Helper 函式。  請參閱在 MFC 巨集和全域章節中的主題 [集合類別 Helper](../../mfc/reference/collection-class-helpers.md) 。  
  
 陣列類似類別的衍生清單衍生。  
  
 如需如何使用 `CArray`的詳細資訊，請參閱本文 [集合](../../mfc/collections.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## 需求  
 `Header:` afxtempl.h  
  
## 請參閱  
 [MFC 範例收集](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)   
 [集合類別 Helper](../../mfc/reference/collection-class-helpers.md)