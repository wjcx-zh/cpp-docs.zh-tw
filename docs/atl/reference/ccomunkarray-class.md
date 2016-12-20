---
title: "CComUnkArray Class | Microsoft Docs"
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
  - "ATL.CComUnkArray"
  - "ATL.CComUnkArray<nMaxSize>"
  - "ATL::CComUnkArray<nMaxSize>"
  - "ATL::CComUnkArray"
  - "CComUnkArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComUnkArray class"
  - "連接點 [C++], 管理"
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComUnkArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會將 **IUnknown** 指標和是設計用來做為參數 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 樣板類別。  
  
## 語法  
  
```  
template<  
   unsigned int nMaxSize  
>  
class CComUnkArray  
```  
  
#### 參數  
 *nMaxSize*  
 的 **IUnknown** 指標最大數目。在此靜態陣列可以存放。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComUnkArray::CComUnkArray](../Topic/CComUnkArray::CComUnkArray.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComUnkArray::Add](../Topic/CComUnkArray::Add.md)|呼叫這個方法會將 **IUnknown** 指標陣列。|  
|[CComUnkArray::begin](../Topic/CComUnkArray::begin.md)|傳回指向儲存在集合中的第一個 **IUnknown** 指標。|  
|[CComUnkArray::end](../Topic/CComUnkArray::end.md)|會將指標傳至一個傳遞集合中的最後一個 **IUnknown** 指標。|  
|[CComUnkArray::GetCookie](../Topic/CComUnkArray::GetCookie.md)|呼叫這個方法會取得 Cookie 與特定 **IUnknown** 指標。|  
|[CComUnkArray::GetUnknown](../Topic/CComUnkArray::GetUnknown.md)|呼叫這個方法會取得 **IUnknown** 指標與特定 Cookie。|  
|[CComUnkArray::Remove](../Topic/CComUnkArray::Remove.md)|呼叫這個方法會從陣列移除 **IUnknown** 指標。|  
  
## 備註  
 **CComUnkArray** 保留 **IUnknown** 指標固定數量，在每個連接點的介面。  **CComUnkArray** 可以用來做為 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 樣板類別的參數。  **CComUnkArray\<1\>** 是一個連接點 **CComUnkArray** 最佳化的樣板特製化。  
  
 **CComUnkArray** 方法 [啟動](../Topic/CComUnkArray::begin.md) 和 [結束](../Topic/CComUnkArray::end.md) 可用來逐一查看所有連接點迴圈 \(例如，在中，當事件引發時\)。  
  
 請參閱 [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md) 有關在 Automation 連接點 Proxy 的詳細資料。  
  
> [!NOTE]
>  類別 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)**加入類別** 精靈使用**Note** ，當建立具有連接點的控制項時。  如果您想要手動指定連接點的數目，從 **CComDynamicUnkArray** 將參考加入至 `CComUnkArray_<``_>`*n* ，其中 *n* 是連接的點數需求。  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComDynamicUnkArray Class](../../atl/reference/ccomdynamicunkarray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)