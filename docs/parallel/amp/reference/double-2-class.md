---
title: "double_2 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::double_2::set_x
- amp_short_vectors/Concurrency::graphics::double_2::operator+=
- amp_short_vectors/Concurrency::graphics::double_2::operator=
- amp_short_vectors/Concurrency::graphics::double_2::operator/=
- amp_short_vectors/Concurrency::graphics::double_2::operator*=
- amp_short_vectors/Concurrency::graphics::double_2::yx
- amp_short_vectors/Concurrency::graphics::double_2::y
- amp_short_vectors/Concurrency::graphics::double_2::xy
- amp_short_vectors/Concurrency::graphics::double_2::set_xy
- amp_short_vectors/Concurrency::graphics::double_2::get_yx
- amp_short_vectors/Concurrency::graphics::double_2::set_yx
- amp_short_vectors/Concurrency::graphics::double_2::get_xy
- amp_short_vectors/Concurrency::graphics::double_2::operator++
- amp_short_vectors/Concurrency::graphics::double_2::get_x
- amp_short_vectors/Concurrency::graphics::double_2::operator-=
- amp_short_vectors/Concurrency::graphics::double_2::rg
- amp_short_vectors/Concurrency::graphics::double_2::gr
- amp_short_vectors/Concurrency::graphics::double_2::get_y
- amp_short_vectors/Concurrency::graphics::double_2::x
- amp_short_vectors/Concurrency::graphics::double_2::r
- amp_short_vectors/Concurrency::graphics::double_2::operator--
- amp_short_vectors/Concurrency::graphics::double_2
- amp_short_vectors/Concurrency::graphics::double_2::operator-
- amp_short_vectors/Concurrency::graphics::double_2::g
- amp_short_vectors/Concurrency::graphics::double_2::set_y
dev_langs:
- C++
ms.assetid: c19c2d21-3cbf-4ce5-b460-3b8253688f82
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
ms.openlocfilehash: 003cf8a4e1803154b4224c30524f8a302f10ea8f
ms.lasthandoff: 02/24/2017

---
# <a name="double2-class"></a>double_2 類別
代表 2 雙短向量。  
  
## <a name="syntax"></a>語法  
  
```  
class double_2;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[double_2 建構函式](#ctor)|多載。 預設建構函式，初始化為 0 的所有項目。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|double_2::get_x 方法||  
|double_2::get_xy 方法||  
|double_2::get_y 方法||  
|double_2::get_yx 方法||  
|double_2::ref_g 方法||  
|double_2::ref_r 方法||  
|double_2::ref_x 方法||  
|double_2::ref_y 方法||  
|double_2::set_x 方法||  
|double_2::set_xy 方法||  
|double_2::set_y 方法||  
|double_2::set_yx 方法||  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|double_2::operator 運算子||  
|double_2::operator-運算子||  
|double_2::operator * = 運算子||  
|double_2::operator / = 運算子||  
|double_2::operator + + 運算子||  
|double_2::operator + = 運算子||  
|double_2::operator = 運算子||  
|double_2::operator-= 運算子||  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|double_2::size 常數||  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|double_2::g 資料成員||  
|double_2::gr 資料成員||  
|double_2::r 資料成員||  
|double_2::rg 資料成員||  
|double_2::x 資料成員||  
|double_2::xy 資料成員||  
|double_2::y 資料成員||  
|double_2::yx 資料成員||  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `double_2`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp_short_vectors.h  
  
 **命名空間︰** concurrency:: graphics  
  
##  <a name="a-namectora-double2"></a><a name="ctor"></a>double_2 

 預設建構函式，初始化為 0 的所有項目。  
  
```  
double_2() restrict(amp,
    cpu);

 
double_2(
    double _V0,  
    double _V1) restrict(amp,
    cpu);

 
double_2(
    double _V) restrict(amp,
    cpu);

 
double_2(
    const double_2& _Other) restrict(amp,
    cpu);

 
explicit inline double_2(
    const uint_2& _Other) restrict(amp,
    cpu);

 
explicit inline double_2(
    const int_2& _Other) restrict(amp,
    cpu);

 
explicit inline double_2(
    const float_2& _Other) restrict(amp,
    cpu);

 
explicit inline double_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

 
explicit inline double_2(
    const norm_2& _Other) restrict(amp,
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
  
##  <a name="a-namedouble2sizea-size"></a><a name="double_2__size"></a>大小 

```  
static const int size = 2;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency:: graphics 命名空間](concurrency-graphics-namespace.md)

