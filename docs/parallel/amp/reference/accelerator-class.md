---
title: accelerator 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
dev_langs:
- C++
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b40177af3796a17d32e78e628c41ea694f69ed9f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="accelerator-class"></a>accelerator 類別
快速鍵會是最適合用於資料平行運算的硬體功能。 快速鍵可能連接到 （例如 GPU) PCIe 匯流排的裝置，或可能是主要的 CPU 上設定的延伸的指令。  
  
## <a name="syntax"></a>語法  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[accelerator 建構函式](#ctor)|初始化 `accelerator` 類別的新執行個體。|  
|[~ accelerator 解構函式](#ctor)|終結`accelerator`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[create_view](#create_view)|建立並傳回`accelerator_view`這個加速器上的物件。|  
|[get_all](#get_all)|傳回向量的`accelerator`物件，表示所有可用的快速鍵。|  
|[get_auto_selection_view](#get_auto_selection_view)|傳回自動選取`accelerator_view`。|  
|[get_dedicated_memory](#get_dedicated_memory)|傳回的專用的記憶體`accelerator`，以 kb 為單位。|  
|[get_default_cpu_access_type](#get_default_cpu_access_type)|傳回的預設[access_type](concurrency-namespace-enums-amp.md#access_type)這個加速器上建立的緩衝區。|  
|[get_default_view](#get_default_view)|傳回的預設`accelerator_view`與其相關聯物件`accelerator`。|  
|[get_description](#get_description)|傳回的簡短描述`accelerator`裝置。|  
|[get_device_path](#get_device_path)|傳回裝置路徑。|  
|[get_has_display](#get_has_display)|決定是否`accelerator`附加到顯示器。|  
|[get_is_debug](#get_is_debug)|決定是否`accelerator`已啟用 DEBUG 層以更詳盡的錯誤報告。|  
|[get_is_emulated](#get_is_emulated)|決定是否`accelerator`會模擬。|  
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|決定是否`accelerator`支援共用記憶體|  
|[get_supports_double_precision](#get_supports_double_precision)|決定是否`accelerator`附加到顯示器。|  
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|決定是否`accelerator`雙精確度運算的支援有限。|  
|[get_version](#get_version)|傳回的版本`accelerator`。|  
|[set_default](#set_default)|傳回的預設加速器的路徑。|  
|[set_default_cpu_access_type](#set_default_cpu_access_type)|設定預設 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)陣列和隱含的記憶體配置，這對`accelerator`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator!=](#operator_neq)|比較這個`accelerator`與另一個物件，然後傳回`false`如果它們是相同的; 否則會傳回`true`。|  
|[operator=](#operator_eq)|將指定的內容複製`accelerator`給這一個物件。|  
|[operator==](#operator_eq_eq)|比較這個`accelerator`與另一個物件，然後傳回`true`如果它們是相同的; 否則會傳回`false`。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[cpu_accelerator](#cpu_accelerator)|取得 cpu 的常數字串`accelerator`。|  
|[dedicated_memory](#dedicated_memory)|取得的專用的記憶體`accelerator`，以 kb 為單位。|  
|[default_accelerator](#default_accelerator)|取得預設的字串常數`accelerator`。|  
|[default_cpu_access_type](#default_cpu_access_type)|取得或設定預設 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)陣列和隱含的記憶體配置，這對`accelerator`。|  
|[default_view](#default_view)|取得預設`accelerator_view`與其相關聯物件`accelerator`。|  
|[description](#description)|取得的簡短描述`accelerator`裝置。|  
|[device_path](#device_path)|取得裝置的路徑。|  
|[direct3d_ref](#direct3d_ref)|取得字串常數的 Direct3D 參考`accelerator`。|  
|[direct3d_warp](#direct3d_warp)|取得字串常數的`accelerator`物件可讓您使用 Streaming SIMD 擴充功能 (SSE) 中的多核心 Cpu 上執行 c + + AMP 程式碼。|  
|[has_display](#has_display)|取得布林值，指出是否`accelerator`附加到顯示器。|  
|[is_debug](#is_debug)|指出是否`accelerator`已啟用 DEBUG 層以更詳盡的錯誤報告。|  
|[is_emulated](#is_emulated)|指出是否`accelerator`會模擬。|  
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|指出是否`accelerator`支援共用記憶體。|  
|[supports_double_precision](#supports_double_precision)|指出快速鍵是否支援雙精確度運算。|  
|[supports_limited_double_precision](#supports_limited_double_precision)|指出是否快速鍵支援有限的雙精確度運算。|  
|[version](#version)|取得版本`accelerator`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `accelerator`  
  
## <a name="remarks"></a>備註  
 快速鍵會是最適合用於資料平行運算的硬體功能。 加速器通常不連續的 GPU，但它也可以是虛擬的主應用程式端實體，例如 WARP （會透過 SSE 指令加速 CPU 端裝置） 或 CPU 本身的 DirectX REF 裝置。  
  
 您可以建構`accelerator`物件列舉可用的裝置，或藉由取得預設的裝置、 參考裝置或 WARP 裝置。  
  
## <a name="requirements"></a>需求  
 **標頭：** amprt.h  
  
 **命名空間：** 並行  
  
##  <a name="dtor"></a> </a> ~ accelerator 

 終結`accelerator`物件。  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="ctor"></a> 快速鍵 

 初始化的新執行個體[accelerator 類別](accelerator-class.md)。  
  
```  
accelerator();

 
explicit accelerator(const std::wstring& _Device_path);

 
accelerator(const accelerator& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Device_path`  
 實體裝置的路徑。  
  
 `_Other`  
 若要複製快速鍵。  
  
##  <a name="cpu_accelerator"></a> cpu_accelerator 

 取得 CPU 快速鍵的字串常數。  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="create_view"></a> create_view 

 建立並傳回`accelerator_view`此快速鍵，使用指定的佇列模式上的物件。 未指定的佇列模式時，新`accelerator_view`使用[queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode)佇列模式。  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>參數  
 `qmode`  
 佇列的模式。  
  
### <a name="return-value"></a>傳回值  
 新`accelerator_view`此快速鍵，使用指定的佇列模式上的物件。  
  
##  <a name="dedicated_memory"></a> dedicated_memory 

 取得的專用的記憶體`accelerator`，以 kb 為單位。  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="default_accelerator"></a> default_accelerator 

 取得預設的字串常數`accelerator`。  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="default_cpu_access_type"></a> default_cpu_access_type 

 預設 cpu [access_type](concurrency-namespace-enums-amp.md#access_type)陣列和隱含的記憶體配置，這對`accelerator`。  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="default_view"></a> default_view 

 取得相關聯的預設加速器檢視`accelerator`。  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="description"></a> 描述 

 取得的簡短描述`accelerator`裝置。  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="device_path"></a> device_path 

 取得快速鍵的路徑。 路徑是在系統上唯一的。  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="direct3d_ref"></a> direct3d_ref 

 取得 Direct3D 參考快速鍵的字串常數。  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="direct3d_warp"></a> direct3d_warp 

 取得字串常數的`accelerator`物件可讓您在使用 Streaming SIMD 擴充功能 (SSE) 中的多核心 Cpu 上執行您的 c + + AMP 程式碼。  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="get_all"></a> get_all 

 傳回向量的`accelerator`物件，表示所有可用的快速鍵。  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>傳回值  
 向量的可用的快速鍵  
  
##  <a name="get_auto_selection_view"></a> get_auto_selection_view 

 傳回自動選取項目 accelerator_view，當指定為執行 parallel_for_each 核心執行階段會自動選取的目標 accelerator_view parallel_for_each 目標結果。 基於其他目的，這個方法所傳回的 accelerator_view 等同於預設 accelerator_view 的預設加速器  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>傳回值  
 自動選取項目 accelerator_view 中。  
  
##  <a name="get_dedicated_memory"></a> get_dedicated_memory 

 傳回的專用的記憶體`accelerator`，以 kb 為單位。  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 專用的記憶體`accelerator`，以 kb 為單位。  
  
##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type 

 取得預設 cpu access_type 這個加速器上建立的緩衝區  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 在此加速器上建立的緩衝區預設 cpu access_type。  
  
##  <a name="get_default_view"></a> get_default_view 

 傳回的預設`accelerator_view`與其相關聯物件`accelerator`。  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 預設值`accelerator_view`與其相關聯物件`accelerator`。  
  
##  <a name="get_description"></a> get_description 

 傳回的簡短描述`accelerator`裝置。  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 簡短描述`accelerator`裝置。  
  
##  <a name="get_device_path"></a> get_device_path 

 傳回快速鍵的路徑。 路徑是在系統上唯一的。  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 全系統唯一的裝置執行個體路徑。  
  
##  <a name="get_has_display"></a> get_has_display 

 傳回布林值，指出是否`accelerator`可以輸出到顯示器。  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果`accelerator`可以輸出到顯示器; 否則`false`。  
  
##  <a name="get_is_debug"></a> get_is_debug 

 決定是否`accelerator`已啟用 DEBUG 層以更詳盡的錯誤報告。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果`accelerator`已啟用 DEBUG 層以更詳盡的錯誤報告。 否則為 `false`。  
  
##  <a name="get_is_emulated"></a> get_is_emulated 

 決定是否`accelerator`會模擬。  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果`accelerator`會模擬。 否則為 `false`。  
  
##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory 

 傳回布林值，指出是否快速鍵支援快速鍵和 CPU 都能存取的記憶體。  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果快速鍵支援 CPU 共用記憶體。否則， `false`。  
  
##  <a name="get_supports_double_precision"></a> get_supports_double_precision 

 傳回布林值，指出是否快速鍵支援雙精確度的數學運算，包括 fused 乘新增 (FMA)、 除法、 對等，以及轉換之間`int`和`double`。  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果快速鍵支援雙精確度數學;否則， `false`。  
  
##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision 

 傳回布林值，指出是否快速鍵支援有限的雙精確度的數學運算。 必須有快速鍵只有有限的支援，然後 fused 多次新增 (FMA)，除法、 對等，以及轉換之間`int`和`double`不支援。  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果快速鍵的雙精確度數學; 對於支援有限，否則， `false`。  
  
##  <a name="get_version"></a> get_version 

 傳回的版本`accelerator`。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 版本`accelerator`。  
  
##  <a name="has_display"></a> has_display 

 取得布林值，指出是否`accelerator`可以輸出到顯示器。  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="is_debug"></a> is_debug 

 取得布林值，指出是否`accelerator`已啟用 DEBUG 層以更詳盡的錯誤報告。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="is_emulated"></a> is_emulated 

 取得布林值，指出是否`accelerator`會模擬。  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="operator_neq"></a> 運算子 ！ = 

 比較這個`accelerator`與另一個物件，然後傳回`false`如果它們是相同的; 否則會傳回`true`。  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `accelerator`這一個與相比較的物件。  
  
### <a name="return-value"></a>傳回值  
 `false` 如果兩個`accelerator`物件是否相同，否則`true`。  
  
##  <a name="operator_eq"></a> 運算子 = 

 將指定的內容複製`accelerator`給這一個物件。  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `accelerator`從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`accelerator`物件。  
  
##  <a name="operator_eq_eq"></a> 運算子 = = 

 比較這個`accelerator`與另一個物件，然後傳回`true`如果它們是相同的; 否則會傳回`false`。  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `accelerator`這一個與相比較的物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果其他`accelerator`物件是否與此相同`accelerator`物件; 否則`false`。  
  
##  <a name="set_default"></a> set_default 

 設定要用於隱含使用預設加速器的任何作業的預設加速器。 如果執行階段選取的預設加速器不已經使用隱含使用預設加速器的作業中，這個方法才會成功  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>參數  
 `_Path`  
 要對應的路徑。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果呼叫成功設定的預設加速器。 否則為 `false`。  
  
##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type 

 設定預設 cpu access_type，一部分 array_views 上此快速鍵存取建立此快速鍵或隱含的記憶體配置的陣列。 如果 accelerator default_cpu_access_type 尚未由先前呼叫這個方法的覆寫，而且此快速鍵的執行階段選取 default_cpu_access_type 具有尚未使用或來配置陣列，這個方法才會成功備份此加速器上存取 array_view 是隱含的記憶體配置。  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>參數  
 `_Default_cpu_access_type`  
 要用於陣列/array_view 記憶體配置，在此加速器上預設 cpu access_type。  
  
### <a name="return-value"></a>傳回值  
 布林值，指出 accelerator 預設 cpu access_type 是否已成功設定。  
  
##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory 

 取得布林值，指出是否`accelerator`支援共用記憶體。  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="supports_double_precision"></a> supports_double_precision 

 取得布林值，指出快速鍵是否支援雙精確度運算。  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision 

 取得布林值，指出是否快速鍵支援有限的雙精確度的數學運算。 必須有快速鍵只有有限的支援，然後 fused 多次新增 (FMA)，除法、 對等，以及轉換之間`int`和`double`不支援。  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="version"></a> 版本 

 取得版本`accelerator`。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="dtor"></a> </a> ~ accelerator_view 

 終結[accelerator_view](accelerator-view-class.md)物件。  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="accelerator"></a> 快速鍵 

 取得`accelerator`物件[accelerator_view](accelerator-view-class.md)物件。  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="ctor"></a> accelerator_view 

 初始化的新執行個體[accelerator_view](accelerator-view-class.md)藉由複製現有的類別`accelerator_view`物件。  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `accelerator_view`来複製物件。  
  
##  <a name="create_marker"></a> create_marker 

 傳回追蹤的所有命令提交到目前為止此完成未來`accelerator_view`物件。  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>傳回值  
 未來若要追蹤的所有命令提交到目前為止此完成`accelerator_view`物件。  
  
##  <a name="flush"></a> 排清 

 送出所有暫止命令排入佇列[accelerator_view](accelerator-view-class.md)執行對應的物件。  
  
```  
void flush();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `void`。  
  
##  <a name="get_accelerator"></a> get_accelerator 

 傳回`accelerator`物件[accelerator_view](accelerator-view-class.md)物件。  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `accelerator`物件`accelerator_view`物件。  
  
##  <a name="get_is_auto_selection"></a> get_is_auto_selection 

 傳回布林值，指出是否執行階段將會自動選取適當的加速器 accelerator_view 傳遞至[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)。  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果執行階段將會自動選取適當的快速鍵。否則， `false`。  
  
##  <a name="get_is_debug"></a> get_is_debug 

 傳回布林值，指出是否[accelerator_view](accelerator-view-class.md)物件已啟用 DEBUG 層以更詳盡的錯誤報告。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 布林值，指出是否`accelerator_view`物件已啟用 DEBUG 層以更詳盡的錯誤報告。  
  
##  <a name="get_queuing_mode"></a> get_queuing_mode 

 傳回的佇列模式[accelerator_view](accelerator-view-class.md)物件。  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 佇列模式`accelerator_view`物件。  
  
##  <a name="get_version"></a> get_version 

 傳回的版本[accelerator_view](accelerator-view-class.md)。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 版本`accelerator_view`。  
  
##  <a name="is_auto_selection"></a> is_auto_selection 

 取得布林值，指出是否執行階段將會自動選取適當的加速器 accelerator_view 傳遞至[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)。  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="is_debug"></a> is_debug 

 取得布林值，指出是否[accelerator_view](accelerator-view-class.md)物件已啟用 DEBUG 層以更詳盡的錯誤報告。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="operator_neq"></a> 運算子 ！ = 

 比較這個[accelerator_view](accelerator-view-class.md)與另一個物件，然後傳回`false`如果它們是相同的; 否則會傳回`true`。  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `accelerator_view`這一個與相比較的物件。  
  
### <a name="return-value"></a>傳回值  
 如果這兩個物件相同則為 `false`，否則為 `true`。  
  
##  <a name="operator_eq"></a> 運算子 = 

 將指定的內容複製[accelerator_view](accelerator-view-class.md)成這一個物件。  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `accelerator_view`從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 已修改的參考`accelerator_view`物件。  
  
##  <a name="operator_eq_eq"></a> 運算子 = = 

 比較這個[accelerator_view](accelerator-view-class.md)與另一個物件，然後傳回`true`如果它們是相同的; 否則會傳回`false`。  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `accelerator_view`這一個與相比較的物件。  
  
### <a name="return-value"></a>傳回值  
 如果這兩個物件相同則為 `true`，否則為 `false`。  
  
##  <a name="queuing_mode"></a> queuing_mode 

 取得佇列模式[accelerator_view](accelerator-view-class.md)物件。  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="version"></a> 版本 

 取得版本[accelerator_view](accelerator-view-class.md)。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="wait"></a> 等候 

 等候所有命令送出至[accelerator_view](accelerator-view-class.md)完成的物件。  
  
```  
void wait();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `void`。  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
