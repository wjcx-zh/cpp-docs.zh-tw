---
title: "writeonly_texture_view 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_graphics/Concurrency::graphics::writeonly_texture_view"
dev_langs: 
  - "C++"
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# writeonly_texture_view 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供 writeonly 存取材質。  
  
## 語法  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class writeonly_texture_view;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class writeonly_texture_view<_Value_type, _Rank> : public details::_Texture_base<_Value_type, _Rank>;  
```  
  
#### 參數  
 `_Value_type`  
 材質中項目的類型。  
  
 `_Rank`  
 材質的順位。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`scalar_type`||  
|`value_type`|材質中項目的類型。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[writeonly\_texture\_view::writeonly\_texture\_view 建構函式](../Topic/writeonly_texture_view::writeonly_texture_view%20Constructor.md)|初始化 [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) 類別的新執行個體。|  
|[writeonly\_texture\_view::~writeonly\_texture\_view 解構函式](../Topic/writeonly_texture_view::~writeonly_texture_view%20Destructor.md)|終結 [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[writeonly\_texture\_view::set 方法](../Topic/writeonly_texture_view::set%20Method.md)|設定位於指定索引處的元素值。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[writeonly\_texture\_view::operator\= 運算子](../Topic/writeonly_texture_view::operator=%20Operator.md)|將指定的 [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) 物件複製到這個物件。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[writeonly\_texture\_view::rank 常數](../Topic/writeonly_texture_view::rank%20Constant.md)|取得 [writeonly\_texture\_view](../../../parallel/amp/reference/writeonly-texture-view-class.md) 物件的陣序。|  
  
## 繼承階層架構  
 `_Texture_base`  
  
 `writeonly_texture_view`  
  
## 需求  
 **標頭：**amp\_graphics.h  
  
 **命名空間：**Concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)