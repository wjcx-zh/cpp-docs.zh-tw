---
title: 使用 accelerator 和 accelerator_view 物件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebbb33a4f17f5b4d458c4add4d59040d698dd4b8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222190"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>使用 accelerator 和 accelerator_view 物件
您可以使用[加速器](../../parallel/amp/reference/accelerator-class.md)並[accelerator_view](../../parallel/amp/reference/accelerator-view-class.md)類別來指定裝置或模擬器上執行您的 c + + AMP 程式碼。 系統可能包含數個裝置或模擬器不同的記憶體數量、 共用的記憶體支援、 偵錯支援或雙精確度支援。 C + + Accelerated Massive Parallelism (c + + AMP) 提供的 Api，可用來檢查可用的加速器，設定為預設值，指定多個對 parallel_for_each 而言，多個呼叫的 accelerator_views 和執行特殊的偵錯工作。  
  
## <a name="using-the-default-accelerator"></a>使用預設加速器  
 
C + + AMP 執行階段會挑選預設的加速器，除非您撰寫程式碼來選擇特定加速器。 執行階段會選擇預設加速器，如下所示：  
  
1. 應用程式正在執行以偵錯模式中，如果加速器支援偵錯。  
  
2. 否則，如果設定 CPPAMP_DEFAULT_ACCELERATOR 環境變數中，所指定的加速器。  
  
3. 否則，非模擬的裝置。  
  
4. 否則，具有最大的可用記憶體的裝置。  
  
5. 否則，不會附加至顯示的裝置。  
  
此外，指定執行階段`access_type`的`access_type_auto`預設加速器。 這表示預設加速器會使用共用的記憶體，如果支援，以及其效能特性 （頻寬和延遲） 已知與專用 （非共用） 記憶體相同。  
  
您可以建立預設加速器並檢查其屬性，以判斷預設加速器的屬性。 下列程式碼範例會列印路徑，也就是數量加速器記憶體、 共用的記憶體支援、 雙精確度支援以及預設加速器的有限的雙精確度支援。  
  
```cpp  
void default_properties() {  
    accelerator default_acc;  
    std::wcout << default_acc.device_path << "\n";  
    std::wcout << default_acc.dedicated_memory << "\n";  
    std::wcout << (accs[i].supports_cpu_shared_memory ?   
        "CPU shared memory: true" : "CPU shared memory: false") << "\n";  
    std::wcout << (accs[i].supports_double_precision ?   
        "double precision: true" : "double precision: false") << "\n";  
    std::wcout << (accs[i].supports_limited_double_precision ?   
        "limited double precision: true" : "limited double precision: false") << "\n";  
}  
```  
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>CPPAMP_DEFAULT_ACCELERATOR 環境變數  
您可以設定 CPPAMP_DEFAULT_ACCELERATOR 環境變數，以指定`accelerator::device_path`預設加速器。 路徑與硬體相依。 下列程式碼會使用`accelerator::get_all`函式來擷取可用加速器清單，並接著會顯示每個加速器的特性與路徑。  
  
```cpp  
void list_all_accelerators()  
{  
    std::vector<accelerator> accs = accelerator::get_all();  
  
    for (int i = 0; i <accs.size(); i++) {  
        std::wcout << accs[i].device_path << "\n";  
        std::wcout << accs[i].dedicated_memory << "\n";  
        std::wcout << (accs[i].supports_cpu_shared_memory ?   
            "CPU shared memory: true" : "CPU shared memory: false") << "\n";  
        std::wcout << (accs[i].supports_double_precision ?   
            "double precision: true" : "double precision: false") << "\n";  
        std::wcout << (accs[i].supports_limited_double_precision ?   
            "limited double precision: true" : "limited double precision: false") << "\n";  
    }  
}  
```  
  
## <a name="selecting-an-accelerator"></a>選取加速器  
 
若要選取加速器，請使用`accelerator::get_all`方法來擷取可用加速器清單，然後選取其中一個會根據其屬性。 此範例顯示如何挑選擁有最多記憶體的加速器：  
  
```cpp  
void pick_with_most_memory()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator acc_chosen = accs[0];  
    
    for (int i = 0; i <accs.size(); i++) {  
        if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {  
            acc_chosen = accs[i];  
        }  
    }  
 
    std::wcout << "The accelerator with the most memory is "    
        << acc_chosen.device_path << "\n"  
        << acc_chosen.dedicated_memory << ".\n";  
}  
```  
  
