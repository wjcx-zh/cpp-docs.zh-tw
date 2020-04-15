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
ms.openlocfilehash: e21b1f2869ab81973b341abc5371714fbf8580e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375938"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d 命名空間函式 (AMP)

||||
|-|-|-|
|[Abs](#abs)|[鉗](#clamp)|[計數位](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[第一位高](#firstbithigh)|
|[第一比特洛](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[伊甯](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[瘋狂](#mad)|[make_array](#make_array)|[雜訊](#noise)|
|[弧度](#radians)|[rcp](#rcp)|[反向位](#reversebits)|
|[飽和](#saturate)|[標誌](#sign)|[平滑步驟](#smoothstep)|
|[步驟](#step)|[烏馬克斯](#umax)|[烏甯](#umin)|

## <a name="requirements"></a>需求

**標題:amp.h** **命名空間:** 併發性

## <a name="abs"></a><a name="abs"></a>Abs

傳回參數的絕對值

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

返回參數的絕對值。

## <a name="clamp"></a><a name="clamp"></a>鉗

計算第一個指定參數的值,該參數夾緊在第二個和第三個指定參數定義的範圍內。

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
要夾緊的值

*_Min*<br/>
夾緊範圍的下限。

*_Max*<br/>
夾緊範圍的上限。

### <a name="return-value"></a>傳回值

的夾緊值`_X`。

## <a name="countbits"></a><a name="countbits"></a>計數位

在_X中計算設定位數

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
沒有符號整數值

### <a name="return-value"></a>傳回值

傳回_X的設定位數

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a>create_accelerator_view

從指向 Direct3D 設備介面的指標創建[accelerator_view](accelerator-view-class.md)物件。

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
要創建新accelerator_view的加速器。

*_D3D_device*<br/>
指向 Direct3D 設備介面的指標。

*_Disable_timeout*<br/>
布爾參數,用於指定是否應為新創建的accelerator_view禁用超時。 這對應於 Direct3D 設備創建D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT標誌,用於指示作業系統是否應允許執行超過 2 秒的工作負載,而無需根據 Windows 超時檢測和恢復機制重置設備。 如果需要在accelerator_view執行耗時的任務,建議使用此標誌。

*_Qmode*<br/>
用於[新](concurrency-namespace-enums-amp.md#queuing_mode)創建的accelerator_viewqueuing_mode。 這裡的預設值為`queuing_mode_automatic`。

## <a name="return-value"></a>傳回值

從`accelerator_view`傳遞的 Direct3D 設備介面創建的物件。

## <a name="remarks"></a>備註

此函數從現有指標`accelerator_view`創建一個新物件到 Direct3D 設備介面。 如果函數調用成功,則參數的引用計數將通過使用對介面的`AddRef`調用增加。 當 DirectX 代碼中不再需要物件時,可以安全地釋放該物件。 如果方法調用失敗,將引發[runtime_exception。](runtime-exception-class.md)

使用此`accelerator_view`函數創建的對像是線程安全。 必須同步`accelerator_view`物件的併發使用。 `accelerator_view`物件和原始 ID3D11Device 介面的未同步併發使用會導致未定義的行為。

如果使用`D3D11_CREATE_DEVICE_DEBUG`標誌,C++ AMP 運行時通過使用 D3D 調試層在調試模式下提供詳細的錯誤資訊。

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a>d3d_access_lock

獲取accelerator_view上的鎖,以便對與accelerator_view共用的資源安全地執行 D3D 操作。 執行操作時,accelerator_view和所有與此accelerator_view關聯的所有C++ AMP 資源在內部獲取此鎖,並在另一個線程持有 D3D 訪問鎖時阻止。 此鎖是非遞歸的:從已持有鎖的線程調用此函數是未定義的行為。 從保存 D3D 訪問鎖的線程中對accelerator_view或任何與accelerator_view關聯的數據容器執行操作是未定義的行為。 另請參閱scoped_d3d_access_lock,即基於作用域的 D3D 訪問鎖的 RAII 樣式類。

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要鎖定accelerator_view。

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock

嘗試在accelerator_view上獲取 D3D 訪問鎖,而不會阻塞。

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要鎖定accelerator_view。

### <a name="return-value"></a>傳回值

如果獲取了鎖,則為 true,如果鎖當前由另一個線程持有,則為 false。

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a>d3d_access_unlock

釋放給定accelerator_view上的 D3D 訪問鎖。 如果調用線程未在accelerator_view上持有鎖,則結果未定義。

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要釋放鎖的accelerator_view。

## <a name="firstbithigh"></a><a name="firstbithigh"></a>第一位高

獲取_X中第一個集位的位置,從最高階位開始,然後向最低階位移動。

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

第一個設定位的位置

## <a name="firstbitlow"></a><a name="firstbitlow"></a>第一比特洛

獲取_X中第一個設置位的位置,從最低階位開始,然後朝著最高階位工作。

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

傳回第一個設定位的位置

## <a name="get_buffer"></a><a name="get_buffer"></a>get_buffer

獲取指定陣列基礎的 Direct3D 緩衝區介面。

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
Direct3D 上的陣列accelerator_view返回基礎 Direct3D 緩衝區介面。

### <a name="return-value"></a>傳回值

I未知介面指針對應於陣列基礎的 Direct3D 緩衝區。

## <a name="a-nameget_device-get_device"></a><a name="get_device">get_device

獲取accelerator_view基礎的 D3D 設備介面。

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>參數

*Av*<br/>
返回基礎 D3D 設備介面的 D3D accelerator_view。

### <a name="return-value"></a>傳回值

accelerator_view`IUnknown`基礎的 D3D 設備的介面指標。

## <a name="imax"></a><a name="imax"></a>Imax

確定參數的最大數值

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

傳回參數的最大數值

## <a name="imin"></a><a name="imin"></a>伊甯

確定參數的最小數值

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

傳回參數的最小數值

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a>is_timeout_disabled

返回一個布爾標誌,指示指定accelerator_view是否禁用超時。 這對應於 Direct3D 設備創建的D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT標誌。

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>參數

*_Accelerator_view*<br/>
要查詢已禁用超時設置accelerator_view。

### <a name="return-value"></a>傳回值

一個布爾標誌,指示指定accelerator_view是否禁用超時。

## <a name="mad"></a><a name="mad"></a>瘋狂

計算第一個和第二個指定參數的積,然後添加第三個指定的參數。

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
第一個指定的參數。

*_Y*<br/>
第二個指定的參數。

*_Z*<br/>
第三個指定的參數。

### <a name="return-value"></a>傳回值

`_X``_Y`的結果。 \* `_Z`  + 

## <a name="make_array"></a><a name="make_array"></a>make_array

從 Direct3D 緩衝區介面指標創建陣組。

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
要創建的陣列的元素類型。

*_Rank*<br/>
要創建的陣列的排名。

*_Extent*<br/>
描述陣列聚合形狀的範圍。

*_Rv*<br/>
要在其中創建陣列的 D3D 快速鍵檢視。

*_D3D_buffer*<br/>
D3D 緩衝區的I未知介面指標,用於從中創建陣列。

### <a name="return-value"></a>傳回值

使用提供的 Direct3D 緩衝區創建的陣列。

## <a name="noise"></a><a name="noise"></a>雜訊

使用佩林雜訊演算法產生隨機值

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
從中產生佩林雜訊的浮點值

### <a name="return-value"></a>傳回值

傳回 -1 和 1 之間範圍內的 Perlin 雜色值

## <a name="radians"></a><a name="radians"></a>弧度

將_X從度轉換為弧度

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

傳回從度轉換為弧度的_X

## <a name="rcp"></a><a name="rcp"></a>Rcp

使用快速近似計算指定參數的對數。

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
要計算對數的值。

### <a name="return-value"></a>傳回值

指定參數的對等項。

## <a name="reversebits"></a><a name="reversebits"></a>反向位

反轉_X位的順序

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
沒有符號整數值

### <a name="return-value"></a>傳回值

返回位訂單在_X中反轉的值

## <a name="saturate"></a><a name="saturate"></a>飽和

夾鉗_X 0 到 1 的範圍內

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
浮點值。

### <a name="return-value"></a>傳回值

返回_X夾在 0 到 1 的範圍內

## <a name="sign"></a><a name="sign"></a>標誌

確定指定參數的符號。

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>參數

*_X*<br/>
整數值

### <a name="return-value"></a>傳回值

參數的標誌。

## <a name="smoothstep"></a><a name="smoothstep"></a>平滑步驟

如果_X在 [_Min,_Max]範圍內,則返回介於 0 和 1 之間的平滑 Hermite 插值。

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

如果_X小於_Min,則返回 0;如果_X大於_Max;如果_X大於_Max;否則,如果_X在 [_Min,_Max] 範圍內,則介於 0 和 1 之間的值。

## <a name="step"></a><a name="step"></a>步

比較兩個值,返回 0 或 1 基於哪個值較大

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

如果_X大於或等於_Y,則返回 1;否則,0

## <a name="umax"></a><a name="umax"></a>烏馬克斯

確定參數的最大數值

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

傳回參數的最大數值

## <a name="umin"></a><a name="umin"></a>烏甯

確定參數的最小數值

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

傳回參數的最小數值

## <a name="see-also"></a>另請參閱

[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)
