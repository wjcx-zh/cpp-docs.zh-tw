---
title: "如何：使用 PInvoke 封送處理結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料封送處理 [C++], 結構"
  - "Interop [C++], 結構"
  - "封送處理 [C++], 結構"
  - "平台叫用 [C++], 結構"
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# 如何：使用 PInvoke 封送處理結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文件將說明如何使用 P\/Invoke，從提供 <xref:System.String> 執行個體的 Managed 函式來呼叫接受 C\-Style 字串的原生函式。  雖然通常建議您使用 C\+\+ Interop 功能而不是 P\/Invoke \(因為 P\/Invoke 只提供很少的編譯時期錯誤報告、不具型別安全，且實作繁瑣\)，但如果 Unmanaged API 是封裝成 DLL，而且沒有原始程式碼可用，則 P\/Invoke 是唯一選擇。  否則請參閱下列文件：  
  
-   [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [How to: Marshal Structures Using PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
 根據預設，原生和 Managed 結構是以不同的方式配置在記憶體中，因此，若要順利將結構傳遞過 Managed\/Unmanaged 的界限，必須執行額外的步驟以保持資料完整性。  
  
 本文件將說明定義原生結構的 Managed 對應項所需的步驟，以及如何將產生的結構傳遞至 Unmanaged 函式。  這份文件假設使用簡單的結構，即不包含字串或指標的結構。  如需非 Blittable 互通性的詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  P\/Invoke 不能以非 Blittable 型別做為傳回值。  在 Managed 和 Unmanaged 程式碼中，Blittable 型別具有相同的表示法。  如需詳細資訊，請參閱[Blittable 和非 Blittable 類型](../Topic/Blittable%20and%20Non-Blittable%20Types.md)。  
  
 若要在 Managed\/Unmanaged 界限之間封送處理 \(Marshaling\) 簡單的 Blittable 結構，每一個原生結構的 Managed 版本都必須先行定義。  這些結構可以具有任何合法的名稱；除了資料配置之外，這兩個結構的原生和 Managed 版本並沒有任何關聯性 \(Relationship\)。  因此，Managed 版本所包含欄位的大小和順序，都必須與原生版本中的欄位相同，這一點非常重要的\(由於沒有機制能夠確保結構的 Managed 和原生版本完全相等，因此到了執行階段，不相容的情形會變得很明顯。  程式設計人員必須負責確保兩個結構具有相同的資料配置\)。  
  
 由於 Managed 結構的成員有時會為了效能而重新整理，因此，這時候必須使用 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性，以指示結構是循序配置的。  明確地將結構封裝 \(Packing\) 設定設為與原生結構所使用的設定相同，也是不錯的做法\(雖然 Visual C\+\+ 預設會在這兩種 Managed 程式碼中使用 8 個位元組結構封裝\)。  
  
1.  接下來，請使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 宣告對應到接受此結構之任何 Unmanaged 函式的進入點 \(Entry Point\)，但在函式簽章 \(Signature\) 中，請使用此結構的 Managed 版本，因為如果此結構的兩種版本都使用相同的名稱，就會是假設 \(Moot\) 點。  
  
2.  現在，Managed 程式碼可以將結構的 Managed 版本當做真的 Managed 函式一般，傳遞到 Unmanaged 函式。  這些結構可以利用傳值 \(By Value\) 或傳址 \(By Reference\) 的方式傳遞，如下列範例所示。  
  
## 範例  
 下列程式碼由 Unmanaged 和 Managed 的模組所組成。  Unmanaged 模組是一個 DLL，定義了名為 Location 的結構和名為 GetDistance 的函式，該函式會接受 Location 結構的兩個執行個體。  第二個模組是 Managed 命令列應用程式，它會匯入 GetDistance 函式，但是會依照 Location 結構的 Managed 對等項 \(MLocation\) 來定義該函式。  實際上，結構的兩個版本可能會使用同一個名稱；但是，在這裡使用不同的名稱，以示範依 Managed 版本定義 DllImport 原型 \(Prototype\)。  
  
 Managed 模組是使用 \/clr 編譯的，但是 \/clr:pure 也一樣可以執行。  
  
 請注意，DLL 的任何部分不會都公開給使用傳統 \#include 指示詞的 Managed 程式碼。  事實上 DLL 只會在執行階段存取，因此，如果以 DllImport 匯入的函式發生問題，在編譯時期並不會偵測出來。  
  
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
  
## 範例  
  
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
  
  **\[unmanaged\] loc1\(0,0\) loc2\(100,100\)**  
**\[managed\] distance \= 141.42135623731**  
**\[unmanaged\] 正在初始化 location...**  
**\[managed\] x\=50 y\=50**   
## 請參閱  
 [在 C\+\+ 中使用明確的 PInvoke \(DllImport 屬性\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)