> [!NOTE]
> 其中一個所傳回的加速器`accelerator::get_all`是 CPU 加速器。 您無法在 CPU 加速器上執行的程式碼。 若要篩選掉 CPU 加速器，比較的值[device_path](reference/accelerator-class.md#device_path)屬性所傳回的加速器`accelerator::get_all`的值[accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator)。 如需詳細資訊，請參閱本文 < 特殊的加速器 」 一節。  
  
## <a name="shared-memory"></a>共用的記憶體  
 
共用的記憶體是可由 CPU 和加速器存取的記憶體。 使用共用記憶體排除或大幅降低的 CPU 和加速器之間複製資料的額外負荷。 雖然共用記憶體，其 CPU 和加速器，無法並行存取，而且會產生未定義的行為。 快速鍵屬性[supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)會傳回 **，則為 true**如果加速器支援共用的記憶體，而[default_cpu_access_type 未](reference/accelerator-class.md#default_cpu_access_type)屬性會取得預設值[access_type](reference/concurrency-namespace-enums-amp.md#access_type)配置之記憶體`accelerator`— 比方說，**陣列**相關聯的 s `accelerator`，或`array_view`上存取的物件`accelerator`. 
  
C + + AMP 執行階段會自動選擇最佳的預設值`access_type`針對每個`accelerator`，但讀取時，共用記憶體的效能特性 （頻寬和延遲） 可能會比專用 （非共用） 加速器記憶體的差從 CPU 寫入從 CPU，或兩者。 如果共用的記憶體執行以及從 CPU 讀取和寫入的專屬記憶體，執行階段預設值為`access_type_read_write`; 否則執行階段會選擇較保守的預設`access_type`，並允許覆寫它，如果記憶體存取應用程式其計算核心模式受益於不同`access_type`。  
  
下列程式碼範例示範如何判斷是否預設加速器支援共用的記憶體，然後覆寫其預設存取類型，並建立`accelerator_view`從它。  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
    accelerator acc = accelerator(accelerator::default_accelerator);  
  
    // Early out if the default accelerator doesn’t support shared memory.  
    if (!acc.supports_cpu_shared_memory)  
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
  
`accelerator_view`一律會反映`default_cpu_access_type`的`accelerator`與其相關聯，而且它會提供任何介面來覆寫或變更其`access_type`。  
  
## <a name="changing-the-default-accelerator"></a>變更預設加速器  
 
您可以藉由呼叫來變更預設加速器`accelerator::set_default`方法。 只要每個應用程式執行，而且您必須變更它在 GPU 上執行的任何程式碼之前，您可以變更預設加速器。 若要變更加速器的任何後續的函式呼叫會傳回**false**。 如果您想要的呼叫中使用不同的 accelerator `parallel_for_each`，閱讀這篇文章中的 「 使用多個 Accelerator 」 一節。 下列程式碼範例會將預設加速器設定為未模擬、 未連接至顯示器，並支援雙精確度。  
  
```cpp  
bool pick_accelerator()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator chosen_one;  
 
    auto result = std::find_if(accs.begin(), accs.end(), 
        [] (const accelerator& acc) {  
            return !acc.is_emulated && 
                acc.supports_double_precision && 
                !acc.has_display;  
        });
  
    if (result != accs.end()) {  
        chosen_one = *(result);
    }
  
    std::wcout <<chosen_one.description <<std::endl;  
    bool success = accelerator::set_default(chosen_one.device_path);
    return success;  
}  
```  
  
## <a name="using-multiple-accelerators"></a>使用多個加速器  
 
有兩種方式可在您的應用程式中使用多個加速器：  

- 您可以傳遞`accelerator_view`到呼叫的物件[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。  
  
- 您可以建構**陣列**物件使用特定`accelerator_view`物件。 C + + AMP 執行階段會挑選`accelerator_view`從擷取的物件**陣列**lambda 運算式中的物件。  
  
## <a name="special-accelerators"></a>特殊快速鍵  
 
三個特殊加速器的裝置路徑會當作屬性`accelerator`類別：  
  
- [accelerator::direct3d_ref 資料成員](reference/accelerator-class.md#direct3d_ref)： 此單一執行緒加速器在 CPU 上使用軟體來模擬一般圖形卡。 它預設會使用偵錯，但它並不適用於生產環境因為比硬體加速器慢。 此外，它是僅適用於 DirectX SDK 和 Windows SDK，並不太可能安裝在您客戶的電腦上。 如需詳細資訊，請參閱 <<c0> [ 偵錯 GPU 程式碼](/visualstudio/debugger/debugging-gpu-code)。  
  
- [accelerator::direct3d_warp 資料成員](reference/accelerator-class.md#direct3d_warp)： 此加速器提供後援解決方案，來使用 Streaming SIMD Extensions (SSE) 的多核心 Cpu 上執行 c + + AMP 程式碼。  
  
- [accelerator:: cpu_accelerator 資料成員](reference/accelerator-class.md#cpu_accelerator)： 您可以使用這個加速器來設定預備環境陣列。 它無法執行 c + + AMP 程式碼。 如需詳細資訊，請參閱 < [c + + AMP 中的預備環境陣列](http://go.microsoft.com/fwlink/p/?linkId=248485)上平行程式設計的原生程式碼的部落格文章。  
  
## <a name="interoperability"></a>互通性  
 
C + + AMP 執行階段支援之間的互通性`accelerator_view`類別與 Direct3D [ID3D11Device 介面](http://go.microsoft.com/fwlink/p/?linkId=248488)。 [Create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)方法會採用`IUnknown`介面，並傳回`accelerator_view`物件。 [Get_device](https://msdn.microsoft.com/8194125e-8396-4d62-aa8a-65831dea8439)方法會採用`accelerator_view`物件，然後傳回`IUknown`介面。  
  
## <a name="see-also"></a>另請參閱  
 
[C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
[偵錯 GPU 程式碼](/visualstudio/debugger/debugging-gpu-code)   
[accelerator_view 類別](../../parallel/amp/reference/accelerator-view-class.md)