---
title: network_link_registry 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dab0ad6aff391eb89ac59198fb8c173ecb362bbd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="networklinkregistry-class"></a>network_link_registry 類別
`network_link_registry` 抽象基底類別會管理來源和目標區塊之間的連結。  
  
## <a name="syntax"></a>語法  
  
```
template<class _Block>
class network_link_registry;
```  
  
#### <a name="parameters"></a>參數  
 `_Block`  
 封鎖資料類型儲存在`network_link_registry`。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`const_pointer`|類型，提供的指標`const`中的項目`network_link_registry`物件。|  
|`const_reference`|提供的參考型別`const`項目儲存在`network_link_registry`物件進行讀取和執行 const 作業。|  
|`iterator`|類型，提供迭代器可以讀取或修改任何項目中的`network_link_registry`物件。|  
|`type`|表示儲存在中的區塊類型的型別`network_link_registry`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[add](#add)|當在衍生類別中覆寫時，將加入的連結`network_link_registry`物件。|  
|[begin](#begin)|當在衍生類別中覆寫時，會傳回迭代器中的第一個項目`network_link_registry`物件。|  
|[包含](#contains)|當在衍生類別中覆寫時，會搜尋`network_link_registry`物件指定的區塊。|  
|[count](#count)|當在衍生類別中覆寫時，會傳回中的項目數`network_link_registry`物件。|  
|[remove](#remove)|當在衍生類別中覆寫時，會移除從指定的區塊`network_link_registry`物件。|  
  
## <a name="remarks"></a>備註  
 `network link registry`而言是不安全的並行存取。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `network_link_registry`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="add"></a> 新增 

 當在衍生類別中覆寫時，將加入的連結`network_link_registry`物件。  
  
```
virtual void add(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 要加入區塊的指標。  
  
##  <a name="begin"></a> 開始 

 當在衍生類別中覆寫時，會傳回迭代器中的第一個項目`network_link_registry`物件。  
  
```
virtual iterator begin() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器中的第一個項目定址`network_link_registry`物件。  
  
### <a name="remarks"></a>備註  
 迭代器的結束狀態以`NULL`連結。  
  
##  <a name="contains"></a> 包含 

 當在衍生類別中覆寫時，會搜尋`network_link_registry`物件指定的區塊。  
  
```
virtual bool contains(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 要搜尋在區塊的指標`network_link_registry`物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果找不到此區塊，`false`否則。  
  
##  <a name="count"></a> 計數 

 當在衍生類別中覆寫時，會傳回中的項目數`network_link_registry`物件。  
  
```
virtual size_t count() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 中的項目數`network_link_registry`物件。  
  
##  <a name="remove"></a> 移除 

 當在衍生類別中覆寫時，會移除從指定的區塊`network_link_registry`物件。  
  
```
virtual bool remove(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 要移除，如果在區塊的指標找到。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果找到並移除，連結`false`否則。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [single_link_registry 類別](single-link-registry-class.md)   
 [multi_link_registry 類別](multi-link-registry-class.md)
