---
title: 圖形 (c + + AMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e91f762a6f340d4fe0dcc513dea850b977e0524c
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208724"
---
# <a name="graphics-c-amp"></a>圖形 (C++ AMP)
C + + AMP 包含在多個 Api [concurrency:: graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md)命名空間可供您存取 Gpu 的紋理支援。 以下是一些常見的情節：  
  
-   您可以使用[紋理](../../parallel/amp/reference/texture-class.md)類別作為計算及惡意探索的資料容器*空間區域性*紋理快取和 GPU 硬體的配置。 空間位置是實體上彼此相近之資料元素的屬性。  
  
-   執行階段可透過非計算著色器提供有效率的互通性。 像素、端點、鑲嵌式和輪廓著色器經常會使用或產生紋理，可讓您在 C++ AMP 計算中使用。  
  
-   C++ AMP 中的圖形應用程式開發介面可提供不同的方式來存取 sub-word 封裝的緩衝區。 紋理的格式，代表*材質*（紋理元素） 所組成的 8 位元或 16 位元純量允許這類封裝的資料儲存區的存取。  
  
## <a name="the-norm-and-unorm-types"></a>norm 及 unorm 類型  
 `norm`並`unorm`類型是限制的範圍的純量類型`float`值; 這稱為*固定*。 這些類型可以從其他純量類型明確建構。 在轉型時，此值會先轉換成`float`，然後壓制於由 norm [-1.0，1.0] 或 unorm [0.0，1.0] 允許的個別區域。 從 +/- 無限大轉型會傳回 +/-1。 並未定義從 NaN 轉型。 norm 可以從 unorm 隱含建構，而且資料不會遺失。 將運算子隱含轉換為 float 是在這些類型上定義。 這類二元運算子定義這些類型和其他內建的純量類型之間`float`和`int`: +、-， \*、 /、 = =、 ！ =，>， \<，> =、 < =。 也支援複合指派運算子: + =、-=、 \*=、 / =。 一元負運算子 (-) 則是針對 norm 類別定義。  
  
## <a name="short-vector-library"></a>短向量庫  
 短向量庫提供的功能的一些[向量類型](http://go.microsoft.com/fwlink/p/?linkid=248500)HLSL 中所定義，通常用於定義材質。 短向量是一種資料結構，可保存相同類型的一到四個值。 支援的類型包括 `double`、`float`、`int`、`norm`、`uint` 和 `unorm`。 下表顯示類型名稱。 每一種類型都有一個對應的 `typedef`，其名稱不含底線。 含底線的類型位於[concurrency:: graphics 命名空間](../../parallel/amp/reference/concurrency-graphics-namespace.md)。 不含底線的類型位於[Concurrency::graphics::direct3d 命名空間](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md)，讓他們清楚劃分開來，同樣名為基本類型這類`__int8`和`__int16`。  
  
||Length 2|長度為 3|長度為 4|  
|-|--------------|--------------|--------------|  
|double|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|  
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> float4|  
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|  
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|  
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|  
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|  
  
### <a name="operators"></a>運算子  
 如果在兩個短向量之間定義了一個運算子，則該運算子也會在短向量和純量之間定義。 此外，下列其中一個條件必須成立：  
  
-   純量的類型必須與短向量的元素類型相同。  
  
-   純量類型可以只透過一個使用者定義的轉換，隱含轉換為向量的元素類型。  
  
 此作業會在短向量與純量的每個元件之間對整個元件執行。 以下是有效的運算子：  
  
|運算子類型|有效的類型|  
|-------------------|-----------------|  
|二元運算子|對所有類型都有效: +、-、 \*，/，<br /><br /> 對整數類型有效: %、 ^、 &#124;、 &、 <\<，>><br /><br /> 兩個向量的大小必須相同，而且結果為相同大小的向量。|  
|關係運算子|對所有類型都有效：== 和 !=|  
|複合指派運算子|對所有類型都有效: + =、-=、 \*=、 / =<br /><br /> 對整數類型有效: %=、 ^ =、 &#124;=、 & =、 <\<=、 >> =|  
|遞增和遞減運算子|對所有類型都有效：++、--<br /><br /> 前置和後置都有效。|  
|位元 NOT 運算子 (~)|對整數類型有效。|  
|一元 - 運算子|除了 `unorm` 和 `uint` 以外，對所有類型都有效。|  
  
### <a name="swizzling-expressions"></a>Swizzling 運算式  
 短向量庫支援 `vector_type.identifier` 存取子建構存取短向量的元件。 `identifier`，這稱為*swizzling 運算式*，指定向量的元件。 運算式可以是左值或右值。 識別項中的個別字元可能是： x、 y、 z 和 w;或 r、 g、 b 和 a。 "x"和"r"表示第零個元件、"y"和"g"表示第一個元件，等等。 (請注意，"x" 和 "r" 不能在相同識別項中使用)。因此，"rgba" 和 "xyzw" 會傳回相同的結果。 項是 "x" 和 "y" 這類單一元件存取子都是純量實值類型。 多元件存取子則是短向量類型。 例如，如果您建構一個名為 `int_4` 且包含值 2、4、6 和 8 的 `fourInts` 向量，則 `fourInts.y` 會傳回整數 4，而 `fourInts.rg` 會傳回包含值 2 和 4 的 `int_2` 物件。  
  
## <a name="texture-classes"></a>紋理類別  
 許多 GPU 都有針對擷取像素和材質以及呈現影像和紋理最佳化的硬體與快取。 [紋理\<T，N> >](../../parallel/amp/reference/texture-class.md)類別，也就是材質物件的容器類別，會公開這些 Gpu 的紋理功能。 材質可以是：  
  
-   `int`、`uint`、`float`、`double`、`norm` 或 `unorm` 純量。  
  
-   擁有兩個或四個元件的短向量。 唯一的例外狀況是 `double_4`，它不可使用。  
  
 `texture` 物件的順位可以是 1、2 或 3。 `texture` 物件只能在呼叫 `parallel_for_each` 的 Lambda 中以傳址方式擷取。 紋理會做為 Direct3D 紋理物件儲存在 GPU 上。 如需 Direct3D 中紋理和材質的詳細資訊，請參閱[Direct3D 11 中紋理的簡介](http://go.microsoft.com/fwlink/p/?linkid=248502)。  
  
 您使用的材質類型可能是圖形程式設計中所使用眾多紋理格式的其中一種。 例如，RGBA 格式可以使用 32 位元，其中 R、G、B 和 A 純量元素各使用 8 位元。 圖形卡的紋理硬體可以根據格式存取個別元素。 例如，如果您使用 RGBA 格式，紋理硬體可以將各 8 位元的元素擷取至 32 位元格式內。 在 C++ AMP 中，您可以設定材質中每個純量元素的位元，如此就能在程式碼中自動存取個別純量元素，而不需使用位元位移。  
  
### <a name="instantiating-texture-objects"></a>具現化紋理物件  
 您可以在不進行初始化的情況下宣告紋理物件。 下列程式碼範例會宣告數個紋理物件。  
  
```cpp  
#include <amp.h>  
#include <amp_graphics.h>  
using namespace concurrency;  
using namespace concurrency::graphics;  
  
void declareTextures() {  
  
    // Create a 16-texel texture of int.   
    texture<int, 1> intTexture1(16);    
    texture<int, 1> intTexture2(extent<1>(16));   
  
    // Create a 16 x 32 texture of float_2.    
    texture<float_2, 2> floatTexture1(16, 32);    
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));     
  
    // Create a 2 x 4 x 8 texture of uint_4.   
    texture<uint_4, 3> uintTexture1(2, 4, 8);    
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));  
}  
  
```  
  
 您也可以使用建構函式宣告並初始化 `texture` 物件。 下列程式碼範例會從 `texture` 物件的向量具現化 `float_4` 物件。 每個純量元素的位元都會設為預設值。 您無法將這個建構函式搭配 `norm`、`unorm`，或是 `norm` 和 `unorm` 的短向量使用，因為它們的每個純量元素並沒有預設位元。  
  
```cpp  
#include <amp.h>  
#include <amp_graphics.h>  
#include <vector>  
using namespace concurrency;  
using namespace concurrency::graphics;  
  
void initializeTexture() {  
  
    std::vector<int_4> texels;  
    for (int i = 0; i < 768 * 1024; i++) {  
        int_4 i4(i, i, i, i);  
        texels.push_back(i4);  
    }  
  
texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());  
}  
```  
  
 您也可以使用指標指向來源資料、以位元組為單位的來源資料大小及每個純量元素的位元之建構函式多載，宣告及初始化 `texture` 物件。  
  
```cpp  
void createTextureWithBPC() { // Create the source data.  
    float source[1024* 2];   
    for (int i = 0; i <1024* 2; i++) {  
    source[i] = (float)i;  
 }  
 // Initialize the texture by using the size of source in bytes // and bits per scalar element.  
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);

}  
```  
  
 這些範例中的紋理都是在預設加速器的預設檢視上建立。 如果您想要指定 `accelerator_view` 物件，也可以使用建構函式的其他多載。 您無法在 CPU 加速器上建立紋理物件。  
  
 `texture` 物件的每個維度大小都有其限制，如下表所示。 如果您超過這些限制，就會產生執行階段錯誤。  
  
|紋理|每個維度的大小限制|  
|-------------|---------------------|  
|材質\<T，1 >|16384|  
|材質\<T，2 >|16384|  
|材質\<T，3 >|2048|  
  
### <a name="reading-from-texture-objects"></a>從紋理物件讀取  
 您可以從讀取`texture`使用的物件[texture:: operator\[\]](reference/texture-class.md#operator_at)，[材質:: operator （) 運算子](reference/texture-class.md#operator_call)，或[texture:: get 方法](reference/texture-class.md#get). 兩個運算子會傳回值，而不是參考。 因此，您無法使用 `texture` 寫入 `texture::operator\[\]` 物件。  
  
```cpp  
void readTexture() {  
    std::vector<int_2> src;      
    for (int i = 0; i <16 *32; i++) {  
    int_2 i2(i, i);

    src.push_back(i2);

 }  
 
    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

 
    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { // Use the subscript operator.        
    arr[idx].x += tex9[idx].x; // Use the function () operator.        
    arr[idx].x += tex9(idx).x; // Use the get method.  
    arr[idx].y += tex9.get(idx).y; // Use the function () operator.    
    arr[idx].y += tex9(idx[0], idx[1]).y;   
 });

 
    arr.synchronize();

} 
 
```  
  
 下列程式碼範例將示範如何在短向量中儲存紋理通道，然後將個別純量元素做為短向量的屬性存取。  
  
```cpp  
void UseBitsPerScalarElement() { // Create the image data. // Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).  
    const int image_height = 16;  
    const int image_width = 16;  
    std::vector<unsigned int> image(image_height* image_width);

 
    extent<2> image_extent(image_height, image_width);

 // By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is // stored in one 32-bit component of a uint_4.  
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

 // Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.  
    parallel_for_each(image_extent, 
 [&image_texture](index<2> idx) restrict(amp)   
 { // 4 bytes are automatically extracted when reading.  
    uint_4 color = image_texture[idx];   
    unsigned int r = color.r;   
    unsigned int g = color.g;   
    unsigned int b = color.b;   
    unsigned int a = color.a;   
 });

}  
 
```  
  
 下表列出各短向量類型中每個通道的有效位元。  
  
|紋理資料類型|每個純量元素的有效位元|  
|-----------------------|-----------------------------------|  
|int、int_2、int_4<br /><br /> uint、uint_2、uint_4|8, 16, 32|  
|int_3、uint_3|32|  
|float、float_2、float_4|16, 32|  
|float_3|32|  
|double、double_2|64|  
|norm、norm_2、norm_4<br /><br /> unorm、unorm_2、unorm、4|8, 16|  
  
### <a name="writing-to-texture-objects"></a>寫入紋理物件  
 使用[texture:: set](reference/texture-class.md#set)方法，將寫入`texture`物件。 紋理物件可以是唯讀或可讀寫的。 若要讓紋理物件成為可讀取和可寫入，下列條件必須成立：  

  
-   T 只有一個純量元件  (不允許短向量)。  
  
-   T 不是 `double`、`norm` 或 `unorm`。  
  
-   `texture::bits_per_scalar_element` 屬性為 32。  
  
 如果這三個條件都不成立，則 `texture` 物件是唯讀的。 前兩項條件會在編譯期間檢查。 如果您的程式碼嘗試寫入 `readonly` 紋理物件，則會產生編譯錯誤。 條件`texture::bits_per_scalar_element`偵測到在執行階段，並在執行階段產生[unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md)例外狀況，如果您嘗試寫入唯讀`texture`物件。  
  
 下列程式碼範例會將值寫入紋理物件。  
  
```cpp  
void writeTexture() {  
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {      
    tex1.set(idx, 0);

 });

 
}  
 
```  
  
### <a name="copying-texture-objects"></a>複製紋理物件  
 您可以複製使用的紋理物件之間[複製](reference/concurrency-namespace-functions-amp.md#copy)函式或[copy_async](reference/concurrency-namespace-functions-amp.md#copy_async)函式，如下列程式碼範例所示。  
  
```cpp  
void copyHostArrayToTexture() { // Copy from source array to texture object by using the copy function.  
    float floatSource[1024* 2];   
    for (int i = 0; i <1024* 2; i++) {  
    floatSource[i] = (float)i;  
}  
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

 // Copy from source array to texture object by using the copy function.  
    char charSource[16* 16];   
    for (int i = 0; i <16* 16; i++) {  
    charSource[i] = (char)i;  
 }  
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
// Copy from texture object to source array by using the copy function.  
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));

}  
 
```  
  
 您也可以複製從一種材質至另一個使用[texture:: copy_to](reference/texture-class.md#copy_to)方法。 兩個紋理可以位於不同的 accelerator_views 上。 當您複製到 `writeonly_texture_view` 物件時，資料會複製到基礎 `texture` 物件。 來源和目的 `texture` 物件上每個純量元素的位元和範圍必須一致。 如果未符合這些需求，執行階段就會擲回例外狀況。  

  
## <a name="texture-view-classes"></a>紋理檢視類別  
 C + + AMP 引入了[texture_view 類別](../../parallel/amp/reference/texture-view-class.md)在[!INCLUDE[vs_dev12](../../atl-mfc-shared/includes/vs_dev12_md.md)]。 紋理檢視支援相同材質類型和順做[texture 類別](../../parallel/amp/reference/texture-class.md)，但不像紋理，可提供存取額外的硬體功能，例如紋理取樣和 mipmap。 紋理檢視支援對基礎紋理資料進行唯讀、唯寫和讀寫存取。  
  
-   唯讀存取是由 `texture_view<const T, N>` 樣板特製化所提供，可支援擁有 1、2 或 4 個元件的元素、紋理取樣，以及動態存取檢視具現化時所決定之某個範圍的 Mipmap 層次。  
  
-   唯寫存取是由非特製化樣板類別 `texture_view<T, N>` 所提供，可支援擁有 2 或 4 個元件的元素，並且可以存取檢視具現化時所決定的一個 Mipmap 層次。 它不支援取樣。  
  
-   讀寫存取是由非特製化樣板類別 `texture_view<T, N>` 所提供，它就像紋理，可支援只有一個元件的元素，而檢視可以存取本身具現化時所決定的一個 Mipmap 層次。 它不支援取樣。  
  
 紋理檢視類似於陣列檢視，但不是提供自動的資料管理和移動功能， [array_view 類別](../../parallel/amp/reference/array-view-class.md)可透過提供[array 類別](../../parallel/amp/reference/array-class.md)。 `texture_view` 只能在基礎紋理資料所在的加速器檢視上存取。  
  
### <a name="writeonlytextureview-deprecated"></a>writeonly_texture_view 已被取代  
 針對[!INCLUDE[vs_dev12](../../atl-mfc-shared/includes/vs_dev12_md.md)]，c + + AMP 引入了更佳的支援硬體紋理功能，例如取樣和 mipmap，可能不會受到[writeonly_texture_view 類別](../../parallel/amp/reference/writeonly-texture-view-class.md)。 新引入的 `texture_view` 類別可支援 `writeonly_texture_view` 中功能的超集，因此 `writeonly_texture_view` 已被取代。  
  
 建議您至少針對新程式碼使用 `texture_view` 存取 `writeonly_texture_view` 先前所提供的功能。 請比較下面兩個寫入包含兩個元件 (int_2) 之紋理物件的程式碼範例。 請注意，在這兩個案例中，`wo_tv4` 檢視都必須在 Lambda 運算式中以傳值方式擷取。 以下是使用新 `texture_view` 類別的範例：  
  
```cpp  
void write2ComponentTexture() {  
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {  
    wo_tv4.set(idx, int_2(1, 1));

 });

}  
```  
  
 以下是已被取代的 `writeonly_texture_view` 類別：  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {     
    wo_tv4.set(idx, int_2(1, 1));

 });

}  
```  
  
 如您所見，如果您只是寫入主要 Mipmap 層次，則這兩個程式碼範例幾乎一模一樣。 如果您在現有程式碼中使用了 `writeonly_texture_view`，但是您不打算強化該程式碼，則不需要變更它。 不過，如果您想要改善該程式碼，建議您將它重寫為使用 `texture_view`，因為其中的增強功能可支援新的硬體紋理功能。 如需這些新功能的詳細資訊，請繼續閱讀下面內容。  
  
 如需有關取代`writeonly_texture_view`，請參閱 <<c2> [ 在 c + + AMP 紋理檢視設計概觀](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx)上平行程式設計機器碼部落格中。  
  
### <a name="instantiating-texture-view-objects"></a>具現化紋理檢視物件  
 宣告 `texture_view` 的方式類似於宣告與 `array_view` 相關聯的 `array`。 下列程式碼範例將宣告數個 `texture` 物件以及與這些物件相關聯的 `texture_view` 物件。  
  
```  
#include <amp.h>  
#include <amp_graphics.h>  
using namespace concurrency;  
using namespace concurrency::graphics;  
  
void declareTextureViews()  
{  
    // Create a 16-texel texture of int, with associated texture_views.  
    texture<int, 1> intTexture(16);  
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only  
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write  
  
    // Create a 16 x 32 texture of float_2, with associated texture_views.  
    texture<float_2, 2> floatTexture(16, 32);  
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only  
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only  
  
    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.  
    texture<uint_4, 3> uintTexture(2, 4, 8);  
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only  
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only  
}  
```  
  
 請注意，元素類型為非 const 且擁有一個元件的紋理檢視為讀寫，但是元素類型為非 const 且擁有多個元件的紋理檢視為唯寫。 const 元素類型的紋理檢視一律為唯讀，不過，如果元素類型為非 const，則元素中的元件數目會決定其為讀寫 (1 個元件) 或唯寫 (多個元件)。  
  
 `texture_view` 的元素類型 (其 const 性質以及擁有的元件數目) 也扮演著決定檢視是否支援紋理取樣及如何存取 Mipmap 層次的重要角色：  
  
|類型|元件|讀取|Write|取樣|Mipmap 存取|  
|----------|----------------|----------|-----------|--------------|-------------------|  
|texture_view\<const T，N> >|1, 2, 4|[是]|否 (1)|[是]|是，可索引。 範圍於具現化時決定。|  
|Texture_view\<T，N> >|1<br /><br /> 2, 4|[是]<br /><br /> 否 （2)|[是]<br /><br /> [是]|否 (1)<br /><br /> 否 (1)|是，一個層次。 層次於具現化時決定。<br /><br /> 是，一個層次。 層次於具現化時決定。|  
  
 從這個表中可以看見，唯讀的紋理檢視完全支援新功能，但會犧牲寫入檢視的功能。 可寫入的紋理檢視會有所限制，只能存取一個 Mipmap 層次。 讀寫紋理檢閱比可寫入檢閱更為特製化，因為前者加入了紋理檢閱的元素類型只有一個元件的需求。 請注意，可寫入紋理檢視不支援取樣，因為它是讀取導向的作業。  
  
### <a name="reading-from-texture-view-objects"></a>從紋理檢視物件讀取  
 除了紋理是以傳址的方式擷取，而紋理檢視是以傳值的方式擷取之外，透過紋理檢視讀取未取樣的紋理資料就像是從紋理本身讀取一樣。 下面兩個程式碼範例將進行示範，首先只使用 `texture`：  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {  
    tex_data.set(idx, int_2(1, 1));

 });

}  
```  
  
 以下是相同的範例，但現在是使用 `texture_view` 類別：  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {  
    tex_view.set(idx, int_2(1, 1));

 });

}  
```  
 若紋理檢視的元素是以浮點類型為基礎 (例如 float、float_2 或 float_4)，則也可以使用紋理取樣讀取，藉此利用硬體對於各種不同篩選模式和定址模式的支援。 C++ AMP 支援計算情節中最常用的兩種篩選模式，也就是點篩選 (最鄰近點) 和線性篩選 (加權平均)，以及四種定址模式，也就是包裝、鏡像、壓制和框線。 如需定址模式的詳細資訊，請參閱[address_mode 列舉](reference/concurrency-graphics-namespace-enums.md#address_mode)。  
  
 除了 C++ AMP 直接支援的模式之外，您還可以存取基礎平台的其他篩選模式和定址模式，方法是使用 Interop 應用程式開發介面採用直接使用平台應用程式開發介面建立的紋理取樣器。 例如，Direct3D 支援其他篩選模式 (例如，非等向性篩選)，而且可以對紋理的每個維度套用不同的定址模式。 您可以建立紋理取樣器並使用 Direct3D 應用程式開發介面垂直包裝、水平鏡像以及透過非等向性篩選取樣其座標，然後在 C++ AMP 程式碼中使用 `make_sampler` Interop 應用程式開發介面來運用取樣器。 如需詳細資訊，請參閱[c + + AMP 中的紋理取樣](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx)上平行程式設計機器碼部落格中。  
  
 紋理檢視也支援讀取 Mipmap。 因為具現化時所決定的 MIP 層級範圍可以動態取樣，同時也因為支援具有 1、2 或 4 個元件的元素，所以唯讀紋理檢視 (具有 const 元素類型) 可提供最大的彈性。 讀寫紋理檢視包含擁有一個元件的元素，這類檢視也支援 Mipmap，但只支援具現化時所決定的 Mipmap 層次。 如需詳細資訊，請參閱 <<c0> [ 具有 Mipmap 的紋理](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx)上平行程式設計機器碼部落格中。  
  
### <a name="writing-to-texture-view-objects"></a>寫入紋理檢視物件  
 使用[texture_view:: get 方法](reference/texture-view-class.md#get)寫入至基礎`texture`透過`texture_view`物件。 紋理檢視可以是唯讀、讀寫或唯寫。 若要使紋理檢視成為可寫入，該檢視必須具有非 const 的元素類型，而若要使紋理檢視成為可讀取和可寫入，其元素類型也必須只有一個元件。 否則，紋理檢視會是唯讀。 透過紋理檢視一次只能存取一個紋理的 Mipmap 層次，且該層次是在檢視具現化時指定。  
  
 這個範例將示範如何寫入擁有 4 個 Mipmap 層次之紋理的第二詳細 Mipmap 層次。 最詳細的 Mipmap 層次為層級 0。  
  
```  
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2  
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

 
// Create a writable texture view to the second mipmap level :4x4  
texture_view<int, 2> w_view(tex, 1);

 
parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)  
{  
    w_view.set(idx, 123);

});
```  
  
## <a name="interoperability"></a>互通性  

 C + + AMP 執行階段支援之間的互通性`texture<T,1>`和[ID3D11Texture1D 介面](http://go.microsoft.com/fwlink/p/?linkId=248503)之間`texture<T,2>`並[ID3D11Texture2D 介面](http://go.microsoft.com/fwlink/p/?linkId=255317)，和之間`texture<T,3>`而[ID3D11Texture3D 介面](http://go.microsoft.com/fwlink/p/?linkId=255377)。 [Get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture)方法會採用`texture`物件，然後傳回`IUnknown`介面。 [Make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture)方法會採用`IUnknown`介面並`accelerator_view`物件，然後傳回`texture`物件。  
  
## <a name="see-also"></a>另請參閱  
 [double_2 類別](../../parallel/amp/reference/double-2-class.md)   
 [double_3 類別](../../parallel/amp/reference/double-3-class.md)   
 [double_4 類別](../../parallel/amp/reference/double-4-class.md)   
 [float_2 類別](../../parallel/amp/reference/float-2-class.md)   
 [float_3 類別](../../parallel/amp/reference/float-3-class.md)   
 [float_4 類別](../../parallel/amp/reference/float-4-class.md)   
 [int_2 類別](../../parallel/amp/reference/int-2-class.md)   
 [int_3 類別](../../parallel/amp/reference/int-3-class.md)   
 [int_4 類別](../../parallel/amp/reference/int-4-class.md)   
 [norm_2 類別](../../parallel/amp/reference/norm-2-class.md)   
 [norm_3 類別](../../parallel/amp/reference/norm-3-class.md)   
 [norm_4 類別](../../parallel/amp/reference/norm-4-class.md)   
 [short_vector 結構](../../parallel/amp/reference/short-vector-structure.md)   
 [short_vector_traits 結構](../../parallel/amp/reference/short-vector-traits-structure.md)   
 [uint_2 類別](../../parallel/amp/reference/uint-2-class.md)   
 [uint_3 類別](../../parallel/amp/reference/uint-3-class.md)   
 [uint_4 類別](../../parallel/amp/reference/uint-4-class.md)   
 [unorm_2 類別](../../parallel/amp/reference/unorm-2-class.md)   
 [unorm_3 類別](../../parallel/amp/reference/unorm-3-class.md)   
 [unorm_4 類別](../../parallel/amp/reference/unorm-4-class.md)
