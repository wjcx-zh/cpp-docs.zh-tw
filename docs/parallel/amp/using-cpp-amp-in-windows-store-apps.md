---
title: 在 UWP 應用程式中使用 c + + AMP |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3676bc8f2c4ecbd89f01fb9257c7306a66827548
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584012"
---
# <a name="using-c-amp-in-uwp-apps"></a>在 UWP 應用程式中使用 c + + AMP
您可以在通用 Windows 平台 (UWP) 應用程式中使用 c + + AMP (c + + Accelerated Massive Parallelism)，在 GPU （圖形處理單元） 或其他運算加速器上執行計算。 然而，C++ AMP 並未提供可直接搭配 Windows 執行階段類型使用的 API，而 Windows 執行階段也未提供 C++ AMP 的包裝函式。 當您在程式碼中使用 Windows 執行階段類型 (包括您自行建立的類型) 時，必須將這些類型轉換成與 C++ AMP 相容的類型。  
  
## <a name="performance-considerations"></a>效能考量  
 
如果您使用 Visual c + + 元件擴充功能中 C + + /CX，以建立您的通用 Windows 平台 (UWP) 應用程式，我們建議您先使用連續的儲存體以及純舊資料 (POD) 類型 — 比方說，`std::vector`或 C 樣式陣列 — 會的資料搭配使用 c + + AMP。 這可協助您達成更高的效能比使用非 POD 類型或 Windows RT 容器，因為沒有封送處理發生。  
  
在 c + + AMP 核心中，以存取資料儲存在這種方式，只是包裝`std::vector`或陣列中的儲存體`concurrency::array_view`，然後使用 [陣列] 檢視中的`concurrency::parallel_for_each`迴圈：  
  
```cpp  
// simple vector addition example  
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);
  
concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);
  
av2.discard_data();
  
concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)  
    {  
        av2[idx] = av0[idx] + av1[idx];  
    });
```  
  
## <a name="marshaling-windows-runtime-types"></a>封送處理 Windows 執行階段型別  
 
當您使用 Windows 執行階段 Api 時，您可能想要這類儲存在 Windows 執行階段容器中的資料使用 c + + AMP`Platform::Array<T>^`或例如類別或結構宣告使用的複雜資料型別**ref**關鍵字或**值**關鍵字。 在這些情況下，您必須執行一些額外的工作，可讓 c + + AMP 中使用的資料。  
  
### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform:: array\<T > ^，其中 T 是 POD 類型  
當您遇到`Platform::Array<T>^`T 是 POD 類型，您可以存取其基礎儲存體，只要使用`get`成員函式：  
  
```cpp  
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API  
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```  
  
如果 T 不是 POD 類型，使用下一節中所述的技巧，以搭配 c + + AMP 中的資料。  
  
### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Windows 執行階段型別: ref 類別和實值類別  
C + + AMP 不支援複雜資料型別。 這包括非 POD 類型以及宣告使用的任何型別**ref**關鍵字則**值**關鍵字。 如果不支援的類型用在`restrict(amp)`會產生編譯時期錯誤的內容。  
  
當您遇到不支援的類型時，您可以將複製資料有興趣的部分`concurrency::array`物件。 除了讓資料適用於 c + + AMP 使用，此手動複製方法也會改善效能最大化資料局部性，並確保不會使用的資料不複製到這個加速器。 您可以使用，以改善效能進一步*預備環境陣列*，這是一種特殊形式的`concurrency::array`，會提示 AMP 執行階段陣列應該最佳化的其他陣列之間頻繁的傳輸上指定的加速器。  
  
```cpp  
// pixel_color.h  
ref class pixel_color sealed  
{  
public: 
    pixel_color(Platform::String^ color_name, int red, int green, int blue)   
    {  
        name = color_name;  
        r = red;  
        g = green;  
        b = blue;  
    }  
 
    property Platform::String^ name;   
    property int r;  
    property int g;  
    property int b;  
};  
  
// Some other file  
  
std::vector<pixel_color^> pixels (256);
  
for (pixel_color ^pixel : pixels)   
{  
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}  
  
// Create the accelerators  
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);
  
// Create the staging arrays  
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
  
// Extract data from the complex array of structs into staging arrays.  
concurrency::parallel_for(0, 256, [&](int i)  
    {   
        red_vec[i] = pixels[i]->r;  
        blue_vec[i] = pixels[i]->b;  
    });
  
// Array views are still used to copy data to the accelerator  
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);
  
// Change all pixels from blue to red.  
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)  
    {  
        av_red[idx] = 255;  
        av_blue[idx] = 0;  
    });
```  
  
## <a name="see-also"></a>另請參閱  
 
[建立第一個 UWP 應用程式使用 c + +](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)   
[在 c + + 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)