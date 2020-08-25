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
ms.openlocfilehash: bf98249001c2b8227581fbbbcceeebd085e5d820
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831108"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d 命名空間函式 (AMP)

:::row:::
   :::column span="":::
      [Abs](#abs)\
      [鉗](#clamp)\
      [countbits](#countbits)\
      [create_accelerator_view](#create_accelerator_view)\
      [d3d_access_lock](#d3d_access_lock)\
      [d3d_access_try_lock](#d3d_access_try_lock)\
      [d3d_access_unlock](#d3d_access_unlock)
   :::column-end:::
   :::column span="":::
      [firstbithigh](#firstbithigh)\
      [firstbitlow](#firstbitlow)\
      [get_buffer](#get_buffer)\
      [get_device](#get_device)\
      [Imax](#imax)\
      [imin](#imin)\
      [is_timeout_disabled](#is_timeout_disabled)
   :::column-end:::
   :::column span="":::
      [瘋狂](#mad)\
      [make_array](#make_array)\
      [雜訊](#noise)\
      [弧度](#radians)\
      [Rcp](#rcp)\
      [reversebits](#reversebits)
   :::column-end:::
   :::column span="":::
      [飽和](#saturate)\
      [標誌](#sign)\
      [smoothstep](#smoothstep)\
      [步](#step)\
      [umax](#umax)\
      [umin](#umin)
   :::column-end:::
:::row-end:::

## <a name="requirements"></a>規格需求

**Header：** Amp **命名空間：** 並行

## <a name="abs"></a><a name="abs"></a> Abs

傳回引數的絕對值。

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的絕對值。

## <a name="clamp"></a><a name="clamp"></a> 鉗

將第一個指定引數壓制的值，計算為第二個和第三個指定引數所定義的範圍。

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

的壓制值 `_X` 。

## <a name="countbits"></a><a name="countbits"></a> countbits

計算 _X 中的設定位數數目

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
不帶正負號的整數值

### <a name="return-value"></a>傳回值

傳回 _X 中的設定位數目

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a> create_accelerator_view

從 Direct3D 裝置介面的指標建立 [accelerator_view](accelerator-view-class.md) 物件。

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
布林值參數，指定是否應該針對新建立的 accelerator_view 停用 timeout。 這對應于 Direct3D 裝置建立的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標，用來指出作業系統是否應允許超過2秒的工作負載執行，而不需要根據 Windows TIMEOUT 偵測和復原機制重設裝置。 如果您需要在 accelerator_view 上執行耗時的工作，建議使用這個旗標。

*_Qmode*<br/>
要用於新建立之 accelerator_view 的 [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) 。 此參數的預設值為 `queuing_mode_automatic` 。

## <a name="return-value"></a>傳回值

`accelerator_view`從傳遞的 Direct3D 裝置介面建立的物件。

## <a name="remarks"></a>備註

此函 `accelerator_view` 式會從現有的 Direct3D 裝置介面指標建立新的物件。 如果函式呼叫成功，參數的參考計數就會藉由 `AddRef` 呼叫介面來遞增。 您可以在 DirectX 程式碼中不再需要物件時，安全地釋放該物件。 如果方法呼叫失敗，則會擲回 [runtime_exception](runtime-exception-class.md) 。

`accelerator_view`您使用此函數所建立的物件是安全線程。 您必須同步處理物件的並行使用 `accelerator_view` 。 `accelerator_view`物件和原始 ID3D11Device 介面的並行使用未同步處理會造成未定義的行為。

如果您使用旗標，C++ AMP 執行時間會使用 D3D Debug 層，在偵測模式中提供詳細的錯誤資訊 `D3D11_CREATE_DEVICE_DEBUG` 。

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a> d3d_access_lock

取得 accelerator_view 的鎖定，以安全地在與 accelerator_view 共用的資源上執行 D3D 作業。 Accelerator_view 以及與此 accelerator_view 相關聯的所有 C++ AMP 資源在執行作業時，會在內部執行此鎖定，而且會在另一個執行緒保留 D3D 存取鎖定時封鎖。 此鎖定為非遞迴：它是未定義的行為，無法從已經保存鎖定的執行緒呼叫這個函式。 這是未定義的行為，可在 accelerator_view 或任何與保存 D3D 存取鎖定的執行緒中 accelerator_view 相關聯的資料容器上執行作業。 另請參閱 scoped_d3d_access_lock，也就是以範圍為基礎的 D3D 存取鎖定的 RAII 樣式類別。

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要鎖定的 accelerator_view。

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a> d3d_access_try_lock

嘗試在不封鎖的情況下取得 accelerator_view 的 D3D 存取鎖定。

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要鎖定的 accelerator_view。

### <a name="return-value"></a>傳回值

如果已取得鎖定，則為 true; 如果目前由另一個執行緒保留，則為 false。

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a> d3d_access_unlock

釋放指定 accelerator_view 上的 D3D 存取鎖定。 如果呼叫的執行緒未持有 accelerator_view 的鎖定，則結果為未定義。

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要釋放鎖定的 accelerator_view。

## <a name="firstbithigh"></a><a name="firstbithigh"></a> firstbithigh

取得 _X 中第一個集合位的位置，以最高序位位為開頭，並移至最低序位位。

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

第一個設定位的位置

## <a name="firstbitlow"></a><a name="firstbitlow"></a> firstbitlow

取得 _X 中第一個集合位的位置，以最低順序位為開頭，並朝最高序位位。

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回第一個 set 位的位置

## <a name="get_buffer"></a><a name="get_buffer"></a> get_buffer

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
Direct3D accelerator_view 上的陣列，會傳回基礎 Direct3D 緩衝區介面。

### <a name="return-value"></a>傳回值

IUnknown 介面指標，對應至陣列基礎的 Direct3D 緩衝區。

## <a name="a-nameget_device-get_device"></a><a name="get_device"> get_device

取得以 accelerator_view 為基礎的 D3D 裝置介面。

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>參數

*Av*<br/>
傳回基礎 D3D 裝置介面的 D3D accelerator_view。

### <a name="return-value"></a>傳回值

`IUnknown`Accelerator_view 基礎之 D3D 裝置的介面指標。

## <a name="imax"></a><a name="imax"></a> Imax

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

## <a name="imin"></a><a name="imin"></a> imin

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

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a> is_timeout_disabled

傳回布林值旗標，指出是否已針對指定的 accelerator_view 停用 timeout。 這會對應至建立 Direct3D 裝置的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標。

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>參數

*_Accelerator_view*<br/>
要查詢已停用 timeout 設定的 accelerator_view。

### <a name="return-value"></a>傳回值

布林值旗標，指出是否已針對指定的 accelerator_view 停用 timeout。

## <a name="mad"></a><a name="mad"></a> 瘋狂

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

的結果 `_X` \* `_Y`  +  `_Z` 。

## <a name="make_array"></a><a name="make_array"></a> make_array

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
描述陣列匯總之形狀的範圍。

*_Rv*<br/>
要在其上建立陣列的 D3D 加速器視圖。

*_D3D_buffer*<br/>
要從中建立陣列之 D3D 緩衝區的 IUnknown 介面指標。

### <a name="return-value"></a>傳回值

使用提供的 Direct3D 緩衝區建立的陣列。

## <a name="noise"></a><a name="noise"></a> 雜訊

使用 Perlin 雜訊演算法產生隨機值

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
要產生 Perlin 雜訊的浮點值

### <a name="return-value"></a>傳回值

傳回介於-1 和1之間範圍內的 Perlin 雜訊值

## <a name="radians"></a><a name="radians"></a> 弧度

將 _X 從度數轉換為弧度

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 從度數轉換為弧度

## <a name="rcp"></a><a name="rcp"></a> Rcp

使用快速近似值，計算指定之引數的倒數。

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
要計算倒數的值。

### <a name="return-value"></a>傳回值

指定之引數的倒數。

## <a name="reversebits"></a><a name="reversebits"></a> reversebits

反轉 _X 中的位順序

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
不帶正負號的整數值

### <a name="return-value"></a>傳回值

傳回在 _X 中反轉位順序的值

## <a name="saturate"></a><a name="saturate"></a> 飽和

個在0到1的範圍內 _X

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回0到1範圍內 _X 壓制

## <a name="sign"></a><a name="sign"></a> 標誌

判斷指定之引數的正負號。

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

引數的正負號。

## <a name="smoothstep"></a><a name="smoothstep"></a> smoothstep

如果 _X 在範圍 [_Min，_Max]，則會傳回介於0和1之間的平滑 Hermite 插補。

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

如果 _X 小於 _Min，則傳回 0;1，如果 _X 大於 _Max;否則，如果 _X 是在範圍 [_Min，_Max]，則介於0和1之間的值

## <a name="step"></a><a name="step"></a> 步

比較兩個值，並根據值較大的值傳回0或1

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

## <a name="umax"></a><a name="umax"></a> umax

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

## <a name="umin"></a><a name="umin"></a> umin

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
