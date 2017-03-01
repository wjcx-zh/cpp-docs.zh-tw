---
title: "int_3 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_3::get_x
- amp_short_vectors/Concurrency::graphics::int_3::operator-=
- amp_short_vectors/Concurrency::graphics::int_3::get_y
- amp_short_vectors/Concurrency::graphics::int_3::operator=
- amp_short_vectors/Concurrency::graphics::int_3::operator++
- amp_short_vectors/Concurrency::graphics::int_3::zyx
- amp_short_vectors/Concurrency::graphics::int_3::get_z
- amp_short_vectors/Concurrency::graphics::int_3::operator*=
- amp_short_vectors/Concurrency::graphics::int_3::grb
- amp_short_vectors/Concurrency::graphics::int_3::get_xz
- amp_short_vectors/Concurrency::graphics::int_3::br
- amp_short_vectors/Concurrency::graphics::int_3::operator--
- amp_short_vectors/Concurrency::graphics::int_3
- amp_short_vectors/Concurrency::graphics::int_3::set_yx
- amp_short_vectors/Concurrency::graphics::int_3::x
- amp_short_vectors/Concurrency::graphics::int_3::yxz
- amp_short_vectors/Concurrency::graphics::int_3::set_y
- amp_short_vectors/Concurrency::graphics::int_3::zy
- amp_short_vectors/Concurrency::graphics::int_3::z
- amp_short_vectors/Concurrency::graphics::int_3::get_zx
- amp_short_vectors/Concurrency::graphics::int_3::rb
- amp_short_vectors/Concurrency::graphics::int_3::yzx
- amp_short_vectors/Concurrency::graphics::int_3::gb
- amp_short_vectors/Concurrency::graphics::int_3::set_zxy
- amp_short_vectors/Concurrency::graphics::int_3::xy
- amp_short_vectors/Concurrency::graphics::int_3::set_zx
- amp_short_vectors/Concurrency::graphics::int_3::g
- amp_short_vectors/Concurrency::graphics::int_3::operator/=
- amp_short_vectors/Concurrency::graphics::int_3::get_zy
- amp_short_vectors/Concurrency::graphics::int_3::yx
- amp_short_vectors/Concurrency::graphics::int_3::xzy
- amp_short_vectors/Concurrency::graphics::int_3::set_x
- amp_short_vectors/Concurrency::graphics::int_3::set_xz
- amp_short_vectors/Concurrency::graphics::int_3::get_yzx
- amp_short_vectors/Concurrency::graphics::int_3::b
- amp_short_vectors/Concurrency::graphics::int_3::gbr
- amp_short_vectors/Concurrency::graphics::int_3::operator+=
- amp_short_vectors/Concurrency::graphics::int_3::gr
- amp_short_vectors/Concurrency::graphics::int_3::brg
- amp_short_vectors/Concurrency::graphics::int_3::bg
- amp_short_vectors/Concurrency::graphics::int_3::zx
- amp_short_vectors/Concurrency::graphics::int_3::get_xyz
- amp_short_vectors/Concurrency::graphics::int_3::set_zyx
- amp_short_vectors/Concurrency::graphics::int_3::set_yzx
- amp_short_vectors/Concurrency::graphics::int_3::y
- amp_short_vectors/Concurrency::graphics::int_3::set_z
- amp_short_vectors/Concurrency::graphics::int_3::r
- amp_short_vectors/Concurrency::graphics::int_3::set_xzy
- amp_short_vectors/Concurrency::graphics::int_3::rg
- amp_short_vectors/Concurrency::graphics::int_3::xyz
- amp_short_vectors/Concurrency::graphics::int_3::get_yz
- amp_short_vectors/Concurrency::graphics::int_3::operator-
- amp_short_vectors/Concurrency::graphics::int_3::set_xy
- amp_short_vectors/Concurrency::graphics::int_3::zxy
- amp_short_vectors/Concurrency::graphics::int_3::yz
- amp_short_vectors/Concurrency::graphics::int_3::set_zy
- amp_short_vectors/Concurrency::graphics::int_3::bgr
- amp_short_vectors/Concurrency::graphics::int_3::get_xzy
- amp_short_vectors/Concurrency::graphics::int_3::get_yx
- amp_short_vectors/Concurrency::graphics::int_3::rbg
- amp_short_vectors/Concurrency::graphics::int_3::get_zxy
- amp_short_vectors/Concurrency::graphics::int_3::set_yxz
- amp_short_vectors/Concurrency::graphics::int_3::rgb
- amp_short_vectors/Concurrency::graphics::int_3::get_xy
- amp_short_vectors/Concurrency::graphics::int_3::set_xyz
- amp_short_vectors/Concurrency::graphics::int_3::get_yxz
- amp_short_vectors/Concurrency::graphics::int_3::get_zyx
- amp_short_vectors/Concurrency::graphics::int_3::xz
- amp_short_vectors/Concurrency::graphics::int_3::set_yz
dev_langs:
- C++
ms.assetid: d4af182f-30f1-455c-b16d-aa99cd314038
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
ms.openlocfilehash: 038b3cafdbdc628fdff0bcf70db6575acabb17e1
ms.lasthandoff: 02/24/2017

