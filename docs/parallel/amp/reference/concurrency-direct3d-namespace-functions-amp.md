---
title: Concurrency::direct3d 命名空間函式 (AMP)
ms.date: 08/31/2018
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::get_device
- amp/Concurrency::direct3d::imax
- amp/Concurrency::direct3d::is_timeout_disabled
- amp/Concurrency::direct3d::mad
- amp/Concurrency::direct3d::noise
- amp/Concurrency::direct3d::radians
- amp/Concurrency::direct3d::reversebits
- amp/Concurrency::direct3d::saturate
- amp/Concurrency::direct3d::smoothstep
- amp/Concurrency::direct3d::step
- amp/Concurrency::direct3d::umin
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
ms.openlocfilehash: 438d211ac2f15bf781b704a7d0d7484d1542f131
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127042"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d 命名空間函式 (AMP)

||||
|-|-|-|
|[abs](#abs)|[夾具](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[mad](#mad)|[make_array](#make_array)|[雜色](#noise)|
|[為](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|
|[達到](#saturate)|[簽署](#sign)|[smoothstep](#smoothstep)|
|[步驟](#step)|[umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>需求

**Header：** Amp**命名空間：** 並行

## <a name="abs"></a>  abs

傳回引數的絕對值。

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的絕對值。

## <a name="clamp"></a>夾具

將第一個指定引數壓制的值，計算為由第二個和第三個指定引數所定義的範圍。

```cpp
inline float clamp(
    float _X,
    float _Min,
    float _Max) restrict(amp);

inline int clamp(
    int _X,
    int _Min,
    int _Max) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
要壓制的值

*_Min*<br/>
固定範圍的下限。

*_Max*<br/>
固定範圍的上限。

### <a name="return-value"></a>傳回值

`_X`的壓制值。

## <a name="countbits"></a>countbits

計算 _X 中的設定位數目

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
不帶正負號的整數值

### <a name="return-value"></a>傳回值

傳回 _X 中的集合位數目

## <a name="create_accelerator_view"></a>create_accelerator_view

從 Direct3D 裝置介面的指標建立[accelerator_view](accelerator-view-class.md)物件。

## <a name="syntax"></a>語法

```cpp
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>參數

*_Accelerator*<br/>
要在其上建立新 accelerator_view 的加速器。

*_D3D_device*<br/>
Direct3D 裝置介面的指標。

*_Disable_timeout*<br/>
布林值參數，指定是否應該針對新建立的 accelerator_view 停用 timeout。 這對應于 Direct3D 裝置建立的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標，用來指出作業系統是否應允許執行超過2秒的工作負載，而不需要在每個 Windows TIMEOUT 中重設裝置。偵測和修復機制。 如果您需要在 accelerator_view 上執行耗時的工作，建議使用此旗標。

*_Qmode*<br/>
要用於新建立之 accelerator_view 的[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) 。 此參數的預設值為 `queuing_mode_automatic`。

## <a name="return-value"></a>傳回值

從傳遞的 Direct3D 裝置介面建立的 `accelerator_view` 物件。

## <a name="remarks"></a>備註

此函式會從現有的 Direct3D 裝置介面指標建立新的 `accelerator_view` 物件。 如果函式呼叫成功，參數的參考計數會藉由對介面的 `AddRef` 呼叫來遞增。 當您的 DirectX 程式碼不再需要該物件時，您可以安全地將它釋放。 如果方法呼叫失敗，則會擲回[runtime_exception](runtime-exception-class.md) 。

您使用此函數建立的 `accelerator_view` 物件是安全線程。 您必須同步處理 `accelerator_view` 物件的並行使用。 未同步處理 `accelerator_view` 物件的並行使用，而原始 ID3D11Device 介面導致未定義的行為。

如果C++您使用 `D3D11_CREATE_DEVICE_DEBUG` 旗標，AMP 執行時間會使用 D3D debug 層，在 debug 模式中提供詳細的錯誤資訊。

## <a name="d3d_access_lock"></a>d3d_access_lock

取得 accelerator_view 的鎖定，以安全地在與 accelerator_view 共用的資源上執行 D3D 作業。 在執行作業時C++ ，與此 accelerator_view 相關聯的 accelerator_view 和所有 AMP 資源會在內部執行此鎖定，而當另一個執行緒持有 D3D 存取鎖定時，將會封鎖此鎖定。 這是非遞迴的鎖定：它是未定義的行為，從已持有鎖定的執行緒呼叫此函式。 這是未定義的行為，可在 accelerator_view 上執行作業，或從保留 D3D 存取鎖定的執行緒中，對任何與 accelerator_view 相關聯的資料容器進行操作。 另請參閱 scoped_d3d_access_lock，這是以範圍為基礎之 D3D 存取鎖定的 RAII 樣式類別。

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要鎖定的 accelerator_view。

## <a name="d3d_access_try_lock"></a>d3d_access_try_lock

嘗試取得 accelerator_view 上的 D3D 存取鎖定，而不封鎖。

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要鎖定的 accelerator_view。

### <a name="return-value"></a>傳回值

如果已取得鎖定，則為 true，如果目前已由另一個執行緒保留，則為 false。

## <a name="d3d_access_unlock"></a>d3d_access_unlock

釋放指定 accelerator_view 上的 D3D 存取鎖定。 如果呼叫的執行緒未持有 accelerator_view 的鎖定，則結果會是未定義的。

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要釋放鎖定的 accelerator_view。

## <a name="firstbithigh"></a>firstbithigh

取得 _X 中第一個設定位的位置，以最高序位位開頭，並移至最低序位位。

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

第一個設定位的位置

## <a name="firstbitlow"></a>firstbitlow

取得 _X 中第一個設定位的位置，以最低序位位開頭，並使用最高序位位。

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回第一個設定位的位置。

## <a name="get_buffer"></a>get_buffer

取得指定陣列基礎的 Direct3D 緩衝區介面。

```cpp
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>參數

*value_type*<br/>
陣列中項目的型別。

*_Rank*<br/>
陣列的順位。

*_Array*<br/>
Direct3D accelerator_view 上的陣列，其會傳回基礎 Direct3D 緩衝區介面。

### <a name="return-value"></a>傳回值

與陣列基礎的 Direct3D 緩衝區對應的 IUnknown 介面指標。

## <a name="a-nameget_device-get_device"></a><a name="get_device"> get_device

取得以 accelerator_view 為基礎的 D3D 裝置介面。

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>參數

*Av*<br/>
傳回基礎 D3D 裝置介面的 D3D accelerator_view。

### <a name="return-value"></a>傳回值

Accelerator_view 基礎之 D3D 裝置的 `IUnknown` 介面指標。

## <a name="imax"></a>imax

判斷引數的最大數值

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

*_Y*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的最大數值

## <a name="imin"></a>imin

判斷引數的最小數值

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

*_Y*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的最小數值

## <a name="is_timeout_disabled"></a>is_timeout_disabled

傳回布林旗標，指出是否已針對指定的 accelerator_view 停用 timeout。 這對應于 Direct3D 裝置建立的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標。

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>參數

*_Accelerator_view*<br/>
要查詢其已停用超時設定的 accelerator_view。

### <a name="return-value"></a>傳回值

布林值旗標，指出是否已針對指定的 accelerator_view 停用 timeout。

## <a name="mad"></a>mad

計算第一個和第二個指定引數的乘積，然後加入第三個指定的引數。

```cpp
inline float mad(
    float _X,
    float _Y,
    float _Z) restrict(amp);

inline double mad(
    double _X,
    double _Y,
    double _Z) restrict(amp);

inline int mad(
    int _X,
    int _Y,
    int _Z) restrict(amp);

inline unsigned int mad(
    unsigned int _X,
    unsigned int _Y,
    unsigned int _Z) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
第一個指定的引數。

*_Y*<br/>
第二個指定的引數。

*_Z*<br/>
第三個指定的引數。

### <a name="return-value"></a>傳回值

`_X` \* `_Y` + `_Z`的結果。

## <a name="make_array"></a>make_array

從 Direct3D 緩衝區介面指標建立陣列。

```cpp
template<
    typename value_type,
    int _Rank
>
array<value_type, _Rank> make_array(
    const extent<_Rank>& _Extent,
    const Concurrency::accelerator_view& _Rv,
    IUnknown* _D3D_buffer)  ;
```

### <a name="parameters"></a>參數

*value_type*<br/>
要建立之陣列的元素類型。

*_Rank*<br/>
要建立之陣列的順位。

*_Extent*<br/>
描述陣列匯總之圖形的範圍。

*_Rv*<br/>
要在其上建立陣列的 D3D 加速器視圖。

*_D3D_buffer*<br/>
要從中建立陣列的 D3D 緩衝區的 IUnknown 介面指標。

### <a name="return-value"></a>傳回值

使用提供的 Direct3D 緩衝區建立的陣列。

## <a name="noise"></a>雜色

使用 Perlin 雜訊演算法產生隨機值

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
要從中產生 Perlin 雜訊的浮點值

### <a name="return-value"></a>傳回值

傳回介於-1 到1的範圍內的 Perlin 雜訊值

## <a name="radians"></a>為

將 _X 從角度轉換成弧度

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回從度數轉換成弧度 _X

## <a name="rcp"></a>rcp

使用快速近似值，計算指定引數的倒數。

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
要計算倒數的值。

### <a name="return-value"></a>傳回值

指定引數的倒數。

## <a name="reversebits"></a>reversebits

反轉中的位順序 _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
不帶正負號的整數值

### <a name="return-value"></a>傳回值

傳回在中，位順序反轉的值 _X

## <a name="saturate"></a>達到

強加介於0到1的範圍內 _X

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回0到1範圍內的 _X 壓制

## <a name="sign"></a>簽訂

判斷指定引數的正負號。

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

引數的正負號。

## <a name="smoothstep"></a>smoothstep

如果 _X 位於範圍 [_Min，_Max]，則傳回介於0和1之間的平滑 Hermite 插補。

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_Min*<br/>
浮點值。

*_Max*<br/>
浮點值。

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

如果 _X 小於 _Min，則傳回 0;如果 _X 大於 _Max，則為 1;否則，如果 _X 位於範圍 [_Min，_Max]，則介於0和1之間的值

## <a name="step"></a>步驟

比較兩個值，傳回0或1（根據值較大）

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_Y*<br/>
浮點值。

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

如果 _X 大於或等於 _Y，則傳回 1;否則為0

## <a name="umax"></a>umax

判斷引數的最大數值

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

*_Y*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的最大數值

## <a name="umin"></a>umin

判斷引數的最小數值

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

*_Y*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的最小數值

## <a name="see-also"></a>另請參閱

[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)
