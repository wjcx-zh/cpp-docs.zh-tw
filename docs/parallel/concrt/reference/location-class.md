---
title: "location 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::location
dev_langs:
- C++
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
caps.latest.revision: 10
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
ms.openlocfilehash: 1a404f44600addcbf332fabcfc19a7b48dab0c81
ms.lasthandoff: 02/24/2017

---
# <a name="location-class"></a>location 類別
硬體實體位置的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```
class location;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[位置建構函式](#ctor)|多載。 建構 `location` 物件。|  
|[~ location 解構函式](#dtor)|終結 `location` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[目前的方法](#current)|傳回 `location` 物件，表示呼叫執行緒執行的最特定位置。|  
|[from_numa_node 方法](#from_numa_node)|傳回 `location` 物件，該物件代表某一特定的 NUMA 節點。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[運算子 ！ = 運算子](#operator_neq)|判斷兩個 `location` 物件是否表示不同的位置。|  
|[運算子 = 運算子](#operator_eq)|將不同 `location` 物件的內容指派給這一個。|  
|[運算子 = = 運算子](#operator_eq_eq)|判斷兩個`location`物件代表相同的位置。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `location`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namedtora-location"></a><a name="dtor"></a>~ 位置 

 終結 `location` 物件。  
  
```
~location();
```  
  
##  <a name="a-namecurrenta-current"></a><a name="current"></a>目前 

 傳回 `location` 物件，表示呼叫執行緒執行的最特定位置。  
  
```
static location __cdecl current();
```  
  
### <a name="return-value"></a>傳回值  
 表示呼叫執行緒執行的最特定位置。  
  
##  <a name="a-namefromnumanodea-fromnumanode"></a><a name="from_numa_node"></a>from_numa_node 

 傳回 `location` 物件，該物件代表某一特定的 NUMA 節點。  
  
```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```  
  
### <a name="parameters"></a>參數  
 `_NumaNodeNumber`  
 要建構其位置的 NUMA 節點編號。  
  
### <a name="return-value"></a>傳回值  
 代表 NUMA 節點的位置，由 `_NumaNodeNumber` 參數所指定。  
  
##  <a name="a-namectora-location"></a><a name="ctor"></a>位置 

 建構 `location` 物件。  
  
```
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```  
  
### <a name="parameters"></a>參數  
 `_Src`  
 `_LocationType`  
 `_Id`  
 `_BindingId`  
 `_PBinding`  
  
### <a name="remarks"></a>備註  
 預設建構的位置表示整個系統。  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>運算子 ！ = 

 判斷兩個 `location` 物件是否表示不同的位置。  
  
```
bool operator!= (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
  
### <a name="return-value"></a>傳回值  
 如果這兩個位置不同則為 `true`，否則為 `false`。  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>運算子 = 

 將不同 `location` 物件的內容指派給這一個。  
  
```
location& operator= (const location& _Rhs);
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 來源 `location` 物件。  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>運算子 = = 

 判斷兩個`location`物件代表相同的位置。  
  
```
bool operator== (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
  
### <a name="return-value"></a>傳回值  
 `true`如果兩個位置都相同，和`false`否則。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

