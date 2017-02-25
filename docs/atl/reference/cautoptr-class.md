---
title: "CAutoPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAutoPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoPtr class"
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CAutoPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示智慧型指標物件。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<   
typename T  
>  
class CAutoPtr  
```  
  
#### 參數  
 `T`  
 指標型別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAutoPtr::CAutoPtr](../Topic/CAutoPtr::CAutoPtr.md)|建構函式。|  
|[CAutoPtr::~CAutoPtr](../Topic/CAutoPtr::~CAutoPtr.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAutoPtr::Attach](../Topic/CAutoPtr::Attach.md)|呼叫這個方法會接受一個現有指標的擁有權。|  
|[CAutoPtr::Detach](../Topic/CAutoPtr::Detach.md)|呼叫這個方法會釋放指標的擁有權。|  
|[CAutoPtr::Free](../Topic/CAutoPtr::Free.md)|呼叫這個方法會刪除上的物件。 `CAutoPtr`。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAutoPtr::operator T\*](../Topic/CAutoPtr::operator%20T*.md)|轉型運算子。|  
|[CAutoPtr::operator \=](../Topic/CAutoPtr::operator%20=.md)|指派運算子。|  
|[CAutoPtr::operator \-\>](../Topic/CAutoPtr::operator%20-%3E.md)|成員指標運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAutoPtr::m\_p](../Topic/CAutoPtr::m_p.md)|指標資料成員變數。|  
  
## 備註  
 這個類別會建立和管理的智慧型指標提供方法，可協助防止記憶體遺漏 \(Memory Leak\) 會自動釋放資源，並在超出範圍時。  
  
 此外， `CAutoPtr` 的複製建構函式和指派運算子傳輸，複製來源指標的指標和設定來源指標的指標的擁有權 null。  有兩 `CAutoPtr` 物件儲存相同指標的每個也是不可能的，因此，這會減少兩次刪除相同指標的可能性。  
  
 `CAutoPtr` 也簡化了指標集合的建立。  取代衍生集合類別和覆寫解構函式，是較簡單的執行 `CAutoPtr` 集合物件。  當集合中刪除， `CAutoPtr` 物件會超出範圍並自動刪除。  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) 和 Variant 與 `CAutoPtr`類似的方式運作，不過，這些配置和釋放記憶體使用不同的堆積函式而不是 C\+\+ **new** 和 **刪除** 運算子。  [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) 類似 `CAutoPtr`，是唯一差別在於它會使用 **vector new\[\]** 和 **vector delete\[\]** 配置和釋放記憶體。  
  
 如果需要，請參閱 [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) 和 [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) 智慧型指標陣列或清單。  
  
## 需求  
 **Header:** atlbase.h  
  
## 範例  
 [!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/CPP/cautoptr-class_1.cpp)]  
  
## 請參閱  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CAutoVectorPtr Class](../../atl/reference/cautovectorptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)