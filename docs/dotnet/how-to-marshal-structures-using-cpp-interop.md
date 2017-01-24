---
title: "如何：使用 C++ Interop 封送處理結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Interop, 結構"
  - "資料封送處理 [C++], 結構"
  - "Interop [C++], 結構"
  - "封送處理 [C++], 結構"
  - "結構 [C++], 封送處理"
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ Interop 封送處理結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題將示範 Visual C\+\+ 互通性的一個 Facet。  如需詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 在下列範例中，程式碼會使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指示詞，在相同的檔案中實作 Managed 和 Unmanaged 函式，這些函式即使在不同的檔案中定義，也會以相同的方式互相溝通。  只包含 Unmanaged 函式的檔案，不需要以 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 編譯。  
  
## 範例  
 下列程式碼範例會示範以傳值 \(By Value\) 和傳址 \(By Reference\) 的方式，從 Managed 函式將結構傳遞至 Unmanaged 函式。  因為這個範例中的結構只包含簡單的內建型別 \(請參閱[Blittable 和非 Blittable 類型](../Topic/Blittable%20and%20Non-Blittable%20Types.md)\)，所以不需要特別的封送處理 \(Marshaling\)。  若要封送處理非 Blittable 結構，例如包含指標的結構，請參閱 [如何：使用 C\+\+ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
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
  
## 範例  
 下列程式碼範例會示範以傳值和傳址的方式，從 Unmanaged 函式將結構傳遞至 Managed 函式。  因為這個範例中的結構只包含簡單的內建型別 \(請參閱[Blittable 和非 Blittable 類型](../Topic/Blittable%20and%20Non-Blittable%20Types.md)\)，所以不需要特別的封送處理。  若要封送處理非 Blittable 結構，例如包含指標的結構，請參閱 [如何：使用 C\+\+ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
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
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)