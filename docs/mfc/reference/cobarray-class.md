---
title: "CObArray Class | Microsoft Docs"
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
  - "CObArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], 物件類型"
  - "陣列 [C++], 指標"
  - "CObArray class"
  - "物件陣列, CObArray class"
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CObArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援某些 `CObject` 指標。  
  
## 語法  
  
```  
class CObArray : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CObArray::CObArray](../Topic/CObArray::CObArray.md)|建構 `CObject` 指標的空陣列。|  
  
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
|[CObArray::GetData](../Topic/CObArray::GetData.md)|允許存取項目的存取陣列中。  可以是 **NULL**。|  
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
 這些物件陣列類似於 C 陣列，但是，可以動態壓縮並視需要增加。  
  
 陣列索引永遠從位置 0 開始。  當您將傳遞目前繫結的項目時，您可以決定是否修正此上限或允許陣列展開。  記憶體連續配置給這個上限，，即使有些項目是空的。  
  
 在下， `CObArray` Win32 物件的大小只受限於可用記憶體。  
  
 與 C 語言 . 陣列， `CObArray` 索引項目的存取時間是常數也是陣列大小無關。  
  
 `CObArray` 合併 `IMPLEMENT_SERIAL` 巨集支援序列化和傾印其項目。  如果陣列 `CObject` 指標儲存到檔案，則會有多載插入運算子的或 `Serialize` 成員函式中，每個 `CObject` 項目與其陣列索引，然後，序列化。  
  
 如果您在陣列需要個別項目 `CObject` 傾印，您必須設定 `CDumpContext` 物件的深度為 1 或更大。  
  
 當 `CObArray` 刪除物件，或，在移除其元素，，才會移除參考的 `CObject` 指標，而不是物件。  
  
> [!NOTE]
>  在使用陣列，請使用 `SetSize` 建立控制項的大小和配置其記憶體。  如果您不使用 `SetSize`，將項目加入至陣列會經常被重新配置和複製。  經常重新配置和複製沒有效率，而且可能分段記憶體。  
  
 陣列類別衍生類似清單衍生。  如需在特殊清單類別衍生的詳細資訊，請參閱本文 [集合](../../mfc/collections.md)。  
  
> [!NOTE]
>  如果您想要序列化陣列，您可以在您的衍生類別的實作必須使用 `IMPLEMENT_SERIAL` 巨集。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObArray`  
  
## 需求  
 **Header:** afxcoll.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CStringArray Class](../../mfc/reference/cstringarray-class.md)   
 [CPtrArray Class](../../mfc/reference/cptrarray-class.md)   
 [CByteArray Class](../../mfc/reference/cbytearray-class.md)   
 [CWordArray Class](../../mfc/reference/cwordarray-class.md)   
 [CDWordArray Class](../../mfc/reference/cdwordarray-class.md)