---
title: "Concurrency:: direct3d 命名空間函式 (AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
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
dev_langs: C++
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: ad00006c9ab4f25887cf28ed5b977551c35bda9e
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency:: direct3d 命名空間函式 (AMP)
||||  
|-|-|-|  
|[abs](#abs)|[clamp](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|||
|[d3d_access_lock](#d3d_access_lock)|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|  
|[firstbithigh](#firstbithigh)|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|  
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|  
|[mad](#mad)|[make_array](#make_array)|[雜訊](#noise)|  
|[弧度為單位](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|  
|[saturate](#saturate)|[符號](#sign)|[smoothstep](#smoothstep)|  
|[步驟](#step)|[umax](#umax)|[umin](#umin)|  

## <a name="requirements"></a>需求
**標頭︰** amp.h**命名空間︰**並行存取
  
##  <a name="abs"></a>  abs  
 傳回引數的絕對值  
  
```  
inline int abs(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 傳回引數的絕對值。  
  
##  <a name="clamp"></a>clamp  
 計算第二個和第三個指定的引數所定義的範圍僅限於第一個指定引數的值。  
  
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
 `_X`  
 要被縮減的值  
  
 `_Min`  
 Clamping 範圍的下限。  
  
 `_Max`  
 Clamping 範圍的上限。  
  
### <a name="return-value"></a>傳回值  
 壓制的值`_X`。  
  
##  <a name="countbits"></a>countbits  
 計算集合中的位元 _X 數目  
  
```  
inline unsigned int countbits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 不帶正負號的整數值  
  
### <a name="return-value"></a>傳回值  
 傳回在 _X 組位元數  

## <a name="create_accelerator_view"></a>create_accelerator_view  
建立[accelerator_view](accelerator-view-class.md)指標 Direct3D 裝置介面的物件。  
  
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
 `_Accelerator`  
 建立新的 accelerator_view 所在的加速器。  
  
 `_D3D_device`  
 Direct3D 裝置介面指標。  
  
 `_Disable_timeout`  
 指定逾時是否應該停用新建立的 accelerator_view 的布林值參數。 這對應於 Direct3D 裝置建立的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標，用來表示是否作業系統應該允許花 2 秒以上來執行不含每個 Windows 逾時偵測和復原機制將裝置重設的工作負載。 如果您需要在 accelerator_view 執行耗時的工作，建議使用這個旗標。  
  
 `_Qmode`  
 [Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)来用於新建立的 accelerator_view。 此參數的預設值是`queuing_mode_automatic`。  
  
## <a name="return-value"></a>傳回值  
 `accelerator_view`建立傳遞 Direct3D 裝置介面的物件。  
  
## <a name="remarks"></a>備註  
 此函式會建立新`accelerator_view`從現有指標 Direct3D 裝置介面的物件。 如果函式呼叫成功，此參數的參考計數會遞增藉由`AddRef`呼叫的介面。 已不再需要在您的 DirectX 程式碼時，您可以安全地釋放物件。 如果方法呼叫失敗， [runtime_exception](runtime-exception-class.md)就會擲回。  
  
 `accelerator_view`物件，您使用此函式建立具備執行緒安全。 您必須同步處理同時使用`accelerator_view`物件。 未同步處理的並行使用量的`accelerator_view`物件和原始 ID3D11Device 介面會導致未定義的行為。  
  
 C + + AMP 執行階段會提供詳細的錯誤資訊，偵錯模式中使用偵錯 D3D 圖層，如果您使用`D3D11_CREATE_DEVICE_DEBUG`旗標。  
  
  
##  <a name="d3d_access_lock"></a>d3d_access_lock  
 取得 accelerator_view 為了安全地 D3D 上執行的作業與 accelerator_view 共用資源鎖定。 Accelerator_view 和所有的 c + + AMP 資源內部與此 accelerator_view 採取這種鎖定時執行作業，而另一個執行緒擁有 D3D 存取鎖定會封鎖。 這種鎖定為非遞迴︰ 它是從已經擁有鎖定的執行緒呼叫此函式未定義的行為。 它是未定義的行為 accelerator_view 或從包含 D3D 存取鎖定的執行緒 accelerator_view 相關聯的任何資料容器上執行作業。 請參閱 scoped_d3d_access_lock，範圍為基礎的 D3D 存取鎖定的 RAII 樣式類別。  
  
```  
void __cdecl d3d_access_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>參數  
 `_Av`  
 若要鎖定 accelerator_view。  
  
##  <a name="d3d_access_try_lock"></a>d3d_access_try_lock  
 嘗試取得 accelerator_view D3D 存取鎖定，而不會封鎖。  
  
```  
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>參數  
 `_Av`  
 若要鎖定 accelerator_view。  
  
### <a name="return-value"></a>傳回值  
 如果已取得鎖定，則為 true 或 false 目前由另一個執行緒。  
  
##  <a name="d3d_access_unlock"></a>d3d_access_unlock  
 釋放指定 accelerator_view D3D 存取鎖定。 如果呼叫執行緒不適 accelerator_view 的鎖定是未定義的結果。  
  
```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>參數  
 `_Av`  
 要釋放鎖定為 accelerator_view。  
  
##  <a name="firstbithigh"></a>firstbithigh  
 取得 _X，開頭為最高序位位元，採用最低位元中的第一組位元位置。  
  
```  
inline int firstbithigh(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 第一個設定位元的位置  
  
##  <a name="firstbitlow"></a>firstbitlow  
 取得 _X，開頭為最低位元，向的最高序位位元工作中的第一組位元位置。  
  
```  
inline int firstbitlow(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 傳回的第一個設定位元的位置  
  
##  <a name="get_buffer"></a>get_buffer  
 取得指定的陣列的基礎 Direct3D 緩衝區介面。  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;  
```  
  
### <a name="parameters"></a>參數  
 `value_type`  
 陣列中項目的型別。  
  
 `_Rank`  
 陣列的陣序規範。  
  
 `_Array`  
 會傳回基礎 Direct3D 緩衝處理介面 Direct3D accelerator_view 陣列。  
  
### <a name="return-value"></a>傳回值  
 對應至基礎陣列 Direct3D 緩衝區 IUnknown 介面指標。  
  
##  <a name="imax"></a>imax  
 判斷引數的最大數值  
  
```  
inline int imax(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
 `_Y`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最大的數值  
  
##  <a name="imin"></a>imin  
 判斷引數的最小數值  
  
```  
inline int imin(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
 `_Y`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最小數值  
  
##  <a name="is_timeout_disabled"></a>is_timeout_disabled  
 傳回布林值旗標，表示逾時已停用的指定 accelerator_view。 這會對應到 Direct3D 裝置建立的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標。  
  
```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  
  
### <a name="parameters"></a>參數  
 `_Accelerator_view`  
 要查詢設定停用的逾時為 accelerator_view。  
  
### <a name="return-value"></a>傳回值  
 表示逾時已停用的指定 accelerator_view 布林旗標。  
  
##  <a name="mad"></a>mad  
 會計算產品的第一個和第二個指定的引數，然後在其中新增第三個指定的引數。  
  
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
 `_X`  
 第一個指定的引數。  
  
 `_Y`  
 第二個指定的引數。  
  
 `_Z`  
 第三個指定的引數。  
  
### <a name="return-value"></a>傳回值  
 The result of `_X` * `_Y` + `_Z`.  
  
##  <a name="make_array"></a>make_array  
 建立從 Direct3D 緩衝區介面指標的陣列。  
  
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
 `value_type`  
 若要建立陣列的元素型別。  
  
 `_Rank`  
 若要建立陣列的陣序規範。  
  
 `_Extent`  
 描述陣列彙總的範圍。  
  
 `_Rv`  
 建立陣列所是 D3D 加速器檢視。  
  
 `_D3D_buffer`  
 若要建立從陣列 D3D 緩衝區的 IUnknown 介面指標。  
  
### <a name="return-value"></a>傳回值  
 建立使用所提供的 Direct3D 緩衝區的陣列。  
  
##  <a name="noise"></a>雜訊  
 產生使用 Perlin 雜訊演算法的隨機值  
  
```  
inline float noise(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 要從中產生 Perlin 雜訊的浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回介於-1 和 1 之間的範圍內的 Perlin 雜訊值  
  
##  <a name="radians"></a>弧度為單位  
 將 _X 從角度轉換為弧度  
  
```  
inline float radians(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回從度轉換成弧度 _X  
  
##  <a name="rcp"></a>rcp  
 使用快速的近似值，計算指定的引數的對等。  
  
```  
inline float rcp(float _X) restrict(amp);

 
inline double rcp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 要為其對等的計算值。  
  
### <a name="return-value"></a>傳回值  
 指定的引數的對等。  
  
##  <a name="reversebits"></a>reversebits  
 反轉 _X 的位元的順序  
  
```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 不帶正負號的整數值  
  
### <a name="return-value"></a>傳回值  
 反轉 _X 中的位元順序會傳回值  
  
##  <a name="saturate"></a>saturate  
 鉗制 _X 0 到 1 的範圍內  
  
```  
inline float saturate(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 _X 壓制 0 到 1 的範圍內  
  
##  <a name="sign"></a>符號  
 判斷指定的引數的符號。  
  
```  
inline int sign(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 引數的符號。  
  
##  <a name="smoothstep"></a>smoothstep  
 介於 0 和 1，傳回的平滑 Hermite 插補，_X 是否在範圍 [_Min，（_m）]。  
  
```  
inline float smoothstep(
    float _Min,  
    float _Max,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Min`  
 浮點值。  
  
 `_Max`  
 浮點值。  
  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 會傳回 0，如果 _X 小於 _Min;1 _X 是否大於 （_m）。否則，值介於 0 和 1 _X 是否在範圍 [_Min，（_m）]  
  
##  <a name="step"></a>步驟  
 比較兩個值，傳回 0 或 1 為基礎的值大於  
  
```  
inline float step(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Y`  
 浮點值。  
  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回 1，_X 是否大於或等於 _Y;否則為 0  
  
##  <a name="umax"></a>umax  
 判斷引數的最大數值  
  
```  
inline unsigned int umax(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
 `_Y`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最大的數值  
  
##  <a name="umin"></a>umin  
 判斷引數的最小數值  
  
```  
inline unsigned int umin(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
 `_Y`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 傳回引數的最小數值  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)

