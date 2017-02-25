---
title: "CHeapPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CHeapPtr"
  - "CHeapPtr"
  - "ATL.CHeapPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtr class"
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHeapPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理的堆積指標的智慧型指標類別。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
typename T,  
class Allocator= CCRTAllocator  
> class CHeapPtr :  
public CHeapPtrBase< T, Allocator>  
```  
  
#### 參數  
 `T`  
 儲存在堆積上的物件型別。  
  
 `Allocator`  
 要使用的記憶體配置類別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtr::CHeapPtr](../Topic/CHeapPtr::CHeapPtr.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtr::Allocate](../Topic/CHeapPtr::Allocate.md)|呼叫這個方法會配置在堆積上的記憶體中儲存物件。|  
|[CHeapPtr::Reallocate](../Topic/CHeapPtr::Reallocate.md)|呼叫這個方法會重新配置在堆積上的記憶體。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtr::operator \=](../Topic/CHeapPtr::operator%20=.md)|指派運算子。|  
  
## 備註  
 根據預設`CHeapPtr`[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) 從衍生並使用 CRT 常式 \(在 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)\) 配置和釋放記憶體。  類別 [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) 可能用來建構清單堆積指標。  請參閱 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，使用 COM 記憶體配置常式。  
  
## 繼承階層架構  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 `CHeapPtr`  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [CHeapPtrBase Class](../../atl/reference/cheapptrbase-class.md)   
 [CCRTAllocator Class](../../atl/reference/ccrtallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)