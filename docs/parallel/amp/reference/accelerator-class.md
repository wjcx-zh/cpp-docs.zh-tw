---
title: "accelerator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::accelerator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator 類別"
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# accelerator 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

加速器是最佳化的資料平行運算的硬體功能。 加速器可能連接到 （例如 GPU) PCIe 匯流排的裝置，或可能是主要的 CPU 上設定的延伸的指令。  
  
## <a name="syntax"></a>語法  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[accelerator:: accelerator 建構函式](#accelerator__accelerator_constructor)|初始化 `accelerator` 類別的新執行個體。|  
|[accelerator:: ~ accelerator 解構函式](#accelerator___dtoraccelerator_destructor)|終結 `accelerator` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[accelerator:: create_view 方法](#accelerator__create_view_method)|建立並傳回 `accelerator_view` 這個加速器上的物件。|  
|[accelerator:: get_all 方法](#accelerator__get_all_method)|傳回向量的位元 `accelerator` 物件，代表所有可用的快速鍵。|  
|[accelerator:: get_auto_selection_view 方法](#accelerator__get_auto_selection_view_method)|傳回自動選取項目 `accelerator_view`。|  
|[accelerator:: get_dedicated_memory 方法](#accelerator__get_dedicated_memory_method)|傳回的專用的記憶體 `accelerator`, ，以 kb 為單位。|  
|[accelerator:: get_default_cpu_access_type 方法](#accelerator__get_default_cpu_access_type_method)|傳回的預設 [access_type](../Topic/concurrency%20namespace%20enums.md#access_type) 這個加速器上建立的緩衝區。|  
|[accelerator:: get_default_view 方法](#accelerator__get_default_view_method)|傳回的預設 `accelerator_view` 相關聯的物件 `accelerator`。|  
|[accelerator:: get_description 方法](#accelerator__get_description_method)|傳回的簡短描述 `accelerator` 裝置。|  
|[accelerator:: get_device_path 方法](#accelerator__get_device_path_method)|傳回裝置的路徑。|  
|[accelerator:: get_has_display 方法](#accelerator__get_has_display_method)|決定是否 `accelerator` 附加至顯示。|  
|[accelerator:: get_is_debug 方法](#accelerator__get_is_debug_method)|決定是否 `accelerator` 已啟用大量錯誤報告的偵錯層。|  
|[accelerator:: get_is_emulated 方法](#accelerator__get_is_emulated_method)|決定是否 `accelerator` 會模擬。|  
|[accelerator:: get_supports_cpu_shared_memory 方法](#accelerator__get_supports_cpu_shared_memory_method)|決定是否 `accelerator` 支援共用記憶體|  
|[accelerator:: get_supports_double_precision 方法](#accelerator__get_supports_double_precision_method)|決定是否 `accelerator` 附加至顯示。|  
|[accelerator:: get_supports_limited_double_precision 方法](#accelerator__get_supports_limited_double_precision_method)|決定是否 `accelerator` 雙精度數學的支援有限。|  
|[accelerator:: get_version 方法](#accelerator__get_version_method)|傳回的版本 `accelerator`。|  
|[accelerator:: set_default 方法](#accelerator__set_default_method)|傳回在預設加速器的路徑。|  
|[accelerator:: set_default_cpu_access_type 方法](#accelerator__set_default_cpu_access_type_method)|設定預設 CPU [access_type](../Topic/concurrency%20namespace%20enums.md#access_type) 陣列和隱含的記憶體配置，這對 `accelerator`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[accelerator:: operator ！ = 運算子](#accelerator__operator_neq_operator)|比較這個 `accelerator` 與另一個物件，然後傳回 `false` 如果兩個名稱相同; 否則會傳回 `true`。|  
|[accelerator:: operator = 運算子](#accelerator__operator_eq_operator)|將指定的內容複製 `accelerator` 這個物件。|  
|[accelerator:: operator = = 運算子](#accelerator__operator_eq_eq_operator)|比較這個 `accelerator` 與另一個物件，然後傳回 `true` 如果兩個名稱相同; 否則會傳回 `false`。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[accelerator:: cpu_accelerator 資料成員](#accelerator__cpu_accelerator_data_member)|取得 cpu 的常數字串 `accelerator`。|  
|[accelerator:: dedicated_memory 資料成員](#accelerator__dedicated_memory_data_member)|取得的專用的記憶體 `accelerator`, ，以 kb 為單位。|  
|[accelerator:: default_accelerator 資料成員](#accelerator__default_accelerator_data_member)|取得預設的字串常數 `accelerator`。|  
|[accelerator:: default_cpu_access_type 資料成員](#accelerator__default_cpu_access_type_data_member)|取得或設定預設 CPU [access_type](../Topic/concurrency%20namespace%20enums.md#access_type) 陣列和隱含的記憶體配置，這對 `accelerator`。|  
|[accelerator:: default_view 資料成員](#accelerator__default_view_data_member)|取得預設 `accelerator_view` 相關聯的物件 `accelerator`。|  
|[accelerator:: description 資料成員](#accelerator__description_data_member)|取得的簡短描述 `accelerator` 裝置。|  
|[accelerator:: device_path 資料成員](#accelerator__device_path_data_member)|取得裝置的路徑。|  
|[accelerator:: direct3d_ref 資料成員](#accelerator__direct3d_ref_data_member)|取得字串常數的 Direct3D 參考 `accelerator`。|  
|[accelerator:: direct3d_warp 資料成員](#accelerator__direct3d_warp_data_member)|取得字串常數的 [加速器](../../../parallel/amp/reference/accelerator-class.md) 物件，您可以使用使用 Streaming SIMD Extensions (SSE) 的多核心 Cpu 上執行 c + + AMP 程式碼。|  
|[accelerator:: has_display 資料成員](#accelerator__has_display_data_member)|取得布林值，指出是否 `accelerator` 附加至顯示。|  
|[accelerator:: is_debug 資料成員](#accelerator__is_debug_data_member)|指出是否 `accelerator` 已啟用大量錯誤報告的偵錯層。|  
|[accelerator:: is_emulated 資料成員](#accelerator__is_emulated_data_member)|指出是否 `accelerator` 會模擬。|  
|[accelerator:: supports_cpu_shared_memory 資料成員](#accelerator__supports_cpu_shared_memory_data_member)|指出是否 `accelerator` 支援共用記憶體。|  
|[accelerator:: supports_double_precision 資料成員](#accelerator__supports_double_precision_data_member)|指出對應是否支援雙精確度運算。|  
|[accelerator:: supports_limited_double_precision 資料成員](#accelerator__supports_limited_double_precision_data_member)|指出是否加速器支援有限的雙精確度運算。|  
|[accelerator:: version 資料成員](#accelerator__version_data_member)|取得版本 `accelerator`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `accelerator`  
  
## <a name="remarks"></a>備註  
 加速器是最佳化的資料平行運算的硬體功能。 加速器通常不連續的 GPU，但它也可以是虛擬的主應用程式端實體，例如彎曲 （加速透過 SSE 指令的 CPU 端裝置） 或 CPU 本身的 DirectX REF 裝置。  
  
 您可以建構 `accelerator` 列舉可用的裝置，或藉由取得預設的裝置、 參考裝置或彎曲裝置物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** amprt.h  
  
 **命名空間：** 並行  
  
##  <a name="a-nameacceleratordtoracceleratordestructora-acceleratoraccelerator-destructor"></a><a name="accelerator___dtoraccelerator_destructor"></a>  accelerator:: ~ accelerator 解構函式  
 終結 [加速器](../../../parallel/amp/reference/accelerator-class.md) 物件。  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-nameacceleratoracceleratorconstructora-acceleratoraccelerator-constructor"></a><a name="accelerator__accelerator_constructor"></a>  accelerator:: accelerator 建構函式  
 初始化的新執行個體 [加速器類別](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
accelerator();

 
explicit accelerator(const std::wstring& _Device_path);

 
accelerator(const accelerator& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Device_path`  
 實體裝置的路徑。  
  
 `_Other`  
 若要複製加速器。  
  
##  <a name="a-nameacceleratorcpuacceleratordatamembera-acceleratorcpuaccelerator-data-member"></a><a name="accelerator__cpu_accelerator_data_member"></a>  accelerator:: cpu_accelerator 資料成員  
 取得 CPU 加速器常數字串。  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="a-nameacceleratorcreateviewmethoda-acceleratorcreateview-method"></a><a name="accelerator__create_view_method"></a>  accelerator:: create_view 方法  
 建立並傳回 `accelerator_view` 這個加速器，使用指定的佇列模式上的物件。 未指定的佇列模式時，新 `accelerator_view` 使用 [queuing_mode::immediate](../Topic/concurrency%20namespace%20enums.md#queuing_mode) 佇列模式。  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>參數  
 `qmode`  
 佇列的模式。  
  
### <a name="return-value"></a>傳回值  
 新 `accelerator_view` 這個加速器，使用指定的佇列模式上的物件。  
  
##  <a name="a-nameacceleratordedicatedmemorydatamembera-acceleratordedicatedmemory-data-member"></a><a name="accelerator__dedicated_memory_data_member"></a>  accelerator:: dedicated_memory 資料成員  
 取得的專用的記憶體 [加速器](../../../parallel/amp/reference/accelerator-class.md), ，以 kb 為單位。  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="a-nameacceleratordefaultacceleratordatamembera-acceleratordefaultaccelerator-data-member"></a><a name="accelerator__default_accelerator_data_member"></a>  accelerator:: default_accelerator 資料成員  
 取得預設的字串常數 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="a-nameacceleratordefaultcpuaccesstypedatamembera-acceleratordefaultcpuaccesstype-data-member"></a><a name="accelerator__default_cpu_access_type_data_member"></a>  accelerator:: default_cpu_access_type 資料成員  
 預設 cpu [access_type](../Topic/concurrency%20namespace%20enums.md#access_type) 陣列和隱含的記憶體配置，這對 `accelerator`。  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="a-nameacceleratordefaultviewdatamembera-acceleratordefaultview-data-member"></a><a name="accelerator__default_view_data_member"></a>  accelerator:: default_view 資料成員  
 取得相關聯的預設加速器檢視 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="a-nameacceleratordescriptiondatamembera-acceleratordescription-data-member"></a><a name="accelerator__description_data_member"></a>  accelerator:: description 資料成員  
 取得的簡短描述 [加速器](../../../parallel/amp/reference/accelerator-class.md) 裝置。  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="a-nameacceleratordevicepathdatamembera-acceleratordevicepath-data-member"></a><a name="accelerator__device_path_data_member"></a>  accelerator:: device_path 資料成員  
 取得此加速器的路徑。 此路徑是唯一的系統上。  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="a-nameacceleratordirect3drefdatamembera-acceleratordirect3dref-data-member"></a><a name="accelerator__direct3d_ref_data_member"></a>  accelerator:: direct3d_ref 資料成員  
 取得 Direct3D 參考快速鍵的字串常數。  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="a-nameacceleratordirect3dwarpdatamembera-acceleratordirect3dwarp-data-member"></a><a name="accelerator__direct3d_warp_data_member"></a>  accelerator:: direct3d_warp 資料成員  
 取得字串常數的 [加速器](../../../parallel/amp/reference/accelerator-class.md) 物件，您可以用在多核心 Cpu 使用 Streaming SIMD Extensions (SSE) 上執行您的 c + + AMP 程式碼。  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="a-nameacceleratorgetallmethoda-acceleratorgetall-method"></a><a name="accelerator__get_all_method"></a>  accelerator:: get_all 方法  
 傳回向量的位元 `accelerator` 物件，代表所有可用的快速鍵。  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>傳回值  
 向量的可用加速器  
  
##  <a name="a-nameacceleratorgetautoselectionviewmethoda-acceleratorgetautoselectionview-method"></a><a name="accelerator__get_auto_selection_view_method"></a>  accelerator:: get_auto_selection_view 方法  
 傳回自動選取 accelerator_view 中，當指定為執行 parallel_for_each 核心執行階段會自動選取目標 accelerator_view parallel_for_each 目標結果。 基於其他目的，這個方法所傳回的 accelerator_view 等同於在預設加速器的預設 accelerator_view  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>傳回值  
 自動選取 accelerator_view 中。  
  
##  <a name="a-nameacceleratorgetdedicatedmemorymethoda-acceleratorgetdedicatedmemory-method"></a><a name="accelerator__get_dedicated_memory_method"></a>  accelerator:: get_dedicated_memory 方法  
 傳回的專用的記憶體 [加速器](../../../parallel/amp/reference/accelerator-class.md), ，以 kb 為單位。  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 專用的記憶體 `accelerator`, ，以 kb 為單位。  
  
##  <a name="a-nameacceleratorgetdefaultcpuaccesstypemethoda-acceleratorgetdefaultcpuaccesstype-method"></a><a name="accelerator__get_default_cpu_access_type_method"></a>  accelerator:: get_default_cpu_access_type 方法  
 取得預設 cpu access_type 這個加速器上建立的緩衝區  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 在這個加速器上建立的緩衝區預設 cpu access_type。  
  
##  <a name="a-nameacceleratorgetdefaultviewmethoda-acceleratorgetdefaultview-method"></a><a name="accelerator__get_default_view_method"></a>  accelerator:: get_default_view 方法  
 傳回的預設 `accelerator_view` 相關聯的物件 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 預設 `accelerator_view` 相關聯的物件 `accelerator`。  
  
##  <a name="a-nameacceleratorgetdescriptionmethoda-acceleratorgetdescription-method"></a><a name="accelerator__get_description_method"></a>  accelerator:: get_description 方法  
 傳回的簡短描述 [加速器](../../../parallel/amp/reference/accelerator-class.md) 裝置。  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 簡短描述 `accelerator` 裝置。  
  
##  <a name="a-nameacceleratorgetdevicepathmethoda-acceleratorgetdevicepath-method"></a><a name="accelerator__get_device_path_method"></a>  accelerator:: get_device_path 方法  
 傳回此加速器的路徑。 此路徑是唯一的系統上。  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 整個系統的唯一裝置執行個體路徑。  
  
##  <a name="a-nameacceleratorgethasdisplaymethoda-acceleratorgethasdisplay-method"></a><a name="accelerator__get_has_display_method"></a>  accelerator:: get_has_display 方法  
 傳回布林值，指出是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 可以顯示輸出。  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果 `accelerator` 可以輸出顯示; 否則 `false`。  
  
##  <a name="a-nameacceleratorgetisdebugmethoda-acceleratorgetisdebug-method"></a><a name="accelerator__get_is_debug_method"></a>  accelerator:: get_is_debug 方法  
 決定是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 已啟用大量錯誤報告的偵錯層。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果 `accelerator` 已啟用大量錯誤報告的偵錯層。 否則為 `false`。  
  
##  <a name="a-nameacceleratorgetisemulatedmethoda-acceleratorgetisemulated-method"></a><a name="accelerator__get_is_emulated_method"></a>  accelerator:: get_is_emulated 方法  
 決定是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 會模擬。  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果 `accelerator` 會模擬。 否則為 `false`。  
  
##  <a name="a-nameacceleratorgetsupportscpusharedmemorymethoda-acceleratorgetsupportscpusharedmemory-method"></a><a name="accelerator__get_supports_cpu_shared_memory_method"></a>  accelerator:: get_supports_cpu_shared_memory 方法  
 傳回布林值，指出是否加速器支援快速鍵和 CPU 都能存取的記憶體。  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果加速器支援 CPU 共用記憶體。否則， `false`。  
  
##  <a name="a-nameacceleratorgetsupportsdoubleprecisionmethoda-acceleratorgetsupportsdoubleprecision-method"></a><a name="accelerator__get_supports_double_precision_method"></a>  accelerator:: get_supports_double_precision 方法  
 傳回布林值，指出是否加速器支援雙精確度運算，包括融合乘加入 (FMA)、 除法、 對等，以及轉換之間 `int` 和 `double`。  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果此加速器支援雙精確度運算;否則， `false`。  
  
##  <a name="a-nameacceleratorgetsupportslimiteddoubleprecisionmethoda-acceleratorgetsupportslimiteddoubleprecision-method"></a><a name="accelerator__get_supports_limited_double_precision_method"></a>  accelerator:: get_supports_limited_double_precision 方法  
 傳回布林值，指出是否加速器支援有限的雙精確度運算。 加速器有只有有限的支援，然後乘以融合加入 (FMA)、 除法、 對等，以及轉換之間 `int` 和 `double` 不支援。  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 若對應已限制的雙精確度運算; 支援否則， `false`。  
  
##  <a name="a-nameacceleratorgetversionmethoda-acceleratorgetversion-method"></a><a name="accelerator__get_version_method"></a>  accelerator:: get_version 方法  
 傳回的版本 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 版本 `accelerator`。  
  
##  <a name="a-nameacceleratorhasdisplaydatamembera-acceleratorhasdisplay-data-member"></a><a name="accelerator__has_display_data_member"></a>  accelerator:: has_display 資料成員  
 取得布林值，指出是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 可以顯示輸出。  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="a-nameacceleratorisdebugdatamembera-acceleratorisdebug-data-member"></a><a name="accelerator__is_debug_data_member"></a>  accelerator:: is_debug 資料成員  
 取得布林值，指出是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 已啟用大量錯誤報告的偵錯層。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameacceleratorisemulateddatamembera-acceleratorisemulated-data-member"></a><a name="accelerator__is_emulated_data_member"></a>  accelerator:: is_emulated 資料成員  
 取得布林值，指出是否 [加速器](../../../parallel/amp/reference/accelerator-class.md) 會模擬。  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="a-nameacceleratoroperatorneqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_neq_operator"></a>  accelerator:: operator ！ = 運算子  
 比較這個 `accelerator` 與另一個物件，然後傳回 `false` 如果兩個名稱相同; 否則會傳回 `true`。  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
  `accelerator` 要與這個比較的物件。  
  
### <a name="return-value"></a>傳回值  
 `false` 如果這兩個 `accelerator` 物件是否相同，否則 `true`。  
  
##  <a name="a-nameacceleratoroperatoreqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_eq_operator"></a>  accelerator:: operator = 運算子  
 將指定的內容複製 [加速器](../../../parallel/amp/reference/accelerator-class.md) 這個物件。  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
  `accelerator` 從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 參考 `accelerator` 物件。  
  
##  <a name="a-nameacceleratoroperatoreqeqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_eq_eq_operator"></a>  accelerator:: operator = = 運算子  
 比較這個 [加速器](../../../parallel/amp/reference/accelerator-class.md) 與另一個物件，然後傳回 `true` 如果兩個名稱相同; 否則會傳回 `false`。  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
  `accelerator` 要與這個比較的物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果其他 `accelerator` 物件是與此相同 `accelerator` 物件; 否則 `false`。  
  
##  <a name="a-nameacceleratorsetdefaultmethoda-acceleratorsetdefault-method"></a><a name="accelerator__set_default_method"></a>  accelerator:: set_default 方法  
 設定要用於任何作業，會隱含地使用的預設加速器的預設加速器。 這個方法才會成功執行階段選取的預設加速器不已經使用中的作業，會隱含地使用的預設加速器  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>參數  
 `_Path`  
 要對應的路徑。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果呼叫成功設定的預設加速器。 否則為 `false`。  
  
##  <a name="a-nameacceleratorsetdefaultcpuaccesstypemethoda-acceleratorsetdefaultcpuaccesstype-method"></a><a name="accelerator__set_default_cpu_access_type_method"></a>  accelerator:: set_default_cpu_access_type 方法  
 設定預設 cpu access_type，存取此這個加速器的一部分 array_views 建立這個加速器或隱含的記憶體配置的陣列。 如果加速器 default_cpu_access_type 尚未由先前呼叫這個方法的覆寫，而且此快速鍵的執行階段選取 default_cpu_access_type 但尚未使用配置的陣列或備份這個加速器上存取 array_view 是隱含的記憶體配置，這個方法才會成功。  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>參數  
 `_Default_cpu_access_type`  
 要用於此加速器上陣列/array_view 記憶體配置預設 cpu access_type。  
  
### <a name="return-value"></a>傳回值  
 布林值，指出已成功地設加速器預設 cpu access_type。  
  
##  <a name="a-nameacceleratorsupportscpusharedmemorydatamembera-acceleratorsupportscpusharedmemory-data-member"></a><a name="accelerator__supports_cpu_shared_memory_data_member"></a>  accelerator:: supports_cpu_shared_memory 資料成員  
 取得布林值，指出是否 `accelerator` 支援共用記憶體。  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="a-nameacceleratorsupportsdoubleprecisiondatamembera-acceleratorsupportsdoubleprecision-data-member"></a><a name="accelerator__supports_double_precision_data_member"></a>  accelerator:: supports_double_precision 資料成員  
 取得布林值，指出加速器是否支援雙精度數學運算。  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="a-nameacceleratorsupportslimiteddoubleprecisiondatamembera-acceleratorsupportslimiteddoubleprecision-data-member"></a><a name="accelerator__supports_limited_double_precision_data_member"></a>  accelerator:: supports_limited_double_precision 資料成員  
 取得布林值，指出是否加速器支援有限的雙精確度運算。 加速器有只有有限的支援，然後乘以融合加入 (FMA)、 除法、 對等，以及轉換之間 `int` 和 `double` 不支援。  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="a-nameacceleratorversiondatamembera-acceleratorversion-data-member"></a><a name="accelerator__version_data_member"></a>  accelerator:: version 資料成員  
 取得版本 [加速器](../../../parallel/amp/reference/accelerator-class.md)。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="a-nameacceleratorviewdtoracceleratorviewdestructora-acceleratorviewacceleratorview-destructor"></a><a name="accelerator_view___dtoraccelerator_view_destructor"></a>  accelerator_view:: ~ accelerator_view 解構函式  
 終結 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件。  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-nameacceleratorviewacceleratordatamembera-acceleratorviewaccelerator-data-member"></a><a name="accelerator_view__accelerator_data_member"></a>  accelerator_view:: accelerator 資料成員  
 取得 [加速器](../../../parallel/amp/reference/accelerator-class.md) 物件 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件。  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="a-nameacceleratorviewacceleratorviewconstructora-acceleratorviewacceleratorview-constructor"></a><a name="accelerator_view__accelerator_view_constructor"></a>  accelerator_view:: accelerator_view 建構函式  
 初始化的新執行個體 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 藉由複製現有的類別 `accelerator_view` 物件。  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
  `accelerator_view` 要複製物件。  
  
##  <a name="a-nameacceleratorviewcreatemarkermethoda-acceleratorviewcreatemarker-method"></a><a name="accelerator_view__create_marker_method"></a>  accelerator_view:: create_marker 方法  
 傳回追蹤的完成狀態的所有命令送出到目前為止此 future `accelerator_view` 物件。  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>傳回值  
 追蹤的完成狀態的所有命令送出到目前為止此 future `accelerator_view` 物件。  
  
##  <a name="a-nameacceleratorviewflushmethoda-acceleratorviewflush-method"></a><a name="accelerator_view__flush_method"></a>  accelerator_view:: flush 方法  
 送出所有暫止命令排入佇列 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 執行對應的物件。  
  
```  
void flush();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `void`。  
  
##  <a name="a-nameacceleratorviewgetacceleratormethoda-acceleratorviewgetaccelerator-method"></a><a name="accelerator_view__get_accelerator_method"></a>  accelerator_view:: get_accelerator 方法  
 傳回 [加速器](../../../parallel/amp/reference/accelerator-class.md) 物件 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件。  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>傳回值  
  `accelerator` 物件 `accelerator_view` 物件。  
  
##  <a name="a-nameacceleratorviewgetisautoselectionmethoda-acceleratorviewgetisautoselection-method"></a><a name="accelerator_view__get_is_auto_selection_method"></a>  accelerator_view:: get_is_auto_selection 方法  
 傳回布林值，指出是否執行階段會自動選取適當的加速器 accelerator_view 傳遞至 [parallel_for_each](../Topic/concurrency%20namespace%20functions.md#parallel_for_each)。  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 `true` 如果執行階段會自動選取適當的對應。否則， `false`。  
  
##  <a name="a-nameacceleratorviewgetisdebugmethoda-acceleratorviewgetisdebug-method"></a><a name="accelerator_view__get_is_debug_method"></a>  accelerator_view:: get_is_debug 方法  
 傳回布林值，指出是否 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件已啟用大量錯誤報告的偵錯層。  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 布林值，指出是否 `accelerator_view` 物件已啟用大量錯誤報告的偵錯層。  
  
##  <a name="a-nameacceleratorviewgetqueuingmodemethoda-acceleratorviewgetqueuingmode-method"></a><a name="accelerator_view__get_queuing_mode_method"></a>  accelerator_view:: get_queuing_mode 方法  
 傳回的佇列模式 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件。  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 佇列模式 `accelerator_view` 物件。  
  
##  <a name="a-nameacceleratorviewgetversionmethoda-acceleratorviewgetversion-method"></a><a name="accelerator_view__get_version_method"></a>  accelerator_view:: get_version 方法  
 傳回的版本 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md)。  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 版本 `accelerator_view`。  
  
##  <a name="a-nameacceleratorviewisautoselectiondatamembera-acceleratorviewisautoselection-data-member"></a><a name="accelerator_view__is_auto_selection_data_member"></a>  accelerator_view:: is_auto_selection 資料成員  
 取得布林值，指出是否執行階段會自動選取適當的加速器 accelerator_view 傳遞至 [parallel_for_each](concurrency%20namespace%20functions.md#parallel_for_each)。  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="a-nameacceleratorviewisdebugdatamembera-acceleratorviewisdebug-data-member"></a><a name="accelerator_view__is_debug_data_member"></a>  accelerator_view:: is_debug 資料成員  
 取得布林值，指出是否 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件已啟用大量錯誤報告的偵錯層。  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameacceleratorviewoperatorneqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_neq_operator"></a>  accelerator_view:: operator ！ = 運算子  
 比較這個 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 與另一個物件，然後傳回 `false` 如果兩個名稱相同; 否則會傳回 `true`。  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
  `accelerator_view` 要與這個比較的物件。  
  
### <a name="return-value"></a>傳回值  
 如果這兩個物件相同則為 `false`，否則為 `true`。  
  
##  <a name="a-nameacceleratorviewoperatoreqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_eq_operator"></a>  accelerator_view:: operator = 運算子  
 將指定的內容複製 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 到這裡的物件。  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
  `accelerator_view` 從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 修改過的參考 `accelerator_view` 物件。  
  
##  <a name="a-nameacceleratorviewoperatoreqeqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_eq_eq_operator"></a>  accelerator_view:: operator = = 運算子  
 比較這個 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 與另一個物件，然後傳回 `true` 如果兩個名稱相同; 否則會傳回 `false`。  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
  `accelerator_view` 要與這個比較的物件。  
  
### <a name="return-value"></a>傳回值  
 如果這兩個物件相同則為 `true`，否則為 `false`。  
  
##  <a name="a-nameacceleratorviewqueuingmodedatamembera-acceleratorviewqueuingmode-data-member"></a><a name="accelerator_view__queuing_mode_data_member"></a>  accelerator_view:: queuing_mode 資料成員  
 取得佇列模式 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件。  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="a-nameacceleratorviewversiondatamembera-acceleratorviewversion-data-member"></a><a name="accelerator_view__version_data_member"></a>  accelerator_view:: version 資料成員  
 取得版本 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md)。  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="a-nameacceleratorviewwaitmethoda-acceleratorviewwait-method"></a><a name="accelerator_view__wait_method"></a>  accelerator_view:: wait 方法  
 等候所有命令送出至 [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件來完成。  
  
```  
void wait();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `void`。  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (c + + AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
