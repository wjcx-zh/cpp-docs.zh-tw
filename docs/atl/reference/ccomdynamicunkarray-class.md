---
title: "CComDynamicUnkArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComDynamicUnkArray"
  - "CComDynamicUnkArray"
  - "ATL::CComDynamicUnkArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComDynamicUnkArray class"
  - "連接點 [C++], 管理"
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CComDynamicUnkArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會將陣列 **IUnknown** 指標。  
  
## 語法  
  
```  
class CComDynamicUnkArray  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](../Topic/CComDynamicUnkArray::CComDynamicUnkArray.md)|建構函式。  初始化值設定為 **NULL** 和集合大小為零。|  
|[CComDynamicUnkArray::~CComDynamicUnkArray](../Topic/CComDynamicUnkArray::~CComDynamicUnkArray.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComDynamicUnkArray::Add](../Topic/CComDynamicUnkArray::Add.md)|呼叫這個方法會將 `IUnknown` 指標陣列。|  
|[CComDynamicUnkArray::begin](../Topic/CComDynamicUnkArray::begin.md)|傳回指向儲存在集合中的第一個 `IUnknown` 指標。|  
|[CComDynamicUnkArray::clear](../Topic/CComDynamicUnkArray::clear.md)|空白陣列。|  
|[CComDynamicUnkArray::end](../Topic/CComDynamicUnkArray::end.md)|會將指標傳至一個傳遞集合中的最後一個 **IUnknown** 指標。|  
|[CComDynamicUnkArray::GetAt](../Topic/CComDynamicUnkArray::GetAt.md)|擷取指定索引處的項目。|  
|[CComDynamicUnkArray::GetCookie](../Topic/CComDynamicUnkArray::GetCookie.md)|呼叫這個方法會取得 Cookie 與特定 **IUnknown** 指標。|  
|[CComDynamicUnkArray::GetSize](../Topic/CComDynamicUnkArray::GetSize.md)|傳回陣列的長度。|  
|[CComDynamicUnkArray::GetUnknown](../Topic/CComDynamicUnkArray::GetUnknown.md)|呼叫這個方法會取得 **IUnknown** 指標與特定 Cookie。|  
|[CComDynamicUnkArray::Remove](../Topic/CComDynamicUnkArray::Remove.md)|呼叫這個方法會從陣列移除 **IUnknown** 指標。|  
  
## 備註  
 **CComDynamicUnkArray** 保存動態配置的 **IUnknown** 陣列指標，每個連接點的介面。  **CComDynamicUnkArray** 可以用來做為 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 樣板類別的參數。  
  
 **CComDynamicUnkArray** 方法 [啟動](../Topic/CComDynamicUnkArray::begin.md) 和 [結束](../Topic/CComDynamicUnkArray::end.md) 可用來逐一查看所有連接點迴圈 \(例如，在中，當事件引發時\)。  
  
 請參閱 [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md) 有關在 Automation 連接點 Proxy 的詳細資料。  
  
> [!NOTE]
>  類別 **CComDynamicUnkArray加入類別** 精靈使用**Note** ，當建立具有連接點的控制項時。  如果您想要手動指定連接點的數目，從 **CComDynamicUnkArray** 將參考加入至 `CComUnkArray_<``_>`*n* ，其中 *n* 是連接的點數需求。  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComUnkArray Class](../../atl/reference/ccomunkarray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)