---
title: "align (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "align"
  - "align_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], align"
  - "align __declspec 關鍵字"
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# align (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual Studio 2015 和更新版本中，使用 C\+\+11 Standard `alignas` 規範來控制對齊方式。  如需詳細資訊，請參閱[對齊方式](../cpp/alignment-cpp-declarations.md)。  
  
 **Microsoft 特定的**  
  
 使用 `__declspec(align(#))` 可精確控制使用者定義資料的對齊 \(例如，靜態配置或函式中的自動資料\)。  
  
## 語法  
  
```  
__declspec( align( # ) ) declarator  
```  
  
## 備註  
 撰寫使用最新處理器指令的應用程式會帶來一些新的限制和問題。  特別是許多新的指令要求資料必須對齊 16 位元組界限。  此外，將常用資料對齊特定處理器的快取行大小就能改善快取效能。  例如，如果您定義的結構大小小於 32 個位元組，您可能要將它對齊 32 個位元組，以確保有效率地快取該結構類型的物件。  
  
 \# 是對齊值。  有效項目是從 1 至 8192 \(位元組\) 的 2 乘冪整數，例如 2、4、8、16、32 或 64。  `declarator` 是您宣告為已對齊的資料。  
  
 如需如何傳回 `size_t` 類型值 \(這是類型的對齊需求\) 的資訊，請參閱 [\_\_alignof](../cpp/alignof-operator.md)。  如需以 64 位元處理器為目標時，如何宣告未對齊的指標，請參閱 [\_\_unaligned](../cpp/unaligned.md)。  
  
 當您定義 `__declspec(align(#))`、`struct` 或 `union`，或是宣告變數時，可以使用 `class`。  
  
 編譯器不會在複製或資料轉換作業期間，保證或嘗試保留資料的對齊屬性。  例如，[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 可以複製以 `__declspec(align(#))` 宣告的結構至任何位置。  請注意，一般配置器像是 [malloc](../c-runtime-library/reference/malloc.md)、C\+\+ [new 運算子](../Topic/operator%20new%20\(%3Cnew%3E\).md) 和 Win32 配置器，都會傳回記憶體，此記憶體對於 `__declspec(align(#))` 結構或結構陣列通常未充分對齊。  若要保證複製或資料轉換作業的目的地有正確對齊，請使用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md)，或撰寫您自己的配置器。  
  
 您無法為函式參數指定對齊。  有對齊屬性的資料，以值傳遞到堆疊上時，其對齊會由呼叫慣例控制。  如果資料對齊在呼叫的函式中很重要，請將參數複製到正確對齊的記憶體中，才使用該參數。  
  
 沒有 `__declspec(align(#))` 時，Visual C\+\+ 通常會根據目標處理器和資料大小，將資料對齊自然界限，最多 32 位元處理器上的 4 位元組界限和 64 位元處理器上的 8 位元組界限。  類別或結構中的資料，是以其最小自然對齊和目前封裝設定 \(從 \#pragma `pack` 或 **\/Zp** 編譯器選項\)，在類別或結構內對齊。  
  
 這個範例會示範 `__declspec(align(#))` 的使用方式。  
  
```  
__declspec(align(32)) struct Str1{  
   int a, b, c, d, e;  
};  
```  
  
 這個類型現在具有 32 位元組對齊屬性。  這表示所有的靜態和自動執行個體會開始於 32 位元組的界限。  以這個類型宣告為成員的其他結構類型會保留這個類型的對齊屬性，也就是任何具有做為項目之 `Str1` 的結構都會有至少為 32 的對齊屬性。  
  
 請注意，`sizeof(struct Str1)` 等於 32。  這意味著如果建立 Str1 物件的陣列，且陣列的基底是對齊 32 位元組，則陣列的每個成員也會對齊 32 位元組。  若要在動態記憶體中建立基底正確對齊的陣列，請使用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或撰寫您自己的配置器。  
  
 任何結構的 `sizeof` 值都是最後一個成員的位移，加上該成員的大小，然後捨入至最大成員對齊值或整個結構對齊值 \(以較大者為準\) 的最接近倍數。  
  
 編譯器會為結構對齊使用這些規則：  
  
-   除非以 `__declspec(align(#))` 覆寫，否則純量結構成員的對齊是其大小與目前封裝的最小值。  
  
-   除非以 `__declspec(align(#))` 覆寫，否則結構的對齊是其成員的個別對齊最大值。  
  
-   結構成員位於其父結構開始處的位移，這是其對齊 \(大於或等於上一個成員結尾的位移\) 的最小倍數。  
  
-   結構的大小是其對齊的最小倍數 \(大於或等於其最後一個成員結尾的位移\)。  
  
 `__declspec(align(#))` 只能增加對齊限制。  
  
 如需詳細資訊，請參閱:  
  
-   [align 範例](#vclrfalignexamples)  
  
-   [使用 \_\_declspec\(align\(\#\)\) 定義新類型](#vclrf_declspecaligntypedef)  
  
-   [對齊執行緒區域儲存區中的資料](#vclrfthreadlocalstorageallocation)  
  
-   [align 如何搭配資料封裝使用](#vclrfhowalignworkswithdatapacking)  
  
-   [結構對齊範例](../build/examples-of-structure-alignment.md) \(x64 專用\)  
  
##  <a name="vclrfalignexamples"></a> align 範例  
 下列範例說明 `__declspec(align(#))` 如何影響資料結構的大小和對齊。  這個範例會假設下列定義：  
  
```  
#define CACHE_LINE  32  
#define CACHE_ALIGN __declspec(align(CACHE_LINE))  
```  
  
 在這個範例中，`S1` 結構使用 `__declspec(align(32))` 定義。  針對變數定義使用的所有 `S1`，或其他類型宣告中，都是對齊 32 位元組。  `sizeof(struct S1)` 會傳回 32，而且 `S1` 在保留四個整數所需的 16 個位元組後面會有 16 個填補位元組。  每個 `int` 成員需要 4 位元組對齊，但是結構本身的對齊是宣告為 32。  因此，整體對齊是 32。  
  
```  
struct CACHE_ALIGN S1 { // cache align all instances of S1  
   int a, b, c, d;  
};  
struct S1 s1;   // s1 is 32-byte cache aligned  
```  
  
 在下列範例中，`sizeof(struct S2)` 會傳回 16，也就是成員大小的總和，因為這剛好是最大對齊需求的倍數 \(8 倍\)。  
  
```  
__declspec(align(8)) struct S2 {  
   int a, b, c, d;  
};  
```  
  
 在下列範例中，`sizeof(struct S3)` 會傳回 64。  
  
```  
struct S3 {  
   struct S1 s1;   // S3 inherits cache alignment requirement  
                  // from S1 declaration  
   int a;         // a is now cache aligned because of s1  
                  // 28 bytes of trailing padding  
};  
```  
  
 在這個範例中，請注意 `a` 有其自然類型的對齊，在此情況下，為 4 個位元組。  不過，`S1` 必須對齊 32 位元組。  `a` 後面接著二十八個位元組的填補，因此 `s1` 會在位移 32 處起始。  `S4` 接著會繼承 `S1` 的對齊需求，因為這是結構中最大的對齊需求。  `sizeof(struct S4)` 會傳回 64。  
  
```  
struct S4 {  
   int a;  
   // 28 bytes padding  
    struct S1 s1;      // S4 inherits cache alignment requirement of S1  
};  
```  
  
 下列三個變數宣告也會使用 `__declspec(align(#))`。  在每個案例中，變數必須對齊 32 位元組。  若是陣列，陣列的基底位址 \(而非每個陣列成員\) 對齊 32 位元組。  每個陣列成員的 `sizeof` 值不會因為使用 `__declspec(align(#))` 而受影響。  
  
```  
CACHE_ALIGN int i;  
CACHE_ALIGN int array[128];  
CACHE_ALIGN struct s2 s;  
```  
  
 若要對齊陣列的每個成員，應使用如下的程式碼：  
  
```  
typedef CACHE_ALIGN struct { int a; } S5;  
S5 array[10];  
```  
  
 在這個範例中，請注意對齊結構本身和對齊第一個元素都有相同的效果：  
  
```  
CACHE_ALIGN struct S6 {  
   int a;  
   int b;  
};  
  
struct S7 {  
   CACHE_ALIGN int a;  
               int b;  
};  
```  
  
 `S6` 和 `S7` 具有相同的對齊、配置和大小特性。  
  
 在下列範例中，a、b、c 和 d 的對齊開始位址分別為 4、1、4 和 1。  
  
```  
void fn() {   
   int a;  
   char b;  
   long c;  
   char d[10]  
}   
```  
  
 如果已在堆積上配置記憶體，則對齊會取決於所呼叫的配置函式。  例如，如果您使用 `malloc`，則結果會取決於運算元大小。  如果 *arg* \>\= 8，則傳回的記憶體是對齊 8 位元組。  如果 *arg* \< 8，則傳回的記憶體其對齊會是小於 *arg* 之 2 的一次乘冪。  例如，如果您使用 malloc\(7\)，則對齊是 4 個位元組。  
  
##  <a name="vclrf_declspecaligntypedef"></a> 使用 \_\_declspec\(align\(\#\)\) 定義新類型  
 您可以定義具有對齊特性的類型。  
  
 例如，您可以使用對齊值以此方式定義 `struct` ：  
  
```  
struct aType {int a; int b;};  
typedef __declspec(align(32)) struct aType bType;  
```  
  
 現在，`aType` 和 `bType` 具有相同大小 \(8 個位元組\)，但是 `bType` 類型的變數將會對齊 32 位元組。  
  
##  <a name="vclrfthreadlocalstorageallocation"></a> 對齊執行緒區域儲存區中的資料  
 使用 `__declspec(thread)` 屬性建立並放入影像之 TLS 區段的靜態執行緒區域儲存區 \(TLS\) 可用於對齊，就像一般靜態資料一樣。  為了建立 TLS 資料，作業系統會配置記憶體的 TLS 區段大小，並接受 TLS 區段對齊屬性。  
  
 此範例示範各種將對齊的資料放入執行緒區域儲存區中的方式。  
  
```  
// put an aligned integer in TLS  
__declspec(thread) __declspec(align(32)) int a;     
  
// define an aligned structure and put a variable of the struct type  
// into TLS  
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;  
  
// create an aligned structure   
struct CACHE_ALIGN S9 {  
   int a;  
   int b;  
};  
// put a variable of the structure type into TLS  
__declspec(thread) struct S9 a;  
```  
  
##  <a name="vclrfhowalignworkswithdatapacking"></a> align 如何搭配資料封裝使用  
 **\/Zp** 編譯器選項和 `pack` pragma 有封裝結構及等位成員資料的作用。  此範例示範 **\/Zp** 和 `__declspec(align(#))` 如何搭配使用：  
  
```  
struct S {  
   char a;  
   short b;  
   double c;  
   CACHE_ALIGN double d;  
   char e;  
   double f;  
};  
```  
  
 下表列出每個成員在各種 **\/Zp** \(或 \#pragma `pack`\) 值之下的位移，顯示兩者之間的互動情況。  
  
|變數|\/Zp1|\/Zp2|\/Zp4|\/Zp8|  
|--------|-----------|-----------|-----------|-----------|  
|a|0|0|0|0|  
|b|1|2|2|2|  
|c|3|4|4|8|  
|d|32|32|32|32|  
|e|40|40|40|40|  
|f|41|42|44|48|  
|sizeof\(S\)|64|64|64|64|  
  
 如需詳細資訊，請參閱 [\/Zp \(結構成員對齊\)](../build/reference/zp-struct-member-alignment.md)。  
  
 因此，物件的位移是根據前一個物件的位移與目前封裝設定，但如果物件具有 `__declspec(align(#))` 屬性，情況就不是這樣，此時對齊是根據前一個物件的位移與物件的 `__declspec(align(#))` 值。  
  
### END Microsoft 特定的  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [ARM ABI 慣例概觀](../build/overview-of-arm-abi-conventions.md)   
 [x64 呼叫慣例概觀](../build/overview-of-x64-calling-conventions.md)