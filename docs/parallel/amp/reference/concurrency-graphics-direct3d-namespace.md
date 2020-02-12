---
title: Concurrency::graphics::direct3d 命名空間
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d
- amp_short_vectors/Concurrency::graphics::direct3d
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
ms.openlocfilehash: 4911787fd17877769eb723cf1e61e29fe626a783
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139430"
---
# <a name="concurrencygraphicsdirect3d-namespace"></a>Concurrency::graphics::direct3d 命名空間

提供[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)和[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)方法。

## <a name="syntax"></a>語法

```cpp
namespace direct3d;
```

## <a name="members"></a>成員

### <a name="functions"></a>函式

|名稱<br /><br /> 描述|
|--------------------------|
|[get_sampler](concurrency-graphics-direct3d-namespace-functions.md#get_sampler)<br /><br /> 在指定的快速鍵對應上取得 Direct3D 取樣器狀態介面，以代表指定的取樣器物件。|
|[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)<br /><br /> 取得以指定之[材質](texture-class.md)物件為基礎的 Direct3D 材質介面。|
|[make_sampler](concurrency-graphics-direct3d-namespace-functions.md#make_sampler)<br /><br /> 從 Direct3D 取樣器狀態介面指標建立取樣器。|
|[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)<br /><br /> 使用指定的參數建立[材質](texture-class.md)物件。|
|[msad4](concurrency-graphics-direct3d-namespace-functions.md#msad4)<br /><br /> 比較4個位元組的參考值和8個位元組的來源值，並累計4個總和的向量。|

## <a name="requirements"></a>需求

**標頭：** amp_graphics。h

**命名空間：** Concurrency：： graphics

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)
