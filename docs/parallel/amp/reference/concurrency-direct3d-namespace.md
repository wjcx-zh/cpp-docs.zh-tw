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
ms.openlocfilehash: e1374acbd7061afaba372100cf6e69d9d717da8a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127029"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 命名空間

`direct3d` 命名空間提供支援 D3D 互通性的功能。 它可讓您在 AMP 程式碼中使用 D3D 資源來進行計算。 它也允許使用在 D3D 程式碼中建立的資源，而不需要建立多餘的中繼複本。 您可以使用C++ amp，以累加方式加速 DirectX 應用程式的大量計算區段，並在 AMP 計算所產生的資料上使用 D3D API。

## <a name="syntax"></a>語法

```cpp
namespace direct3d;
```

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[scoped_d3d_access_lock 類別](scoped-d3d-access-lock-class.md)|`accelerator_view` 物件上 D3D 存取鎖定的 RAII 包裝函式。|

### <a name="structures"></a>結構

|名稱|描述|
|----------|-----------------|
|[adopt_d3d_access_lock_t 結構](adopt-d3d-access-lock-t-structure.md)|標記類型，表示應採用 D3D 存取鎖定，而不是取得。|

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|傳回引數的絕對值。|
|[夾具](concurrency-direct3d-namespace-functions-amp.md#clamp)|已多載。 強加 _X 至指定的 _Min 和 _Max 範圍|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|計算 _X 中的設定位數目|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|從 Direct3D 裝置介面的指標建立[Accelerator_view 類別](accelerator-view-class.md)|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|取得 accelerator_view 的鎖定，以安全地在與 accelerator_view 共用的資源上執行 D3D 作業|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|嘗試取得 accelerator_view 上的 D3D 存取鎖定，而不封鎖。|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|釋放指定 accelerator_view 上的 D3D 存取鎖定。|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|取得 _X 中第一個設定位的位置，從最高的順序位開始並向下工作|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|取得 _X 中第一個設定位的位置，從最低順序位開始並向上工作|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|取得陣列基礎的 D3D 緩衝區介面。|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|比較兩個值，傳回較大的值。|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|比較兩個值，傳回較小的值。|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|傳回布林旗標，指出是否已針對指定的 accelerator_view 停用 timeout。|
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|已多載。 在三個引數上執行算術乘法/add 運算： _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|從 D3D 緩衝區介面指標建立陣列。|
|[雜色](concurrency-direct3d-namespace-functions-amp.md#noise)|使用 Perlin 雜訊演算法產生隨機值|
|[為](concurrency-direct3d-namespace-functions-amp.md#radians)|將 _X 從角度轉換成弧度|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|計算引數的快速、近似倒數|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|反轉中的位順序 _X|
|[達到](concurrency-direct3d-namespace-functions-amp.md#saturate)|強加介於0到1的範圍內 _X|
|[簽署](concurrency-direct3d-namespace-functions-amp.md#sign)|已多載。 傳回引數的正負號|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|如果 _X 位於範圍 [_Min，_Max]，則傳回介於0和1之間的平滑 Hermite 插補。|
|[步驟](concurrency-direct3d-namespace-functions-amp.md#step)|比較兩個值，傳回0或1（根據值較大）|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|比較兩個不帶正負號的值，傳回大於的值。|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|比較兩個不帶正負號的值，傳回較小的值。|

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
