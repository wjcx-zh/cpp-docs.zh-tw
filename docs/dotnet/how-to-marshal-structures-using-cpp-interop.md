---
title: HOW TO：封送處理結構使用C++Interop
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: 93aeabc3fe984bee8a9281281320d61dccd182bf
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345704"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>HOW TO：封送處理結構使用C++Interop

本主題將示範一個 facet 視覺效果的C++互通性。 如需詳細資訊，請參閱 <<c0> [ 使用C++Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。</c0>

下列程式碼範例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指示詞來實作 managed 和 unmanaged 函式在相同的檔案，但如果在不同的檔案中定義這些函式交互操作方式相同。 包含 unmanaged 的函式的檔案不需要進行編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會示範將傳遞結構從 managed 至 unmanaged 函式，值和傳址。 因為此範例中的結構包含只是簡單、 內建資料型別 (請參閱[Blittable 和非 Blittable 類型](/dotnet/framework/interop/blittable-and-non-blittable-types))，沒有特殊的封送處理為必要。 若要封送處理非 blittable 結構，例如那些包含指標，請參閱[How to:封送處理內嵌指標使用C++Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。

```
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

下列範例示範傳遞結構從 unmanaged，受管理的函式值和傳址。 因為此範例中的結構包含只是簡單、 內建資料型別 (請參閱[Blittable 和非 Blittable 類型](/dotnet/framework/interop/blittable-and-non-blittable-types))，沒有特殊的封送處理為必要。 若要封送處理非 blittable 結構，例如那些包含指標，請參閱[How to:封送處理內嵌指標使用C++Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。

```
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

## <a name="see-also"></a>另請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
