---
title: 如何：使用 C++ Interop 封送處理結構
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: a77745c9a60c9759f8b3b2df91bcbc4cb507533b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988176"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>如何：使用 C++ Interop 封送處理結構

本主題示範視覺化C++互通性的一個 facet。 如需詳細資訊，請參閱[使用C++ Interop （隱含 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

下列程式碼範例會使用[managed、非](../preprocessor/managed-unmanaged.md)受控 #pragma 指示詞，在同一個檔案中執行 managed 和非受控函式，但如果在個別的檔案中定義，則這些函式會以相同的方式進行交互作用。 僅包含非受控函式的檔案不需要使用[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)進行編譯。

## <a name="example"></a>範例

下列範例示範如何將結構從 managed 傳遞至非受控函式，方法是透過值和傳址方式。 因為此範例中的結構只包含簡單的內建資料類型（請參閱全選[和非全像的類型](/dotnet/framework/interop/blittable-and-non-blittable-types)），所以不需要特殊的封送處理。 若要封送處理非類型的結構（例如包含指標的結構），請參閱[如何：使用C++ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。

```cpp
// PassStruct1.cpp
// compile with: /clr

#include <stdio.h>
#include <math.h>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

struct Location {
   int x;
   int y;
};

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

#pragma managed

int main() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   Location loc3;
   InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

## <a name="example"></a>範例

下列範例示範如何將結構從非受控函式傳遞至 managed 函數，方法是以傳值和傳址方式。 因為此範例中的結構只包含簡單的內建資料類型（請參閱全選[和非全像的類型](/dotnet/framework/interop/blittable-and-non-blittable-types)），所以不需要進行任何特殊的封送處理。 若要封送處理非類型的結構（例如包含指標的結構），請參閱[如何：使用C++ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。

```cpp
// PassStruct2.cpp
// compile with: /clr
#include <stdio.h>
#include <math.h>
using namespace System;

// native structure definition
struct Location {
   int x;
   int y;
};

#pragma managed

double GetDistance(Location loc1, Location loc2) {
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   Console::WriteLine("[managed] Initializing location...");
   lp->x = 50;
   lp->y = 50;
}

#pragma unmanaged

int UnmanagedFunc() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);

   double dist = GetDistance(loc1, loc2);
   printf_s("[unmanaged] distance = %f\n", dist);

   Location loc3;
   InitLocation(&loc3);
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);

    return 0;
}

#pragma managed

int main() {
   UnmanagedFunc();
}
```

## <a name="see-also"></a>請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
