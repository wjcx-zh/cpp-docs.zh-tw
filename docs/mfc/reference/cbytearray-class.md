---
title: "CByteArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CByteArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], byte"
  - "位元組陣列"
  - "CByteArray class"
  - "MFC collection classes, 位元組陣列"
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CByteArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援動態的位元組陣列。  
  
## 語法  
  
```  
class CByteArray : public CObject  
```  
  
## Members  
 `CByteArray` 的成員函式類似於類別 [使用 CObArray](../../mfc/reference/cobarray-class.md)的成員函式。  因此相似，您可以使用成員的函式特定使用 `CObArray` 參考文件。  不論您在何處參閱 `CObject` 指標做為函式參數或傳回值，請用 **位元組**。  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 例如，轉譯  
  
 `BYTE CByteArray::GetAt( int <nIndex> ) const;`  
  
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
|[CObArray::ElementAt](../Topic/CObArray::ElementAt.md)|傳回為位元組的暫存參考在陣列中。|  
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
 `CByteArray` 合併 `IMPLEMENT_SERIAL` 巨集支援序列化和傾印其項目。  如果位元組陣列儲存到檔案，則會有多載的外掛程式**\<\<**\(\) 運算子的或 `Serialize` 成員函式中，每個項目，接著，序列化。  
  
> [!NOTE]
>  在使用陣列，請使用 `SetSize` 建立控制項的大小和配置其記憶體。  如果您不使用 `SetSize`，將項目加入至陣列會經常被重新配置和複製。  經常重新配置和複製沒有效率，而且可能分段記憶體。  
  
 如果您需要偵錯從個別項目的輸出陣列中，您必須將 `CDumpContext` 物件的深度為 1 或更大。  
  
 如需使用 `CByteArray`的詳細資訊，請參閱本文 [集合](../../mfc/collections.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CByteArray`  
  
## 需求  
 **Header:** afxcoll.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObArray Class](../../mfc/reference/cobarray-class.md)