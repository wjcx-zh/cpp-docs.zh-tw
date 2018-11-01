---
title: Concurrency::direct3d 命名空間
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
ms.openlocfilehash: c99aba319df6f84dbda7b9cf90a1abebdc3757f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570348"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 命名空間

`direct3d`命名空間提供支援 D3D 互通性的函式。 它可充分運用 D3D 資源在 AMP 程式碼中的計算，以及允許使用的資源在 AMP 中 D3D 程式碼建立，而不需要建立中繼複本。 以累加方式加速 DirectX 應用程式的計算密集區段使用 c + + AMP 即可 D3D 介面用於 AMP 計算所產生的資料。

## <a name="syntax"></a>語法

```
namespace direct3d;
```

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[scoped_d3d_access_lock 類別](scoped-d3d-access-lock-class.md)|上的 D3D 存取鎖定的 RAII 包裝函式`accelerator_view`物件。|

### <a name="structures"></a>結構

|名稱|描述|
|----------|-----------------|
|[adopt_d3d_access_lock_t 結構](adopt-d3d-access-lock-t-structure.md)|若要表示的 D3D 存取鎖定的標記類型應該採用而取得。|

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|傳回引數的絕對值|
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|多載。 將指定的 _Min 和 _Max 範圍 _X 限制|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|計算 _X 中的設定位元數|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|會建立[accelerator_view 類別](accelerator-view-class.md)從指標到 Direct3D 裝置介面|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|取得來安全地執行與 accelerator_view 共用的資源執行 D3D 作業 accelerator_view 的鎖定|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|嘗試取得對 accelerator_view 的 D3D 存取鎖定，而不會封鎖。|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|釋放特定 accelerator_view 的 D3D 存取鎖定。|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|取得從最高序位位元向下的 _X 中第一個設定位元的位置|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|取得 _X，從最低序位位元開始向上中第一個設定位元的位置|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|取得陣列基礎的 D3D 緩衝區介面。|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|比較兩個值，傳回其中較大的值。|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|比較兩個值，傳回其中較小的值。|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|傳回布林值旗標，指出是否停用指定的 accelerator_view 的逾時。|
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|多載。 執行三個引數的算術乘法/加法運算： _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|從 D3D 緩衝區介面指標建立陣列。|
|[雜訊](concurrency-direct3d-namespace-functions-amp.md#noise)|使用 Perlin 雜訊演算法產生隨機值|
|[弧度為單位](concurrency-direct3d-namespace-functions-amp.md#radians)|將 _X 從角度轉換為弧度|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|計算引數快速近似倒數|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|反轉 _X 的位元組順序|
|[saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|將 _X 介於 0 到 1 的限制|
|[簽署](concurrency-direct3d-namespace-functions-amp.md#sign)|多載。 傳回引數的正負號|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|如果 _X 的範圍 [_Min，_Max] 會傳回 0 和 1 之間的平滑 Hermite 插補。|
|[step](concurrency-direct3d-namespace-functions-amp.md#step)|比較兩個值，傳回 0 或 1 為基礎的值大於|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|比較兩個不帶正負號的值，傳回其中較大的值。|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|比較兩個不帶正負號的值，傳回其中較小的值。|

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
