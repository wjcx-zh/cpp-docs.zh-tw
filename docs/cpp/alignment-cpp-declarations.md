---
title: "對齊方式 (C++ 宣告) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 對齊方式 (C++ 宣告)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 的其中一項低階功能可指定記憶體中物件的精確對齊方式，以充份利用特定的硬體架構。  根據預設，編譯器會根據大小值來對齊類別和結構成員：bool 和 char 對齊一個位元組的界限、short 對齊兩個位元組、int 對齊四個位元組，long long、double 和 long double 對齊八個位元組。  在大多數情況下，您永遠不必擔心對齊方式，因為預設已經為最佳對齊方式。  不過在某些情況下，您可以藉由指定資料結構的自訂對齊方式，達到顯著的效能改善或節省記憶體空間。  在 Visual Studio 2015 之前，可以使用 Microsoft 專有關鍵字 \_\_alignof 和 declspec\(alignas\) 來指定大於預設值的對齊方式。  從 Visual Studio 2015 開始，您應該使用 C\+\+11 標準關鍵字 [alignof 和 alignas](../cpp/alignof-and-alignas-cpp.md) 以達到最大的程式碼可攜性。  實際上，新關鍵字的行為與 Microsoft 專有擴充功能相同，且針對這些擴充功能的文件也適用於新的關鍵字。  如需詳細資訊，請參閱 [\_\_alignof 運算子](../cpp/alignof-operator.md)和 [align](../cpp/align-cpp.md)。  C\+\+ 標準不會指定對齊界限小於目標平台編譯器預設值的封裝行為，因此在此情況下您仍需要使用 Microsoft \#pragma [pack](../preprocessor/pack.md)。  
  
 C\+\+ 標準程式庫提供 [aligned\_storage 類別](../standard-library/aligned-storage-class.md)來針對具有自訂對齊的資料結構配置記憶體，並提供 [aligned\_union 類別](../standard-library/aligned-union-class.md)來指定具有非一般建構函式或解構函式之等位的對齊方式。  
  
## 關於對齊方式  
 對齊是記憶體位址的屬性，以數字位址取 2 乘冪的模數來表示。  例如，位址 0x0001103F 取 4 的模數是 3；該位址便稱為對齊 4n\+3，其中 4 表示所選的 2 乘冪。  位址的對齊方式取決於所選的 2 乘冪。  相同位址取 8 的模數為 7。  如果位址的對齊方式為 Xn\+0，則稱為對齊 X。  
  
 CPU 會執行對記憶體中所儲存資料進行操作的指令，而資料是以其在記憶體中的位址來識別。  除了其位址之外，資料也有大小。  如果其位址對齊其大小，則稱資料為自然對齊，反之則否。  例如，如果用來識別 8 位元組浮點數資料的位址對齊 8，則此 8 位元組浮點數資料便是自然對齊。  
  
 處理資料 alignmentDevice 編譯器的編譯器會嘗試以避免資料不對齊的方式配置資料。  
  
 針對簡單的資料類型，編譯器指派的位址會是以位元組為單位之資料類型大小的倍數。  因此，編譯器會將位址指派給類型為 long 且為 4 的倍數之變數，並將位址的最底部兩個位元設為零。  
  
 此外，編譯器也會以自然對齊結構之每個項目的方式來填補結構。  請考量下列程式碼範例中的結構 struct x\_。  
  
```  
struct x_  
{  
   char a;     // 1 byte  
   int b;      // 4 bytes  
   short c;    // 2 bytes  
   char d;     // 1 byte  
} MyStruct;  
  
```  
  
 編譯器會填補這個結構，以便強制執行自然對齊。  
  
 下列程式碼範例會示範編譯器如何將填補好的結構放在 memory:Copy 中  
  
```  
// Shows the actual memory layout  
struct x_  
{  
   char a;            // 1 byte  
   char _pad0[3];     // padding to put 'b' on 4-byte boundary  
   int b;            // 4 bytes  
   short c;          // 2 bytes  
   char d;           // 1 byte  
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4  
}  
  
```  
  
1.  兩個宣告都傳回 12 個位元組的 sizeof\(struct x\_\)。  
  
2.  第二個宣告包含兩個填補項目：  
  
3.  char \_pad0 \[3\] 可在四個位元組的界限上對齊 int b 成員  
  
4.  char \_pad1 \[1\] 可對齊結構 struct \_x bar\[3\] 的陣列項目；  
  
5.  填補會以允許自然存取的方式對齊 bar\[3\] 的項目。  
  
 下列程式碼範例將顯示 bar\[3\] 陣列配置：  
  
```  
adr offset   element  
------   -------  
0x0000   char a;         // bar[0]  
0x0001   char pad0[3];  
0x0004   int b;  
0x0008   short c;  
0x000a   char d;  
0x000b   char _pad1[1];  
  
0x000c   char a;         // bar[1]  
0x000d   char _pad0[3];  
0x0010   int b;  
0x0014   short c;  
0x0016   char d;  
0x0017   char _pad1[1];  
  
0x0018   char a;         // bar[2]  
0x0019   char _pad0[3];  
0x001c   int b;  
0x0020   short c;  
0x0022   char d;  
0x0023   char _pad1[1];  
  
```  
  
## 請參閱  
 [資料結構對齊方式](http://en.wikipedia.org/wiki/Data_structure_alignment)