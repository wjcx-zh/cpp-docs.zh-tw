---
title: scoped_d3d_access_lock 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
dev_langs:
- C++
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0053fa89139ac806a3d8ae0572cd053dd6bec72c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688137"
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock 類別
Accelerator_view 物件上的 D3D 存取鎖定 RAII 包裝函式。  
  
### <a name="syntax"></a>語法  
  
```  
class scoped_d3d_access_lock;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[scoped_d3d_access_lock 建構函式](#ctor)|多載。 建構 `scoped_d3d_access_lock` 物件。 當此物件超出範圍時，會釋放鎖定。|  
|[~ scoped_d3d_access_lock 解構函式](#dtor)|釋出相關聯的 D3D 存取鎖定`accelerator_view`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|取得擁有權的鎖定，從另一個`scoped_d3d_access_lock`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `scoped_d3d_access_lock`  
  
## <a name="requirements"></a>需求  
 **標頭：** amprt.h  
  
 **命名空間：** concurrency:: direct3d  

##  <a name="ctor"></a> scoped_d3d_access_lock 

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
 `scoped_d3d_access_lock`用來移動現有的鎖定物件。  
  
## <a name="construction"></a>建構  
 [1] 建構函式  
 取得的 D3D 存取鎖定上指定[accelerator_view](accelerator-view-class.md)物件。 建構會封鎖已取得鎖定為止。  
  
 [2] 建構函式  
 採用的 D3D 存取鎖定給定[accelerator_view](accelerator-view-class.md)物件。  
  
 [3] 移動建構函式  
 會從另一個現有的 D3D 存取鎖定`scoped_d3d_access_lock`物件。 建構不會封鎖。  

  
##  <a name="dtor"></a> ~scoped_d3d_access_lock 

 釋出相關聯的 D3D 存取鎖定`accelerator_view`物件。  
  
```  
~scoped_d3d_access_lock();
```  
## <a name="operator_eq"></a> 運算子 = 

取得擁有權從另一個的 D3D 存取鎖定`scoped_d3d_access_lock`釋放先前鎖定的物件。  
 
```  
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 要從中移動 D3D 存取鎖定 accelerator_view。  
  
### <a name="return-value"></a>傳回值  
 此參考`scoped_accelerator_view_lock`。  

## <a name="see-also"></a>另請參閱  
 [Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)
