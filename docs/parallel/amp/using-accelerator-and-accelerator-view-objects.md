---
title: 使用 accelerator 和 accelerator_view 物件
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: e3fed4dc2a431b751d4ad50484e32b738e786d10
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404173"
---
# <a name="using-accelerator-and-accelerator_view-objects"></a>使用 accelerator 和 accelerator_view 物件

您可以使用[快速鍵](../../parallel/amp/reference/accelerator-class.md)和[accelerator_view](../../parallel/amp/reference/accelerator-view-class.md)類別來指定要在其上執行 C++ AMP 程式碼的裝置或模擬器。 系統可能有數個裝置或模擬器，不同于記憶體數量、共用記憶體支援、偵錯工具支援或雙精確度支援。 C++ Accelerated Massive Parallelism （C++ AMP）提供的 Api 可讓您用來檢查可用的加速器、設定一個做為預設值、針對多個 parallel_for_each 呼叫指定多個 accelerator_views，以及執行特殊的偵錯工具。

## <a name="using-the-default-accelerator"></a>使用預設加速器

除非您撰寫程式碼來挑選特定的加速器，否則 C++ AMP 執行時間會挑選預設的快速鍵。 執行時間會選擇預設的快速鍵，如下所示：

1. 如果應用程式是在 debug 模式下執行，則為支援偵錯工具的加速器。

2. 否則，CPPAMP_DEFAULT_ACCELERATOR 環境變數所指定的快速鍵（如果已設定的話）。

3. 否則，非模擬裝置。

4. 否則為具有最大可用記憶體數量的裝置。

5. 否則為未連接到顯示的裝置。

此外，執行時間會 `access_type` `access_type_auto` 針對預設加速器指定的。 這表示預設加速器會使用共用記憶體（如果支援的話），以及其效能特性（頻寬和延遲）已知與專用（非共用）記憶體相同。

您可以藉由建立預設加速器，並檢查其屬性，來判斷預設加速器的屬性。 下列程式碼範例會列印預設加速器的路徑、加速器記憶體數量、共用記憶體支援、雙精確度支援，以及有限的雙精確度支援。

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

### <a name="cppamp_default_accelerator-environment-variable"></a>CPPAMP_DEFAULT_ACCELERATOR 環境變數

您可以設定 CPPAMP_DEFAULT_ACCELERATOR 環境變數，以指定 `accelerator::device_path` 預設加速器的。 路徑與硬體相關。 下列程式碼會使用函式 `accelerator::get_all` 來取出可用加速器的清單，然後顯示每個加速器的路徑和特性。

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

## <a name="selecting-an-accelerator"></a>選取快速鍵

