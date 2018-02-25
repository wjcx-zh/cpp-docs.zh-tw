---
title: "unorm 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
dev_langs:
- C++
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cfd4ed2b4aad398e1206d0e3b786742841aa189b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="unorm-class"></a>unorm 類別
表示 unorm 數字。 每個項目是浮點數 [0.0，1.0 f] 範圍內。  
  
## <a name="syntax"></a>語法  
  
```  
class unorm;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[unorm 建構函式](#ctor)|多載。 預設建構函式。 將初始化為 0.0。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|unorm::operator--||  
|unorm::operator float|轉換運算子。 將 unorm 數字轉換成浮點值。|  
|unorm::operator*=||  
|unorm::operator/=||  
|unorm::operator++||  
|unorm::operator+=||  
|unorm::operator=||  
|unorm::operator-=||  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `unorm`  
  
## <a name="requirements"></a>需求  
 **標頭：** amp_short_vectors.h  
  
 **命名空間：** concurrency:: graphics  
  
##  <a name="ctor"></a> unorm 

 預設建構函式。 將初始化為 0.0。  
  
```  
unorm(
    void) restrict(amp,
    cpu);

 
explicit unorm(
    float _V) restrict(amp,
    cpu);

 
explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit unorm(
    int _V) restrict(amp,
    cpu);

 
explicit unorm(
    double _V) restrict(amp,
    cpu);

 
unorm(
    const unorm& _Other) restrict(amp,
    cpu);

 
inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>參數  
 `_V`  
 用來初始化的值。  
  
 `_Other`  
 用來初始化 norm 物件。  
  
## <a name="see-also"></a>請參閱  
 [Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
