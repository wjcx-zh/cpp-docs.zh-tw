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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff24f75c27ee60a085a8f87256a96b65a57e523c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency:: direct3d 命名空間函式 (AMP)
||||  
|-|-|-|  
|[abs](#abs)|[有縮短時間差](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|||
|[d3d_access_lock](#d3d_access_lock)|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|  
|[firstbithigh](#firstbithigh)|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|  
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|  
|[mad](#mad)|[make_array](#make_array)|[雜訊](#noise)|  
|[弧度為單位](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|  
|[saturate](#saturate)|[符號](#sign)|[smoothstep](#smoothstep)|  
|[步驟](#step)|[umax](#umax)|[umin](#umin)|  

## <a name="requirements"></a>需求
**標頭：** amp.h**命名空間：**並行
  
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
  
##  <a name="clamp"></a>有縮短時間差  
 計算壓制為範圍的第二個和第三個指定的引數所定義的第一個指定引數的值。  
  
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
 值壓制的`_X`。  
  
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
 所建立的新 accelerator_view 快速鍵。  
  
 `_D3D_device`  
 要 Direct3D 裝置介面的指標。  
  
 `_Disable_timeout`  
 布林值參數指定為新建立的 accelerator_view 是否應該停用逾時。 這對應至建立 Direct3D 裝置的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標，用來表示作業系統是否應該允許執行，而不重設裝置的 Windows 逾時每 2 秒以上的工作負載偵測和復原機制。 如果您需要執行耗時的工作上 accelerator_view，建議使用這個旗標。  
  
 `_Qmode`  
 [Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)用於新建 accelerator_view。 此參數有預設值是`queuing_mode_automatic`。  
  
## <a name="return-value"></a>傳回值  
 `accelerator_view`傳遞 Direct3D 裝置介面建立物件。  
  
## <a name="remarks"></a>備註  
 此函式會建立新`accelerator_view`從現有指標 Direct3D 裝置介面的物件。 如果函式呼叫成功，此參數的參考計數會遞增藉由`AddRef`呼叫的介面。 當它已不再需要 DirectX 的程式碼中，您可以安全地釋放物件。 如果方法呼叫失敗， [runtime_exception](runtime-exception-class.md)就會擲回。  
  
 `accelerator_view`物件，您使用此函式建立具備執行緒安全。 您必須同步處理的同時使用`accelerator_view`物件。 未同步處理的同時使用`accelerator_view`物件和原始 ID3D11Device 介面會導致未定義的行為。  
  
 C + + AMP 執行階段會提供詳細的錯誤資訊，偵錯模式中使用 D3D 偵錯的圖層，如果您使用`D3D11_CREATE_DEVICE_DEBUG`旗標。  
  
  
##  <a name="d3d_access_lock"></a>d3d_access_lock  
 取得 accelerator_view，為了安全地 D3D 上執行的作業與 accelerator_view 共用資源鎖定。 Accelerator_view 和與此 accelerator_view 內部相關聯的所有 c + + AMP 資源進行此鎖定執行作業時，會封鎖，而另一個執行緒保留 D3D 存取鎖定。 這個鎖定是非遞迴： 它是未定義從已經保留鎖定的執行緒呼叫此函式的行為。 它是未定義的行為 accelerator_view 或從保留 D3D 存取鎖定的執行緒 accelerator_view 相關聯的任何資料容器上執行作業。 另請參閱 scoped_d3d_access_lock，RAII 樣式類別的範圍為基礎的 D3D 存取鎖定。  
  
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
 如果已取得鎖定，則為 true 或 false，如果它目前由另一個執行緒。  
  
##  <a name="d3d_access_unlock"></a>d3d_access_unlock  
 釋放指定 accelerator_view 的 D3D 存取鎖定。 如果呼叫執行緒 accelerator_view 沒有已鎖定的結果便未定義。  
  
```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>參數  
 `_Av`  
 Accelerator_view，釋出鎖定的。  
  
##  <a name="firstbithigh"></a>firstbithigh  
 取得 _X，從最高序位位元和體制的最低順序位元中的第一組位元位置。  
  
```  
inline int firstbithigh(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 第一個設定位元位置  
  
##  <a name="firstbitlow"></a>firstbitlow  
 取得 _X，以最低順序位元為開頭，並使用小組的最高序位位元中的第一組位元位置。  
  
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
 陣列陣序。  
  
 `_Array`  
 在 Direct3D accelerator_view 基礎 Direct3D 緩衝區介面則傳回陣列。  
  
### <a name="return-value"></a>傳回值  
 對應至基礎陣列 Direct3D 緩衝區 IUnknown 介面指標。  
  
##  <a name="imax"></a>imax  
 判斷的最大的數值引數  
  
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
 傳回的最大的數值引數  
  
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
 傳回布林值旗標，指出是否停用的指定 accelerator_view 的逾時。 這會對應至建立 Direct3D 裝置的 D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT 旗標。  
  
```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  
  
### <a name="parameters"></a>參數  
 `_Accelerator_view`  
 Accelerator_view，停用設定的逾時是查詢。  
  
### <a name="return-value"></a>傳回值  
 表示逾時已停用的指定 accelerator_view 的布林值旗標。  
  
##  <a name="mad"></a>mad  
 會計算產品的第一個和第二個指定的引數，然後將第三個指定的引數。  
  
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
 結果`_X`  *  `_Y`  +  `_Z`。  
  
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
 要建立之陣列的項目類型。  
  
 `_Rank`  
 要建立之陣列的陣序規範。  
  
 `_Extent`  
 描述外觀陣列彙總的範圍。  
  
 `_Rv`  
 D3D 加速器檢視所建立的陣列。  
  
 `_D3D_buffer`  
 若要建立從陣列的 D3D 緩衝區的 IUnknown 介面指標。  
  
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
 傳回介於-1 和 1 之間的 Perlin 雜訊值的範圍內  
  
##  <a name="radians"></a>弧度為單位  
 將 _X 從角度轉換成弧度  
  
```  
inline float radians(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回從角度轉換成弧度 _X  
  
##  <a name="rcp"></a>rcp  
 使用快速的近似值，計算指定的引數的倒數。  
  
```  
inline float rcp(float _X) restrict(amp);

 
inline double rcp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 用來計算倒數值。  
  
### <a name="return-value"></a>傳回值  
 對等的指定的引數。  
  
##  <a name="reversebits"></a>reversebits  
 反轉 _X 的位元的順序  
  
```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 不帶正負號的整數值  
  
### <a name="return-value"></a>傳回值  
 傳回值的位元順序反轉 _X 中  
  
##  <a name="saturate"></a>saturate  
 強加 _X 0 到 1 的範圍內  
  
```  
inline float saturate(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 浮點值。  
  
### <a name="return-value"></a>傳回值  
 傳回在 0 到 1 的範圍內壓制 _X  
  
##  <a name="sign"></a>符號  
 判斷指定的引數的符號。  
  
```  
inline int sign(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_X`  
 整數值  
  
### <a name="return-value"></a>傳回值  
 的引數的符號。  
  
##  <a name="smoothstep"></a>smoothstep  
 介於 0 和 1，傳回的 smooth Hermite 插補，_X 是否在範圍 [_Min，（_m）]。  
  
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
 傳回 0，如果 _X 小於 _Min;如果 _X 大於 （_m）;，1否則，值介於 0 和 1 _X 是否在範圍 [_Min，（_m）]  
  
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
 傳回 1，_X 是否大於或等於平均數。否則為 0  
  
##  <a name="umax"></a>umax  
 判斷的最大的數值引數  
  
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
 傳回的最大的數值引數  
  
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
  
## <a name="see-also"></a>請參閱  
 [Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)
