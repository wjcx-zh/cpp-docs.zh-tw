---
title: "writeonly_texture_view 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
dev_langs:
- C++
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
caps.latest.revision: 9
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 5a051b8db98e36ced89783bfa1de2ab5f514c6bc
ms.lasthandoff: 03/17/2017

---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view 類別
提供 writeonly 存取紋理。  
  
## <a name="syntax"></a>語法  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
class writeonly_texture_view;  
 
template <
    typename value_type,  
    int _Rank  
>  
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;  
```  
  
#### <a name="parameters"></a>參數  
 `value_type`  
 紋理中的項目類型。  
  
 `_Rank`  
 紋理的陣序規範。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`scalar_type`||  
|`value_type`|紋理中的項目類型。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[writeonly_texture_view 建構函式](#ctor)|初始化 `writeonly_texture_view` 類別的新執行個體。|  
|[~ writeonly_texture_view 解構函式](#ctor)|終結`writeonly_texture_view`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[set](#set)|指定索引處設定項目的值。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|複製指定`writeonly_texture_view`這個物件。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[rank 常數](#rank)|取得的順位`writeonly_texture_view`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Texture_base`  
  
 `writeonly_texture_view`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp_graphics.h  
  
 **命名空間︰** concurrency:: graphics  
  
##  <a name="dtor"></a>~ writeonly_texture_view 

 終結`writeonly_texture_view`物件。  
  
```  
~writeonly_texture_view() restrict(amp,cpu);
```  
  
##  <a name="operator_eq"></a>運算子 = 

 複製指定`writeonly_texture_view`這個物件。  
  
```  
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `writeonly_texture_view`若要從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 參考`writeonly_texture_view`物件。  
  
##  <a name="rank"></a>陣序規範 

 取得的順位`writeonly_texture_view`物件。  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="set"></a>設定 

 指定索引處設定項目的值。  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 項目的索引。  
  
 `value`  
 項目的新值。  
  
##  <a name="ctor"></a>writeonly_texture_view 

 初始化 `writeonly_texture_view` 類別的新執行個體。  
  
```  
writeonly_texture_view(
    texture<value_type, 
    _Rank>& _Src) restrict(amp);

 
writeonly_texture_view(
    const writeonly_texture_view<value_type,  
    _Rank>& _Src) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 紋理的陣序規範。  
  
 `value_type`  
 紋理中的項目類型。  
  
 `_Src`  
 用來建立紋理`writeonly_texture_view`。  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)

