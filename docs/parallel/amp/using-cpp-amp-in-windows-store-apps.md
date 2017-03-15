---
title: "在 Windows 市集應用程式中使用 C++ AMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
caps.latest.revision: 14
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Windows 市集應用程式中使用 C++ AMP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用 C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)，執行 GPU \(圖形處理單元\) 或其他運算加速器上的計算。  然而，C\+\+ AMP 未提供可直接使用 Windows 執行階段類型的應用程式開發介面，而 Windows 執行階段 也未提供 C\+\+ AMP 的包裝函式。  當您在程式碼中使用 Windows 執行階段類型 \(包括您自行建立的類型\) 時，您必須轉換成與 C\+\+ AMP 相容的類型。  
  
## 效能考量  
 如果您使用 [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]\) 建立 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式，建議您使用簡單舊資料 \(POD\) 類型與適用於 C\+\+ AMP 的連續儲存區 \(例如 `std::vector` 或 C\-Style 陣列\) 一起搭配。  因為不需要進行封送處理，這有助於達到比使用非 POD 類型或 Windows RT 容器還要高的效能。  
  
 在 C\+\+ AMP 核心中，若要存取以這種方式儲存的資料，只需將 `std::vector` 或陣列儲存區包裝在 `concurrency::array_view` 內，然後在 `concurrency::parallel_for_each` 迴圈中使用陣列檢視：  
  
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
  
## 封送處理 Windows 執行階段型別  
 當您使用Windows 執行階段 應用程式開發介面時，可以針對 Windows 執行階段容器 \(例如 `Platform::Array<T>^`\) 中或在複雜資料類型 \(例如使用 `ref` 關鍵字或 `value` 關鍵字宣告的類別或結構\) 中儲存的資料使用 C\+\+ AMP。  在這些情況下，您必須進行一些額外的工作，讓資料可供 C\+\+ AMP 使用。  
  
### Platform::Array\<T\>^，其中 T 是 POD 類型  
 當您遇到 `Platform::Array<T>^`，而 T 是 POD 類型時，可透過使用 `get` 成員函式存取基礎儲存區：  
  
```cpp  
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API  
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));  
  
```  
  
 如果 T 不是 POD 類型，請使用下列章節中描述的技術，搭配 C\+\+ AMP 使用資料。  
  
### Windows 執行階段型別: ref 類別和實值類別  
 C\+\+ AMP 不支援複雜資料類型。  這包括非 POD 類型以及任何使用 `ref` keyword or the `value` 關鍵字宣告的類型。  如果在 `restrict(amp)` 內容中使用不支援的類型，則會產生編譯時期錯誤。  
  
 遇到未支援的類型時，您可以將其資料中有用的部分複製到 `concurrency::array` 物件。  除了讓資料可供 C\+\+ AMP 使用之外，這種手動複製方法也可以改善效能，作法是最大化資料局部性，並確保不使用的資料不會複製到這個加速器。  您可以使用「*預備環境陣列*」\(Staging Array\) 改善效能，這是一種特殊形式的 `concurrency::array`，會提示 AMP 執行階段應針對與特定加速器上其他陣列之間頻繁的傳輸進行陣列最佳化。  
  
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
..property int b;  
};  
  
// Some other file  
std::vector<pixel_color^> pixels (256);   
  
for(pixel_color ^pixel : pixels)   
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
  red_vec[i] = pixels[i]->r; blue_vec[i] = pixels[i]->b;  
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
  
## 請參閱  
 [使用 C\+\+ 建立您的第一個 Windows 市集應用程式](http://go.microsoft.com/fwlink/p/?LinkId=249073)   
 [在 C\+\+ 中建立 Windows 執行階段元件](http://go.microsoft.com/fwlink/p/?LinkId=249076)