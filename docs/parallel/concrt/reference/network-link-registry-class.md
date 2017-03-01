---
title: "network_link_registry 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::network_link_registry
dev_langs:
- C++
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 8b39ab676db0072d279ee4058693769ef6f7eb3f
ms.lasthandoff: 02/24/2017

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
 區塊資料型別儲存在`network_link_registry`。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|`const_pointer`|類型，提供一個指向`const`中的項目`network_link_registry`物件。|  
|`const_reference`|提供的參考型別`const`項目儲存在`network_link_registry`物件進行讀取和執行 const 的作業。|  
|`iterator`|類型，提供迭代器可以讀取或修改任何項目中的`network_link_registry`物件。|  
|`type`|表示儲存在中的區塊類型的型別`network_link_registry`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[新增方法](#add)|在衍生類別中覆寫，將連結`network_link_registry`物件。|  
|[begin 方法](#begin)|當在衍生類別中覆寫時，會傳回迭代器中的第一個項目`network_link_registry`物件。|  
|[包含方法](#contains)|當在衍生類別中覆寫時，會搜尋`network_link_registry`物件指定的區塊。|  
|[count 方法](#count)|當在衍生類別中覆寫時，會傳回項目的數目`network_link_registry`物件。|  
|[remove 方法](#remove)|當在衍生類別中覆寫時，會移除從指定的區塊`network_link_registry`物件。|  
  
## <a name="remarks"></a>備註  
 `network link registry`並不安全的並行存取。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `network_link_registry`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-nameadda-add"></a><a name="add"></a>新增 

 在衍生類別中覆寫，將連結`network_link_registry`物件。  
  
```
virtual void add(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 要加入的區塊的指標。  
  
##  <a name="a-namebegina-begin"></a><a name="begin"></a>開始 

 當在衍生類別中覆寫時，會傳回迭代器中的第一個項目`network_link_registry`物件。  
  
```
virtual iterator begin() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器中的第一個項目定址`network_link_registry`物件。  
  
### <a name="remarks"></a>備註  
 迭代器的結束狀態以`NULL`連結。  
  
##  <a name="a-namecontainsa-contains"></a><a name="contains"></a>包含 

 當在衍生類別中覆寫時，會搜尋`network_link_registry`物件指定的區塊。  
  
```
virtual bool contains(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 在搜尋區塊的指標`network_link_registry`物件。  
  
### <a name="return-value"></a>傳回值  
 `true`如果找不到此區塊，`false`否則。  
  
##  <a name="a-namecounta-count"></a><a name="count"></a>計數 

 當在衍生類別中覆寫時，會傳回項目的數目`network_link_registry`物件。  
  
```
virtual size_t count() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 中的項目數`network_link_registry`物件。  
  
##  <a name="a-nameremovea-remove"></a><a name="remove"></a>移除 

 當在衍生類別中覆寫時，會移除從指定的區塊`network_link_registry`物件。  
  
```
virtual bool remove(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 要移除，如果在區塊的指標找到。  
  
### <a name="return-value"></a>傳回值  
 `true`如果找到並移除連結`false`否則。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [single_link_registry 類別](single-link-registry-class.md)   
 [multi_link_registry 類別](multi-link-registry-class.md)

