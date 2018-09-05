---
title: 如何： 使用 PInvoke 封送處理結構 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6719d7b104c5dd520a8c4e8a027ea47bd76a95bc
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689506"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>如何：使用 PInvoke 封送處理結構
本文件說明如何在原生函式會接受 C 樣式結構可以從呼叫 managed 函式，藉由使用 P/Invoke。 雖然我們建議您使用 c + + Interop 功能，而不是 P/Invoke P/Invoke 提供極少的編譯時期錯誤，報告，因為不是類型安全，並可能會非常繁瑣，若要實作，如果未受管理的 API 會封裝成 DLL，而且沒有原始程式碼可用，P/Invoke 是唯一的選項。 否則，請參閱下列文件：  
  
-   [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
  
-   [如何：使用 PInvoke 封送處理字串](../dotnet/how-to-marshal-strings-using-pinvoke.md)
  
 根據預設，原生和 managed 結構是配置以不同的方式在記憶體中，因此已成功跨 managed/unmanaged 界限傳遞結構需要額外的步驟，以保持資料完整性。  
  
 本文件說明定義原生結構，和如何產生的結構可以傳遞至 unmanaged 函式的 managed 對等項目所需的步驟。 本文件假設簡單結構 — 不會包含字串或指標，會使用。 非 blittable 互通性的相關資訊，請參閱[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。 P/Invoke 不能有非 blittable 類型做為傳回值。 Blittable 類型在 managed 和 unmanaged 程式碼中有相同表示法。 如需詳細資訊，請參閱 < [Blittable 和非 Blittable 類型](/dotnet/framework/interop/blittable-and-non-blittable-types)。  
  
 簡單封送處理，跨 managed/unmanaged 界限的 blittable 結構第一次需要受管理的版本，每個原生結構的定義。 這些結構可以具有任何合法的名稱;兩個的結構，其配置的資料以外的原生和 managed 版本之間沒有任何關聯性。 因此，它是不可或缺的受管理的版本包含相同的大小和順序與原生的版本相同的欄位。 （沒有任何機制可確保結構的 managed 和原生版本同等權限，因此不相容問題會變得明顯到執行階段。 它是程式設計人員必須負責確保兩個結構有相同的資料版面配置）。  
  
 因為基於效能目的有時重新排列的受管理的結構成員，就必須使用<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性來指出此結構依序配置。 它也是個不錯的主意，明確地設定 封裝設定所使用的原生結構相同的結構。 （根據預設，雖然 Visual c + + 使用這兩個受管理的程式碼封裝的 8 位元組結構）。  
  
1.  接下來，使用<xref:System.Runtime.InteropServices.DllImportAttribute>宣告對應至任何接受結構的 unmanaged 函式的進入點，但使用中的函式簽章中，這是就無傷大雅了點，如果您使用相同的名稱，這兩個版本的結構的 managed 的版本結構。  
  
2.  現在的 managed 程式碼可以 unmanaged 函式上傳遞結構的 managed 的版本就好像它們是實際的受管理的函式。 這些結構可以傳遞值或參考，如下列範例所示。  
  
## <a name="example"></a>範例  
 下列程式碼是由 unmanaged 和 managed 的模組所組成。 未受管理的模組是定義結構，其位置和呼叫可接受兩個位置結構執行個體 GetDistance 函式呼叫的 DLL。 第二個模組是受管理的命令列應用程式匯入 GetDistance 函式，但定義位置的 MLocation 結構的 managed 對等方面。 在實務上相同的名稱可能要用於兩個版本的結構;不過，不同的名稱也是此處用來示範 DllImport 原型以受管理的版本定義。  
  
 請注意沒有部分的 dll 會使用傳統的 managed 程式碼以 #include 指示詞。 事實上，DLL 會在執行階段存取，因此將不會在編譯時期偵測使用 DllImport 匯入的函式的問題。  
  
```  
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
  
```  
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
  
## <a name="see-also"></a>另請參閱  
 [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
