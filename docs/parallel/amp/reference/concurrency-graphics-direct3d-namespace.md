---
title: Concurrency::graphics::direct3d 命名空間
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d
- amp_short_vectors/Concurrency::graphics::direct3d
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
ms.openlocfilehash: 2a07aeab410750e38684f564df4cb89c1846b95e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626820"
---
# <a name="concurrencygraphicsdirect3d-namespace"></a>Concurrency::graphics::direct3d 命名空間

提供[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)並[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)方法。

## <a name="syntax"></a>語法

```
namespace direct3d;
```

## <a name="members"></a>成員

### <a name="functions"></a>函式

|名稱<br /><br /> 描述|
|--------------------------|
|[get_sampler](concurrency-graphics-direct3d-namespace-functions.md#get_sampler)<br /><br /> 取得 Direct3D 取樣器狀態介面上的特定加速器檢視，代表指定之取樣器物件。|
|[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)<br /><br /> 取得指定基礎 d3d 材質介面[紋理](texture-class.md)物件。|
|[make_sampler](concurrency-graphics-direct3d-namespace-functions.md#make_sampler)<br /><br /> 從 Direct3D 取樣器狀態介面指標建立取樣器。|
|[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)<br /><br /> 會建立[紋理](texture-class.md)物件使用指定的參數。|
|[msad4](concurrency-graphics-direct3d-namespace-functions.md#msad4)<br /><br /> 比較 4 位元組參考值和 8 位元組來源值，並累積 4 個總和的向量。|

## <a name="requirements"></a>需求

**標頭：** amp_graphics.h

**命名空間：** concurrency:: graphics

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
