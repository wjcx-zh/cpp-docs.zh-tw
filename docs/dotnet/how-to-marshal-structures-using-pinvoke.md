---
title: 如何：使用 PInvoke 封送處理結構
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: fe5d2cf4804baea286827e9d5e270c10cd587b30
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988448"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>如何：使用 PInvoke 封送處理結構

本檔說明如何使用 P/Invoke，從 managed 函數呼叫接受 C 樣式結構的原生函式。 雖然我們建議您使用C++ Interop 功能，而不是 p/invoke，因為 p/invoke 提供的編譯階段錯誤報表很少，而且不是型別安全的，而且如果未受管理的 API 封裝為 DLL，而且沒有可用的原始程式碼，則 p/invoke 是唯一的選項。 否則，請參閱下列檔：

- [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [如何：使用 PInvoke 封送處理字串](../dotnet/how-to-marshal-strings-using-pinvoke.md)

根據預設，原生和受控結構在記憶體中會以不同的方式配置，因此在受控/非受控界限之間成功傳遞結構需要額外的步驟來保留資料完整性。

本檔說明定義原生結構的受控對等專案所需的步驟，以及如何將產生的結構傳遞至未受管理的函式。 本檔假設使用簡單的結構（不包含字串或指標）。 如需非可直接進行互通性的詳細資訊，請參閱[使用C++ Interop （隱含 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。 P/Invoke 不能有非可安裝類型做為傳回值。 在受控和非受控程式碼中，以可集中式的類型具有相同的表示。 如需詳細資訊，請參閱全像[型別和非直接類型](/dotnet/framework/interop/blittable-and-non-blittable-types)。

先封送處理受控/非受控界限之間的簡單、可直接複製結構，需要定義每個原生結構的 managed 版本。 這些結構可以有任何合法的名稱;除了其資料配置以外，這兩個結構的原生和 managed 版本之間沒有任何關聯性。 因此，受控版本所包含的欄位大小和原生版本的順序相同，這是很重要的。 （沒有任何機制可確保結構的 managed 和原生版本相等，因此在執行時間之前，不會有明顯的不相容性。 程式設計人員必須負責確保這兩個結構具有相同的資料配置。）

因為 managed 結構的成員有時會基於效能考慮而重新排列，所以必須使用 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來表示結構是依序排列。 將結構封裝設定明確設定為與原生結構所使用的相同，也是個不錯的主意。 （雖然根據預設，Visual C++會針對這兩個 managed 程式碼使用8個位元組的結構封裝）。

1. 接下來，使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 來宣告對應至任何接受結構之非受控函式的進入點，但在函式簽章中使用 managed 版本的結構，如果您針對這兩個版本的結構使用相同的名稱，這就是想法的點。

1. 現在 managed 程式碼可以將結構的 managed 版本傳遞給非受控函式，就好像它們實際上是 managed 函式一樣。 這些結構可以透過值或傳址方式傳遞，如下列範例所示。

## <a name="example"></a>範例

下列程式碼是由不受管理的和受控模組所組成。 非受控模組是定義名為 Location 之結構的 DLL，以及可接受位置結構之兩個實例的函式，稱為 GetDistance。 第二個模組是受管理的命令列應用程式，它會匯入 GetDistance 函式，但會根據位置結構（MLocation）的受控對等來定義它。 實際上，相同的名稱可能會用於這兩個版本的結構。不過，這裡使用不同的名稱來示範 DllImport 原型是以受控版本來定義。

請注意，使用傳統的 #include 指示詞，不會對 managed 程式碼公開 DLL 的任何部分。 事實上，DLL 只會在執行時間存取，因此在編譯時期不會偵測到以 DllImport 匯入之函式的問題。

```cpp
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}
```

## <a name="example"></a>範例

```cpp
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

```Output
[unmanaged] loc1(0,0) loc2(100,100)
[managed] distance = 141.42135623731
[unmanaged] Initializing location...
[managed] x=50 y=50
```

## <a name="see-also"></a>請參閱

[在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