若要選取加速器，請使用 `accelerator::get_all` 方法來抓取可用加速器的清單，然後根據其屬性來選取一個。 這個範例示範如何挑選具有最多記憶體的加速器：

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
> 所傳回的其中一個快速鍵 `accelerator::get_all` 是 CPU 加速器。 您無法在 CPU 加速器上執行程式碼。 若要篩選出 CPU 加速器，請將所傳回之快速鍵的 [ [device_path](reference/accelerator-class.md#device_path) ] 屬性值 `accelerator::get_all` 與[快速鍵：： cpu_accelerator](reference/accelerator-class.md#cpu_accelerator)的值進行比較。 如需詳細資訊，請參閱本文的「特殊加速器」一節。

## <a name="shared-memory"></a>共用記憶體

共用記憶體是可同時由 CPU 和加速器存取的記憶體。 使用共用記憶體可免除或大幅降低在 CPU 與加速器之間複製資料的額外負荷。 雖然記憶體是共用的，但 CPU 和加速器無法同時存取它，而這麼做會造成未定義的行為。 如果快速鍵支援共用記憶體，則快速鍵屬性[supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)會傳回**true** ，而[default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type)屬性會取得配置於上之記憶體的預設[access_type](reference/concurrency-namespace-enums-amp.md#access_type) `accelerator` （例如， **array**與相關聯的陣列 `accelerator` ，或是 `array_view` 在上存取的物件） `accelerator` 。

C++ AMP 執行時間會自動為每個選擇最佳的預設值 `access_type` `accelerator` ，但共用記憶體的效能特性（頻寬和延遲）可能會比讀取 cpu、從 cpu 寫入或兩者都差。 如果共用記憶體執行，以及從 CPU 讀取和寫入的專用記憶體，執行時間會預設為 `access_type_read_write` ; 否則，執行時間會選擇較保守的預設值 `access_type` ，並允許應用程式在其計算核心的記憶體存取模式受益于不同的時加以覆寫 `access_type` 。

下列程式碼範例示範如何判斷預設加速器是否支援共用記憶體，然後覆寫其預設存取類型，並 `accelerator_view` 從它建立。

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

`accelerator_view`一律 `default_cpu_access_type` `accelerator` 會反映與相關聯之的，而且不會提供任何介面來覆寫或變更其 `access_type` 。

## <a name="changing-the-default-accelerator"></a>變更預設加速器

您可以藉由呼叫方法來變更預設加速器 `accelerator::set_default` 。 您只能針對每個應用程式執行變更預設加速器一次，而且您必須在 GPU 上執行任何程式碼之前加以變更。 任何後續用來變更快速鍵的函式呼叫都會傳回**false**。 如果您想要在對的呼叫中使用不同的快速鍵 `parallel_for_each` ，請閱讀本文中的「使用多個加速器」一節。 下列程式碼範例會將預設快速鍵設定為未模擬、未連接到顯示，並支援雙精確度。

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

- 您可以將 `accelerator_view` 物件傳遞給[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法的呼叫。

- 您可以使用特定的物件來建立**陣列**物件 `accelerator_view` 。 C + AMP 執行時間會 `accelerator_view` 從 lambda 運算式中的已捕獲**陣列**物件中挑選物件。

## <a name="special-accelerators"></a>特殊加速器

三個特殊快速鍵的裝置路徑可當做類別的屬性來使用 `accelerator` ：

- [快速鍵：:d Irect3d_ref 資料成員](reference/accelerator-class.md#direct3d_ref)：此單一執行緒加速器會使用 CPU 上的軟體來模擬一般的圖形配接器。 預設會使用它來進行偵錯工具，但在生產環境中並不實用，因為它比硬體加速器慢。 此外，它僅適用于 DirectX SDK 和 Windows SDK，而且不太可能會安裝在您客戶的電腦上。 如需詳細資訊，請參閱偵測[GPU 程式碼](/visualstudio/debugger/debugging-gpu-code)。

- [快速鍵：:d Irect3d_warp 資料成員](reference/accelerator-class.md#direct3d_warp)：此加速器提供了一種回溯解決方案，可讓您在使用 STREAMING SIMD EXTENSIONS （SSE）的多核心 cpu 上執行 C++ AMP 程式碼。

- [快速鍵：： Cpu_accelerator 資料成員](reference/accelerator-class.md#cpu_accelerator)：您可以使用此加速器來設定臨時陣列。 它無法執行 C++ AMP 程式碼。 如需詳細資訊，請參閱[中的預備陣列，C++ AMP](/archive/blogs/nativeconcurrency/staging-arrays-in-c-amp)文章以機器碼撰寫的平行程式設計。

## <a name="interoperability"></a>互通性

C++ AMP 執行時間支援 `accelerator_view` 類別與 Direct3D [ID3D11Device 介面](/windows/win32/api/d3d11/nn-d3d11-id3d11device)之間的互通性。 [Create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)方法會採用 `IUnknown` 介面，並傳回 `accelerator_view` 物件。 [Get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device)方法會接受 `accelerator_view` 物件並傳回 `IUnknown` 介面。

## <a name="see-also"></a>另請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[偵錯 GPU 程式碼](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view 類別](../../parallel/amp/reference/accelerator-view-class.md)
