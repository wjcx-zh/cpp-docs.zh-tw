---
title: "使用 accelerator 和 accelerator_view 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 accelerator 和 accelerator_view 物件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用 [加速器](../../parallel/amp/reference/accelerator-class.md) 和 [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) 類別來指定裝置或模擬器上執行您的 c + + AMP 程式碼。 系統可能有數個裝置或模擬器不同的記憶體數量、 共用的記憶體支援、 偵錯支援或雙精確度的支援。 C + + Accelerated Massive Parallelism (c + + AMP) 提供 Api，您可以檢查可用的快速鍵、 設定為預設值、 指定多個位於 accelerator_views 的 parallel_for_each 而言，多個呼叫和執行特殊的偵錯工作。  
  
## <a name="using-the-default-accelerator"></a>使用預設加速器  
 C + + AMP 執行階段會挑選預設加速器，除非您撰寫程式碼中挑選一個。 執行階段會選擇在預設加速器，如下所示︰  
  
1.  如果在偵錯模式中執行應用程式，快速鍵可支援偵錯。  
  
2.  否則，為 CPPAMP_DEFAULT_ACCELERATOR 環境變數所指定，如果設定的快速鍵。  
  
3.  否則，非模擬的裝置。  
  
4.  否則，具有最大的可用記憶體的裝置。  
  
5.  否則，不會附加至顯示裝置。  
  
 此外，執行階段指定 `access_type` 的 `access_type_auto` 預設加速器。 這表示在預設加速器使用共用的記憶體，如果支援，以及其效能特性 （頻寬和延遲） 皆為固定 （非共用） 記憶體相同。  
  
 您可以藉由建構預設加速器，並檢查其屬性來判斷預設加速器的屬性。 下列程式碼範例會列印路徑，加速器記憶體、 共用的記憶體支援、 雙精度的支援，以及有限的雙精確度支援在預設加速器。  
  
```cpp  
 
void default_properties() {  
    accelerator default_acc;  
    std::wcout <<default_acc.device_path <<"\n";  
    std::wcout <<default_acc.dedicated_memory <<"\n";  
    std::wcout <<(accs[i].supports_cpu_shared_memory    
 "CPU shared memory: true" : "CPU shared memory: false") <<"\n";  
    std::wcout <<(accs[i].supports_double_precision    
 "double precision: true" : "double precision: false") <<"\n";  
    std::wcout <<(accs[i].supports_limited_double_precision    
 "limited double precision: true" : "limited double precision: false") <<"\n";  
}  
 
```  
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>CPPAMP_DEFAULT_ACCELERATOR 環境變數  
 您可以設定 CPPAMP_DEFAULT_ACCELERATOR 環境變數來指定 `accelerator::device_path` 預設加速器。 路徑是硬體而異。 下列程式碼會使用 `accelerator::get_all` 函式來擷取一份可用的快速鍵，並顯示每個加速器的特性與路徑。  
  
```cpp  
 
void list_all_accelerators()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
for (int i = 0; i <accs.size();

i++) {  
    std::wcout <<accs[i].device_path <<"\n";  
    std::wcout <<accs[i].dedicated_memory <<"\n";  
    std::wcout <<(accs[i].supports_cpu_shared_memory    
 "CPU shared memory: true" : "CPU shared memory: false") <<"\n";  
    std::wcout <<(accs[i].supports_double_precision    
 "double precision: true" : "double precision: false") <<"\n";  
    std::wcout <<(accs[i].supports_limited_double_precision    
 "limited double precision: true" : "limited double precision: false") <<"\n";  
 }  
}  
 
```  
  
## <a name="selecting-an-accelerator"></a>選取快速鍵  
 若要選取加速器，請使用 `accelerator::get_all` 擷取可用的快速鍵的清單，然後選取其中一個方法會根據其內容。 此範例顯示如何挑選具有最多記憶體的加速器︰  
  
```cpp  
 
void pick_with_most_memory()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
accelerator acc_chosen = accs[0];  
    for (int i = 0; i <accs.size();

i++) {  
    if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {  
    acc_chosen = accs[i];  
 }  
 }  
 
    std::wcout <<"The accelerator with the most memory is "    
 <<acc_chosen.device_path <<"\n"  
 <<acc_chosen.dedicated_memory <<".\n";  
}  
 
```  
  
> [!NOTE]
>  其中一個傳回的加速器 `accelerator::get_all` 是 CPU 加速器。 您無法在 CPU 加速器上執行程式碼。 若要篩選出 CPU 加速器，比較值 [device_path](../Topic/accelerator::device_path%20Data%20Member.md) 屬性所傳回的加速器 `accelerator::get_all` 值是 [accelerator:: cpu_accelerator](../Topic/accelerator::cpu_accelerator%20Data%20Member.md)。 如需詳細資訊，請參閱本文 「 加速器特殊 」 一節。  
  
