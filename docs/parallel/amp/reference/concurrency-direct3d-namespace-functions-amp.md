---
title: Concurrency::direct3d 命名空間函式 (AMP) |Microsoft Docs
ms.custom: ''
ms.date: 08/31/2018
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fc56ca800b3e6028d26a64be7323a681589430e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426051"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d 命名空間函式 (AMP)

||||
|-|-|-|
|[abs](#abs)|[clamp](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[mad](#mad)|[make_array](#make_array)|[雜訊](#noise)|
|[弧度為單位](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|
|[saturate](#saturate)|[簽署](#sign)|[smoothstep](#smoothstep)|
|[step](#step)|[umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>需求

**標頭：** amp.h**命名空間：** 並行存取

##  <a name="abs"></a>  abs

傳回引數的絕對值

```
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回引數的絕對值。

##  <a name="clamp"></a>  clamp

計算的值壓制為範圍，第二個和第三個指定的引數所定義的第一個指定引數。

```
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
值，以限制在

*_Min*<br/>
限制範圍的下限。

*_Max*<br/>
限制範圍的上限。

### <a name="return-value"></a>傳回值

受限的值`_X`。

##  <a name="countbits"></a>  countbits

計算 _X 中的設定位元數

```
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
不帶正負號的整數值

### <a name="return-value"></a>傳回值

傳回 _X 中的設定位元數目

## <a name="create_accelerator_view"></a> create_accelerator_view

會建立[accelerator_view](accelerator-view-class.md)從指標到 Direct3D 裝置介面的物件。

## <a name="syntax"></a>語法

```
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

#### <a name="parameters"></a>參數

*_Accelerator*<br/>
建立新 accelerator_view 所在的加速器。

*_D3D_device*<br/>
Direct3D 裝置介面指標。

*_Disable_timeout*<br/>
布林值參數指定的新建立的 accelerator_view 是否應該停用逾時。 這對應到 Direct3D 裝置建立的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標，用來指出作業系統是否應該允許需要超過 2 秒的時間執行，而不將裝置重設每個 Windows 逾時的工作負載偵測和復原機制。 如果您需要在 accelerator_view 執行費時的工作，建議使用這個旗標。

*_Qmode*<br/>
[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)来用於新建立的 accelerator_view。 此參數的預設值是`queuing_mode_automatic`。

## <a name="return-value"></a>傳回值

`accelerator_view`從傳遞的 Direct3D 裝置介面建立物件。

## <a name="remarks"></a>備註

此函式會建立新`accelerator_view`從現有指標到 Direct3D 裝置介面的物件。 如果函式呼叫成功，此參數的參考計數會遞增藉由`AddRef`的介面呼叫。 它不再需要 DirectX 程式碼時，您可以安全地釋放物件。 如果方法呼叫失敗， [runtime_exception](runtime-exception-class.md)就會擲回。

`accelerator_view`您使用此函式建立的物件為安全執行緒。 您必須同步處理同時使用`accelerator_view`物件。 非同步並行使用方式的`accelerator_view`物件和原始 ID3D11Device 介面會導致未定義的行為。

C + + AMP 執行階段會提供詳細的錯誤資訊，偵錯模式中使用 D3D 偵錯層，如果您使用`D3D11_CREATE_DEVICE_DEBUG`旗標。

##  <a name="d3d_access_lock"></a>  d3d_access_lock

取得對 accelerator_view 來安全地執行與 accelerator_view 共用的資源執行 D3D 作業鎖定。 Accelerator_view 和內部與這個 accelerator_view 相關聯的所有 c + + AMP 資源取得這個鎖定執行作業時，會封鎖，而另一個執行緒持有 D3D 存取鎖定。 這個鎖定是非遞迴： 它是未定義的行為，可從已經保留鎖定的執行緒呼叫此函式。 它是未定義的行為，來執行對 accelerator_view 或任何與 accelerator_view，要從保持 D3D 存取鎖定的執行緒相關聯的資料容器的作業。 另請參閱 scoped_d3d_access_lock，範圍為基礎的 D3D 存取鎖定的 RAII 式類別。

```
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
鎖定的 accelerator_view。

##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock

嘗試取得對 accelerator_view 的 D3D 存取鎖定，而不會封鎖。

```
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
鎖定的 accelerator_view。

### <a name="return-value"></a>傳回值

如果已取得鎖定，則為 true 或 false，如果它目前保留由另一個執行緒。

##  <a name="d3d_access_unlock"></a>  d3d_access_unlock

釋放特定 accelerator_view 的 D3D 存取鎖定。 如果呼叫執行緒不適 accelerator_view 的鎖定是未定義的結果。

```
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要釋放鎖定的 accelerator_view。

##  <a name="firstbithigh"></a>  firstbithigh

取得從最高序位位元開始，並採用最低順序位元的 _X 中第一個設定位元的位置。

```
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

第一個設定位元的位置

##  <a name="firstbitlow"></a>  firstbitlow

取得從最低順序位元開始，朝 最高序位位元的 _X 中第一個設定位元的位置。

```
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回的第一個設定位元的位置

##  <a name="get_buffer"></a>  get_buffer

取得指定的陣列基礎 Direct3D 緩衝區介面。

```
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
陣列陣序。

*_Array*<br/>
這傳回基礎 Direct3D 緩衝區介面之 Direct3D accelerator_view 上陣列。

### <a name="return-value"></a>傳回值

IUnknown 介面指標對應至陣列的 Direct3D 緩衝區。

## <a name="a-namegetdevice-getdevice"></a><a name="get_device"> get_device

取得基礎 accelerator_view 的 D3D 裝置介面。

```
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>參數

*Av*<br/>
這傳回基礎 D3D 裝置介面 D3D accelerator_view。

### <a name="return-value"></a>傳回值

`IUnknown`基礎 accelerator_view 的 D3D 裝置介面指標。

##  <a name="imax"></a>  imax

判斷引數的最大數值

```
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

傳回的最大的數值引數

##  <a name="imin"></a>  imin

判斷引數的最小數值

```
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

##  <a name="is_timeout_disabled"></a>  is_timeout_disabled

傳回布林值旗標，指出是否停用指定的 accelerator_view 的逾時。 這會對應到 Direct3D 裝置建立的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標。

```
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>參數

*_Accelerator_view*<br/>
要查詢停用設定的逾時的 accelerator_view。

### <a name="return-value"></a>傳回值

布林值的旗標，表示是否停用指定的 accelerator_view 的逾時。

##  <a name="mad"></a>  mad

計算乘積的第一個和第二個指定引數，然後新增第三個指定的引數。

```
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

結果`_X` \* `_Y`  +  `_Z`。

##  <a name="make_array"></a>  make_array

從 Direct3D 緩衝區介面指標建立陣列。

```
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
要建立之陣列的項目型別。

*_Rank*<br/>
要建立之陣列的陣序規範。

*_Extent*<br/>
描述陣列彙總圖形的範圍。

*_Rv*<br/>
所建立的陣列的 D3D 加速器檢視。

*_D3D_buffer*<br/>
若要建立從陣列的 D3D 緩衝區的 IUnknown 介面指標。

### <a name="return-value"></a>傳回值

使用提供的 Direct3D 緩衝區建立陣列。

##  <a name="noise"></a>  雜訊

產生使用 Perlin 雜訊演算法的隨機值

```
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
要從中產生 Perlin 雜訊的浮點值

### <a name="return-value"></a>傳回值

傳回介於-1 和 1 之間的範圍內的 Perlin 雜訊值

##  <a name="radians"></a>  弧度為單位

將 _X 從角度轉換為弧度

```
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 從角度轉換成弧度

##  <a name="rcp"></a>  rcp

使用快速近似值計算指定的引數的倒數。

```
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
要計算其倒數的值。

### <a name="return-value"></a>傳回值

指定的引數的倒數。

##  <a name="reversebits"></a>  reversebits

反轉 _X 的位元組順序

```
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
不帶正負號的整數值

### <a name="return-value"></a>傳回值

反轉 _X 中的位元順序會傳回值

##  <a name="saturate"></a>  saturate

將 _X 介於 0 到 1 的限制

```
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回 _X 限制在 0 到 1 的範圍內

##  <a name="sign"></a>  符號

判斷指定的引數的正負號。

```
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

的引數的符號。

##  <a name="smoothstep"></a>  smoothstep

如果 _X 的範圍 [_Min，_Max] 會傳回 0 和 1 之間的平滑 Hermite 插補。

```
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

會傳回 0，如果 _X 小於 _Min;1 如果 _X 大於 _Max;否則，值介於 0 和 1，如果 _X 的範圍 [_Min，_Max]

##  <a name="step"></a>  步驟

比較兩個值，傳回 0 或 1 為基礎的值大於

```
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

會傳回 1，如果 _X 大於或等於 _Y;否則，便是 0

##  <a name="umax"></a>  umax

判斷引數的最大數值

```
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

傳回的最大的數值引數

##  <a name="umin"></a>  umin

判斷引數的最小數值

```
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