---
# <a name="int3-class"></a>int_3 類別
代表三個整數的短向量。  
  
## <a name="syntax"></a>語法  
  
```  
class int_3;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[int_3 建構函式](#ctor)|多載。 預設建構函式，初始化為 0 的所有項目。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|int_3::get_x 方法||  
|int_3::get_xy 方法||  
|int_3::get_xyz 方法||  
|int_3::get_xz 方法||  
|int_3::get_xzy 方法||  
|int_3::get_y 方法||  
|int_3::get_yx 方法||  
|int_3::get_yxz 方法||  
|int_3::get_yz 方法||  
|int_3::get_yzx 方法||  
|int_3::get_z 方法||  
|int_3::get_zx 方法||  
|int_3::get_zxy 方法||  
|int_3::get_zy 方法||  
|int_3::get_zyx 方法||  
|int_3::ref_b 方法||  
|int_3::ref_g 方法||  
|int_3::ref_r 方法||  
|int_3::ref_x 方法||  
|int_3::ref_y 方法||  
|int_3::ref_z 方法||  
|int_3::set_x 方法||  
|int_3::set_xy 方法||  
|int_3::set_xyz 方法||  
|int_3::set_xz 方法||  
|int_3::set_xzy 方法||  
|int_3::set_y 方法||  
|int_3::set_yx 方法||  
|int_3::set_yxz 方法||  
|int_3::set_yz 方法||  
|int_3::set_yzx 方法||  
|int_3::set_z 方法||  
|int_3::set_zx 方法||  
|int_3::set_zxy 方法||  
|int_3::set_zy 方法||  
|int_3::set_zyx 方法||  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|int_3::operator 運算子||  
|int_3::operator-運算子||  
|int_3::operator %= 運算子||  
|int_3::operator i = 運算子||  
|int_3::operator * = 運算子||  
|int_3::operator / = 運算子||  
|int_3::operator ^ = 運算子||  
|int_3::operator | = 運算子||  
|int_3::operator ~ 運算子||  
|int_3::operator + + 運算子||  
|int_3::operator + = 運算子||  
|int_3::operator\<= 運算子||  
|int_3::operator = 運算子||  
|int_3::operator-= 運算子||  
|int_3::operator >> = 運算子||  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[大小常數](#size)||  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|int_3::b 資料成員||  
|int_3::bg 資料成員||  
|int_3::bgr 資料成員||  
|int_3::br 資料成員||  
|int_3::brg 資料成員||  
|int_3::g 資料成員||  
|int_3::gb 資料成員||  
|int_3::gbr 資料成員||  
|int_3::gr 資料成員||  
|int_3::grb 資料成員||  
|int_3::r 資料成員||  
|int_3::rb 資料成員||  
|int_3::rbg 資料成員||  
|int_3::rg 資料成員||  
|int_3::rgb 資料成員||  
|int_3::x 資料成員||  
|int_3::xy 資料成員||  
|int_3::xyz 資料成員||  
|int_3::xz 資料成員||  
|int_3::xzy 資料成員||  
|int_3::y 資料成員||  
|int_3::yx 資料成員||  
|int_3::yxz 資料成員||  
|int_3::yz 資料成員||  
|int_3::yzx 資料成員||  
|int_3::z 資料成員||  
|int_3::zx 資料成員||  
|int_3::zxy 資料成員||  
|int_3::zy 資料成員||  
|int_3::zyx 資料成員||  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `int_3`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp_short_vectors.h  
  
 **命名空間︰** concurrency:: graphics  

## <a name="a-namectora-int3"></a><a name="ctor"></a>int_3 

預設建構函式，初始化為 0 的所有項目。  
  
## <a name="syntax"></a>語法  
  
```  
int_3() restrict(amp,cpu);  
int_3(  
   int _V0,  
   int _V1,  
   int _V2  
) restrict(amp,cpu);  
int_3(  
   int _V  
) restrict(amp,cpu);  
int_3(  
   const int_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const uint_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const float_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const unorm_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const norm_3& _Other  
) restrict(amp,cpu);  
explicit inline int_3(  
   const double_3& _Other  
) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_V0`  
 要初始化項目 0 的值。  
  
 `_V1`  
 要初始化項目 1 的值。  
  
 `_V2`  
 要初始化項目 2 的值。  
  
 `_V`  
 初始設定的值。  
  
 `_Other`  
 用來初始化物件。  
  
## <a name="a-namesizea-size"></a><a name="size"></a>大小 

## <a name="syntax"></a>語法  
  
```  
static const int size = 3;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency:: graphics 命名空間](concurrency-graphics-namespace.md)