## <a name="shared-memory"></a>共用的記憶體  
 共用的記憶體是可以存取的 CPU 和快速鍵。 使用共用記憶體會消除或大幅降低 CPU 與對應鍵之間複製資料的額外負荷。 雖然共用記憶體時，它 CPU 和加速器，無法並行存取，而且這樣做，就會導致未定義的行為。 快速鍵屬性 [supports_cpu_shared_memory](../Topic/accelerator::supports_cpu_shared_memory%20Data%20Member.md) 傳回 `true` 如果加速器支援共用的記憶體，而 [default_cpu_access_type](../Topic/accelerator::default_cpu_access_type%20Data%20Member.md) 屬性會取得預設 [access_type](../Topic/access_type%20Enumeration.md) 上配置的記憶體 `accelerator`— 比方說， `array`與相關聯 `accelerator`, ，或 `array_view` 物件上存取 `accelerator`。  
  
 C + + AMP 執行階段會自動選擇最佳預設 `access_type` 每個 `accelerator`, ，但讀取 CPU、 CPU 或兩者都從寫入時，共用記憶體的效能特性 （頻寬和延遲） 可以是最糟的固定 （非共用） 的對應記憶體。 如果共用的記憶體執行以及專用的記憶體讀取及寫入 cpu 時，執行階段會預設為 `access_type_read_write`; 否則執行階段會選擇時較為保守的預設 `access_type`, ，並可讓應用程式，以覆寫它，如果其計算核心的記憶體存取模式受益於不同 `access_type`。  
  
 下列程式碼範例示範如何判斷是否在預設加速器支援共用的記憶體，然後覆寫其預設存取類型，並建立 `accelerator_view` 從它。  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
  accelerator acc = accelerator(accelerator::default_accelerator);  
  
  // Early out if the default accelerator doesn’t support shared memory.  
  if(!acc.supports_cpu_shared_memory)  
  {  
    std::cout << "The default accelerator does not support shared memory" << std::endl;  
    return 1;  
  }  
  
  // Override the default CPU access type.  
  acc.set_default_cpu_access_type(access_type_read_write);  
  
  // Create an accelerator_view from the default accelerator. The  
  // accelerator_view reflects the default_cpu_access_type of the  
  // accelerator it’s associated with.  
  accelerator_view acc_v = acc.default_view;  
}  
  
```  
  
  `accelerator_view` 永遠反映 `default_cpu_access_type` 的 `accelerator` 與其相關聯，而且它會提供任何介面，以覆寫或變更其 `access_type`。  
  
## <a name="changing-the-default-accelerator"></a>變更預設對應鍵  
 您可以變更預設加速器，藉由呼叫 `accelerator::set_default` 方法。 您可以變更預設加速器，只要每個應用程式執行，您必須先將它變更 GPU 上執行任何程式碼。 若要變更加速器任何後續的函式呼叫傳回 `false`。 如果您想在呼叫中使用不同的加速器 `parallel_for_each`, ，閱讀這篇文章的 「 使用多個加速器 」 一節。 下列程式碼範例，不會模擬、 未連線至顯示器，並支援雙精確度的其中一個設定的預設加速器。  
  
```cpp  
 
    bool pick_accelerator()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
accelerator chosen_one;  
 
    auto result = 
    std::find_if(accs.begin(), accs.end(), [] (const accelerator& acc)  
 {  
    return !acc.is_emulated&& 
    acc.supports_double_precision&& 
 !acc.has_display;  
 });

 
    if (result != accs.end())  
    chosen_one = *(result);

 
    std::wcout <<chosen_one.description <<std::endl;  
 
    bool success = accelerator::set_default(chosen_one.device_path);

    return success;  
}  
 
```  
  
## <a name="using-multiple-accelerators"></a>使用多個加速器  
 有兩種方式可在您的應用程式中使用多個加速器︰  
  
-   您可以傳遞 `accelerator_view` 物件呼叫 [parallel_for_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 方法。  
  
-   您可以建構 `array` 物件使用特定 `accelerator_view` 物件。 C + AMP 執行階段會自動挑選 `accelerator_view` 物件擷取 `array` lambda 運算式中的物件。  
  
## <a name="special-accelerators"></a>特殊加速器  
 裝置路徑的三個特殊的加速器可供使用的屬性為 `accelerator` 類別︰  
  
- [accelerator:: direct3d_ref 資料成員](../Topic/accelerator::direct3d_ref%20Data%20Member.md)︰ 這個單一執行緒的加速器 CPU 上使用軟體來模擬一般的圖形卡。 使用預設情況下進行偵錯，但它並不適用於生產因為低於硬體加速器。 此外，它只適用於 DirectX SDK 和 Windows SDK，而且它太安裝在您客戶的電腦上。 如需詳細資訊，請參閱 [偵錯 GPU 程式碼](../Topic/Debugging%20GPU%20Code.md)。  
  
- [accelerator:: direct3d_warp 資料成員](../Topic/accelerator::direct3d_warp%20Data%20Member.md)︰ 這個加速器提供後援方案使用 Streaming SIMD Extensions (SSE) 的多核心 Cpu 上執行 c + + AMP 程式碼。  
  
- [accelerator:: cpu_accelerator 資料成員](../Topic/accelerator::cpu_accelerator%20Data%20Member.md)︰ 您可以使用此快速鍵設定暫存陣列。 它無法執行 c + + AMP 程式碼。 如需詳細資訊，請參閱 [c + + AMP 中的暫存陣列](http://go.microsoft.com/fwlink/p/LinkId=248485) 平行程式設計原生程式碼的部落格文章。  
  
## <a name="interoperability"></a>互通性  
 C + + AMP 執行階段支援互通性之間 `accelerator_view` 類別和 Direct3D [ID3D11Device 介面](http://go.microsoft.com/fwlink/p/LinkId=248488)。  [Create_accelerator_view](../Topic/create_accelerator_view%20Function.md) 方法會採用 `IUnknown` 介面，並傳回 `accelerator_view` 物件。  [Get_device](http://msdn.microsoft.com/zh-tw/8194125e-8396-4d62-aa8a-65831dea8439) 方法會採用 `accelerator_view` 物件，然後傳回 `IUknown` 介面。  
  
## <a name="see-also"></a>另請參閱  
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [偵錯 GPU 程式碼](../Topic/Debugging%20GPU%20Code.md)   
 [accelerator_view 類別](../../parallel/amp/reference/accelerator-view-class.md)
