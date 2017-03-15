---
title: "float_2 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_2::yx
- amp_short_vectors/Concurrency::graphics::float_2::operator-=
- amp_short_vectors/Concurrency::graphics::float_2::operator++
- amp_short_vectors/Concurrency::graphics::float_2::operator-
- amp_short_vectors/Concurrency::graphics::float_2::r
- amp_short_vectors/Concurrency::graphics::float_2::get_yx
- amp_short_vectors/Concurrency::graphics::float_2::get_xy
- amp_short_vectors/Concurrency::graphics::float_2::operator/=
- amp_short_vectors/Concurrency::graphics::float_2::set_yx
- amp_short_vectors/Concurrency::graphics::float_2::x
- amp_short_vectors/Concurrency::graphics::float_2::get_y
- amp_short_vectors/Concurrency::graphics::float_2::operator+=
- amp_short_vectors/Concurrency::graphics::float_2::gr
- amp_short_vectors/Concurrency::graphics::float_2::operator=
- amp_short_vectors/Concurrency::graphics::float_2::set_x
- amp_short_vectors/Concurrency::graphics::float_2::operator--
- amp_short_vectors/Concurrency::graphics::float_2::get_x
- amp_short_vectors/Concurrency::graphics::float_2::operator*=
- amp_short_vectors/Concurrency::graphics::float_2::rg
- amp_short_vectors/Concurrency::graphics::float_2::set_xy
- amp_short_vectors/Concurrency::graphics::float_2::xy
- amp_short_vectors/Concurrency::graphics::float_2
- amp_short_vectors/Concurrency::graphics::float_2::set_y
- amp_short_vectors/Concurrency::graphics::float_2::y
- amp_short_vectors/Concurrency::graphics::float_2::g
dev_langs:
- C++
ms.assetid: b3ebd48e-f8c8-4f00-a640-357f702f0cae
caps.latest.revision: 11
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
ms.openlocfilehash: 05707bd43a8f9b89a93c0da0011c46d67361fc84
ms.lasthandoff: 02/24/2017

---
# <a name="float2-class"></a>float_2 類別
表示兩個浮點數的短向量。  
  
## <a name="syntax"></a>語法  
  
```  
class float_2;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[float_2 建構函式](#ctor)|多載。 預設建構函式，初始化為 0 的所有項目。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|float_2::get_x 方法||  
|float_2::get_xy 方法||  
|float_2::get_y 方法||  
|float_2::get_yx 方法||  
|float_2::ref_g 方法||  
|float_2::ref_r 方法||  
|float_2::ref_x 方法||  
|float_2::ref_y 方法||  
|float_2::set_x 方法||  
|float_2::set_xy 方法||  
|float_2::set_y 方法||  
|float_2::set_yx 方法||  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|float_2::operator 運算子||  
|float_2::operator-運算子||  
|float_2::operator * = 運算子||  
|float_2::operator / = 運算子||  
|float_2::operator + + 運算子||  
|float_2::operator + = 運算子||  
|float_2::operator = 運算子||  
|float_2::operator-= 運算子||  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[大小常數](#float_2__size)||  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|float_2::g 資料成員||  
|float_2::gr 資料成員||  
|float_2::r 資料成員||  
|float_2::rg 資料成員||  
|float_2::x 資料成員||  
|float_2::xy 資料成員||  
|float_2::y 資料成員||  
|float_2::yx 資料成員||  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `float_2`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp_short_vectors.h  
  
 **命名空間︰** concurrency:: graphics  
  
##  <a name="a-namectora-float2"></a><a name="ctor"></a>float_2 

 預設建構函式，初始化為 0 的所有項目。  
  
```  
float_2() restrict(amp,
    cpu);

 
float_2(
    float _V0,  
    float _V1) restrict(amp,
    cpu);

 
float_2(
    float _V) restrict(amp,
    cpu);

 
float_2(
    const float_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const uint_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const int_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const norm_2& _Other) restrict(amp,
    cpu);

 
explicit inline float_2(
    const double_2& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>參數  
 `_V0`  
 要初始化項目 0 的值。  
  
 `_V1`  
 要初始化項目 1 的值。  
  
 `_V`  
 初始設定的值。  
  
 `_Other`  
 用來初始化物件。  
  
##  <a name="a-namefloat2sizea-size"></a><a name="float_2__size"></a>大小 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency:: graphics 命名空間](concurrency-graphics-namespace.md)

