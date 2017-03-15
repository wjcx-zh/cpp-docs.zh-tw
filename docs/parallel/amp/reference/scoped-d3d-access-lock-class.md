---
title: "scoped_d3d_access_lock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
caps.latest.revision: 8
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
ms.openlocfilehash: c5bc6183b3abc7a5598159717b0dbfa1dae2a05d
ms.lasthandoff: 02/24/2017

---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock 類別
RAII 包裝函式的 D3D 存取鎖定 accelerator_view 物件。  
  
### <a name="syntax"></a>語法  
  
```  
class scoped_d3d_access_lock;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[scoped_d3d_access_lock 建構函式](#ctor)|多載。 建構 `scoped_d3d_access_lock` 物件。 當此物件超出範圍時，會釋放鎖定。|  
|[~ scoped_d3d_access_lock 解構函式](#dtor)|釋放相關聯的 D3D 存取鎖定`accelerator_view`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[運算子 = 運算子](#operator_eq)|取得從另一個鎖定的擁有權`scoped_d3d_access_lock`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `scoped_d3d_access_lock`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amprt.h  
  
 **命名空間︰** concurrency:: direct3d  

##  <a name="a-namectora-scopedd3daccesslock"></a><a name="ctor"></a>scoped_d3d_access_lock 

 建構 `scoped_d3d_access_lock` 物件。 當此物件超出範圍時，會釋放鎖定。  
 
```  
explicit scoped_d3d_access_lock(// [1] constructor  
    accelerator_view& _Av);

 
explicit scoped_d3d_access_lock(// [2] constructor  
    accelerator_view& _Av,  
    adopt_d3d_access_lock_t _T);

 
scoped_d3d_access_lock(// [3] move constructor  
    scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Av`  
 `accelerator_view`採用鎖定。  
  
 `_T`  
 `adopt_d3d_access_lock_t` 物件。  
  
 `_Other`  
 `scoped_d3d_access_lock`要移動的現有鎖定的來源物件。  
  
## <a name="construction"></a>建構  
 [1] 建構函式  
 取得 D3D 存取鎖定在指定[accelerator_view](accelerator-view-class.md)物件。 建構封鎖，直到取得鎖定。  
  
 [2] 建構函式  
 採用 D3D 存取鎖定，從給定[accelerator_view](accelerator-view-class.md)物件。  
  
 [3] 移動建構函式  
 會從另一個現有的 D3D 存取鎖定`scoped_d3d_access_lock`物件。 建構不會封鎖。  

  
##  <a name="a-namedtora-scopedd3daccesslock"></a><a name="dtor"></a>~ scoped_d3d_access_lock 

 釋放相關聯的 D3D 存取鎖定`accelerator_view`物件。  
  
```  
~scoped_d3d_access_lock();
```  
## <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>運算子 = 

取得從另一個 D3D 存取鎖定的擁有權`scoped_d3d_access_lock`釋放先前鎖定的物件。  
 
```  
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 要從中移動 D3D 存取鎖定 accelerator_view。  
  
### <a name="return-value"></a>傳回值  
 參考`scoped_accelerator_view_lock`。  

## <a name="see-also"></a>另請參閱  
 [Concurrency:: direct3d 命名空間](concurrency-direct3d-namespace.md)

