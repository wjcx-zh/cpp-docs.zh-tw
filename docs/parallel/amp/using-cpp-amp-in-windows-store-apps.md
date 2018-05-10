---
title: 在 UWP 應用程式中使用 c + + AMP |Microsoft 文件
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
ms.openlocfilehash: 5736c84f21535222de5659780968efd98e1467da
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="using-c-amp-in-uwp-apps"></a>在 UWP 應用程式中使用 c + + AMP
在 GPU （圖形處理單元） 或其他計算加速器上執行計算，您可以在通用 Windows 平台 (UWP) 應用程式中使用 c + + AMP (c + + Accelerated Massive Parallelism)。 然而，C++ AMP 並未提供可直接搭配 Windows 執行階段類型使用的 API，而 Windows 執行階段也未提供 C++ AMP 的包裝函式。 當您在程式碼中使用 Windows 執行階段類型 (包括您自行建立的類型) 時，必須將這些類型轉換成與 C++ AMP 相容的類型。  
  
## <a name="performance-considerations"></a>效能考量  
 如果您使用[!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) 來建立通用 Windows 平台 (UWP) 應用程式，我們建議您先使用連續的儲存體以及純舊資料 (POD) 類型 — 例如， `std::vector` c-style 陣列或-將使用的資料與 c + + AMP。 這可協助您達到更高的效能比使用非 POD 類型或 Windows RT 容器，因為沒有封送處理發生。  
  
 在 c + + AMP 核心，如此一來，儲存的存取資料只包裝`std::vector`或陣列中的儲存體`concurrency::array_view`，然後使用中的陣列檢視`concurrency::parallel_for_each`迴圈：  
  
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
 當您使用 Windows 執行階段 API 時，可能會想要對儲存於 Windows 執行階段容器中的資料 (例如 `Platform::Array<T>^`)，或是複雜資料類型 (例如，使用 `ref` 關鍵字或 `value` 關鍵字宣告的類別或結構) 的資料使用 C++ AMP。 在這些情況下，您必須執行一些額外的工作，可讓 c + + AMP 中使用的資料。  
  
### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform:: array\<T > ^，其中 T 是 POD 類型  
 當您遇到`Platform::Array<T>^`T 是 POD 類型，您可以存取其基礎的存放裝置，只要使用`get`成員函式：  
  
```cpp  
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API  
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```  
  
 如果 T 不是 POD 類型，使用下一節所述的技巧，使用 c + + AMP 中的資料。  
  
### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Windows 執行階段型別: ref 類別和實值類別  
 C + + AMP 並不支援複雜資料型別。 這包括非 POD 類型和任何使用所宣告的型別`ref`關鍵字或`value`關鍵字。 如果不支援的類型不用於`restrict(amp)`會產生編譯時期錯誤的內容。  
  
 當您遇到不支援的類型時，您可以複製有興趣的資料部分`concurrency::array`物件。 除了讓資料適用於使用 c + + AMP，此手動複製方法也會改善效能最大化資料位置，並同時確保不會使用資料不複製到快速鍵。 您可以使用來改善效能的進一步*暫存陣列*，這是一種特殊形式`concurrency::array`提供提示給陣列應該經常它與其他陣列之間的傳輸最佳化 AMP 執行階段指定的對應。  
  
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

