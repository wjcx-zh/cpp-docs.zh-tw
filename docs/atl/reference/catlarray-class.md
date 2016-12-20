---
title: "CAtlArray Class | Microsoft Docs"
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
  - "ATL::CAtlArray"
  - "ATL.CAtlArray"
  - "CAtlArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlArray class"
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作陣列物件。  
  
## 語法  
  
```  
  
      template<   
   typename E,  
   class ETraits = CElementTraits< E >   
>  
class CAtlArray  
```  
  
#### 參數  
 *E*  
 在陣列中儲存的資料型別。  
  
 *ETraits*  
 程式碼會在執行複製或移動項目。  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[Add](../Topic/CAtlArray::Add.md)|呼叫這個方法將項目加入至陣列物件。|  
|[Append](../Topic/CAtlArray::Append.md)|呼叫這個方法會將陣列內容至另一個的結尾。|  
|[AssertValid](../Topic/CAtlArray::AssertValid.md)|呼叫這個方法會檢查陣列物件是有效的。|  
|[CAtlArray](../Topic/CAtlArray::CAtlArray.md)|建構函式。|  
|[~CAtlArray](../Topic/CAtlArray::~CAtlArray.md)|解構函式。|  
|[複製](../Topic/CAtlArray::Copy.md)|呼叫這個方法複製陣列中的某一個型別。|  
|[FreeExtra](../Topic/CAtlArray::FreeExtra.md)|呼叫這個方法會從陣列中移除所有空白項目。|  
|[GetAt](../Topic/CAtlArray::GetAt.md)|呼叫這個方法會從陣列物件擷取單一項目。|  
|[GetCount](../Topic/CAtlArray::GetCount.md)|呼叫這個方法會在陣列中的元素數目。|  
|[GetData](../Topic/CAtlArray::GetData.md)|呼叫這個方法會傳回指標陣列中的第一個項目。|  
|[InsertArrayAt](../Topic/CAtlArray::InsertArrayAt.md)|呼叫這個方法會將一個陣列中的。|  
|[InsertAt](../Topic/CAtlArray::InsertAt.md)|呼叫這個方法會將新的項目 \(或項目的多個複本\) 插入陣列的物件。|  
|[IsEmpty](../Topic/CAtlArray::IsEmpty.md)|如果陣列是空的，則呼叫這個方法會測試。|  
|[RemoveAll](../Topic/CAtlArray::RemoveAll.md)|呼叫這個方法會從陣列移除物件中的所有項目。|  
|[RemoveAt](../Topic/CAtlArray::RemoveAt.md)|呼叫這個方法會從陣列中移除一或多個項目。|  
|[SetAt](../Topic/CAtlArray::SetAt.md)|呼叫這個方法會設定一個項目的值在陣列的物件。|  
|[SetAtGrow](../Topic/CAtlArray::SetAtGrow.md)|呼叫這個方法會設定一個項目的值在物件的陣列，以及陣列中標記為必要欄位。|  
|[SetCount](../Topic/CAtlArray::SetCount.md)|呼叫這個方法會設定物件陣列的大小。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 &#91;&#93;](../Topic/CAtlArray::operator.md)|呼叫這個運算子會傳回的項目參考陣列中。|  
  
### Typedef  
  
|||  
|-|-|  
|[INARGTYPE](../Topic/CAtlArray::INARGTYPE.md)|使用的資料型別以將元素加入至陣列。|  
|[OUTARGTYPE](../Topic/CAtlArray::OUTARGTYPE.md)|使用資料型別來擷取項目的陣列。|  
  
## 備註  
 **CAtlArray** 用於建立和管理陣列方法提供使用者定義型別的項目。  雖然類似於標準 C 陣列， **CAtlArray** 物件可動態壓縮並視需要增加。  陣列索引永遠從位置 0 開始，，和上限 \(Upper Bound\) 可以是內建的或允許展開，在加入新元素。  
  
 對於具有小量項目的陣列，可以使用 ATL 類別 [CSimpleArray](../../atl/reference/csimplearray-class.md) 。  
  
 不支援序列化，**CAtlArray** 非常相關於 MFC 的 **CArray** 類別，而且會在 MFC 專案，雖然。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [MMXSwarm 範例](../../top/visual-cpp-samples.md)   
 [DynamicConsumer 範例](../../top/visual-cpp-samples.md)   
 [UpdatePV 範例](../../top/visual-cpp-samples.md)   
 [Marquee 範例](../../top/visual-cpp-samples.md)   
 [CArray Class](../../mfc/reference/carray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)