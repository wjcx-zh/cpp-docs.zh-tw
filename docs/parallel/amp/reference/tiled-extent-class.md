---
title: "tiled_extent 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
dev_langs:
- C++
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: e295b56290435a1d87ac2f0dbc0951850600534d
ms.lasthandoff: 03/31/2017

---
# <a name="tiledextent-class"></a>tiled_extent 類別
A`tiled_extent`物件是`extent`細分成一段、 兩段或 3d 圖格的範圍空間一到三個維度的物件。  
  
### <a name="syntax"></a>語法  
  
```  
template <
    int _Dim0,  
    int _Dim1,  
    int _Dim2  
>  
class tiled_extent : public Concurrency::extent<3>;  
 
template <
    int _Dim0,  
    int _Dim1  
>  
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;  
 
template <
    int _Dim0  
>  
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;  
```  
  
### <a name="parameters"></a>參數  
 `_Dim0`  
 最重要的維度的長度。  
  
 `_Dim1`  
 下一步 以最重要維度的長度。  
  
 `_Dim2`  
 最小顯著性維度的長度。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[tiled_extent 建構函式](#ctor)|初始化 `tiled_extent` 類別的新執行個體。|  

  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[get_tile_extent](#get_tile_extent)|傳回`extent`物件，以擷取的值`tiled_extent`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。|  
|[填補](#pad)|傳回新`tiled_extent`向上調整為整除磚維度的範圍的物件。|  
|[截斷](#truncate)|傳回新`tiled_extent`與範圍的物件向下調整為整除圖格維度。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[operator=](#operator_eq)|將指定的內容複製`tiled_index`成這一個物件。|  

  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[tile_dim0 常數](#tile_dim0)|會儲存最重要的維度的長度。|  
|[tile_dim1 常數](#tile_dim1)|儲存下一步 以最重要維度的長度。|  
|[tile_dim2 常數](#tile_dim2)|會儲存最小顯著性維度的長度。|  

  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|取得`extent`物件，以擷取的值`tiled_extent`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `extent`  
  
 `tiled_extent`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  

## <a name="ctor"></a> tiled_extent 建構函式  
初始化 `tiled_extent` 類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```  
tiled_extent();  
  
tiled_extent(  
    const Concurrency::extent<rank>& _Other );  
  
tiled_extent(  
    const tiled_extent& _Other );  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `extent`或`tiled_extent`来複製物件。  
  

  

## <a name="get_tile_extent"></a> get_tile_extent   
傳回`extent`物件，以擷取的值`tiled_extent`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。  
  
### <a name="syntax"></a>語法  
  
```  
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>傳回值  
 `extent`擷取這個維度物件`tiled_extent`執行個體。  
  

## <a name="pad"></a>  pad   
傳回新`tiled_extent`向上調整為整除磚維度的範圍的物件。  
  
### <a name="syntax"></a>語法  
  
```  
tiled_extent pad() const;  
```  
  
### <a name="return-value"></a>傳回值  
 新`tiled_extent`傳值物件。 
## <a name="truncate"></a>截斷   
傳回新`tiled_extent`與範圍的物件向下調整為整除圖格維度。  
  
### <a name="syntax"></a>語法  
  
```  
tiled_extent truncate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回新`tiled_extent`與範圍的物件向下調整為整除圖格維度。  

## <a name="operator_eq"></a>運算子 =   
將指定的內容複製`tiled_index`成這一個物件。  
  
### <a name="syntax"></a>語法  
  
```  
tiled_extent&  operator= (  
    const tiled_extent& _Other ) restrict (amp, cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `tiled_index`從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`tiled_index`執行個體。  

## <a name="tile_dim0"></a> tile_dim0   
會儲存最重要的維度的長度。  
  
### <a name="syntax"></a>語法  
  
```  
static const int tile_dim0 = _Dim0;  
```  
  
## <a name="tile_dim1"></a> tile_dim1   
儲存下一步 以最重要維度的長度。  
  
### <a name="syntax"></a>語法  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tile_dim2"></a> tile_dim2   
會儲存最小顯著性維度的長度。  
  
### <a name="syntax"></a>語法  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tile_extent"></a> tile_extent   
  取得`extent`物件，以擷取的值`tiled_extent`樣板引數`_Dim0`， `_Dim1`，和`_Dim2`。  
  
### <a name="syntax"></a>語法  
  
```  
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;  
```  
  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

