---
title: "_InterlockedCompareExchange128 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedCompareExchange128_cpp"
  - "_InterlockedCompareExchange128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cmpxchg16b 指令"
  - "_InterlockedCompareExchange128 內建"
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _InterlockedCompareExchange128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 執行 128 位元的連鎖的比較和交換。  
  
## 語法  
  
```  
unsigned char _InterlockedCompareExchange128(  
   __int64 volatile * Destination,  
   __int64 ExchangeHigh,  
   __int64 ExchangeLow,  
   __int64 * ComparandResult  
);  
```  
  
#### 參數  
 輸入 \[、 輸出\]`Destination`  
 為 128 位元欄位會被視為目的地，因為這是兩個 64 位元整數的陣列的指標。  目的資料必須是 16 位元組對齊，以避免一般保護性錯誤。  
  
 \[in\] `ExchangeHigh`  
 64 位元的整數可以交換高可為目的端。  
  
 \[in\] `ExchangeLow`  
 可能會與低部份目的地交換為 64 位元整數。  
  
 輸入 \[、 輸出\]`ComparandResult`  
 指標 \(128 位元欄位被視為\) 的兩個 64 位元整數的陣列，要與目的地進行比較。  在輸出時，這會覆寫目的端的原始值。  
  
## 傳回值  
 1 如果 128 位元 comparand 等於目的端的原始值。  `ExchangeHigh`與`ExchangeLow`覆寫 128 位元的目的地。  
  
 假如 comparand 未到達目的端的原始值 0。  目的端的值是不變，comparand 的值就會覆寫目的端的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_InterlockedCompareExchange128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建會產生 `cmpxchg16b`指令 \(與`lock`前置詞\) 進行 128 位元鎖定的比較和交換。  早期版本的 「 AMD 64 位元硬體不支援這個指令。  若要檢查是否有硬體支援`cmpxchg16b` 指令，請打`__cpuid`與內建`InfoType=0x00000001 (standard function 1)`。  位元 13 的`CPUInfo[2]` \(ECX\) 為 1，如果指令受支援。  
  
> [!NOTE]
>  值為`ComparandResult`一定會覆寫。  後`lock`指令時，此內建會立即將複製的初始值`Destination`到`ComparandResult`。  基於這個理由， `ComparandResult`和`Destination`應該指向不同的記憶體位置，以避免無法預期的行為。  
  
 雖然您可以使用`_InterlockedCompareExchange128`低層級的執行緒同步處理，您不需要同步處理超過 128 位元，如果您可以使用較小的同步處理函式 \(例如另`_InterlockedCompareExchange`內建函式\) 相反。  使用`_InterlockedCompareExchange128`如果您想要在記憶體中為 128 位元值不可部分完成的存取。  
  
 如果您執行的程式碼會使用此內建不支援的硬體上`cmpxchg16b`指令時，結果會發生無法預期。  
  
 使用僅當做內建這個常式。  
  
## 範例  
 這個範例會使用`_InterlockedCompareExchange128`高兩個 64 位元整數的陣列中的文字取代它的高、 低字組的總和，並以逐步遞增低位文字。  BigInt.Int 陣列存取是不可部分完成，但本範例使用單一執行緒，並會略過鎖定為了簡單起見。  
  
```  
// cmpxchg16b.c  
// processor: x64  
// compile with: /EHsc /O2  
#include <stdio.h>  
#include <intrin.h>  
  
typedef struct _LARGE_INTEGER_128 {  
    __int64 Int[2];  
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;  
  
volatile LARGE_INTEGER_128 BigInt;  
  
// This AtomicOp() function atomically performs:  
//   BigInt.Int[1] += BigInt.Int[0]  
//   BigInt.Int[0] += 1  
void AtomicOp ()  
{  
    LARGE_INTEGER_128 Comparand;  
    Comparand.Int[0] = BigInt.Int[0];  
    Comparand.Int[1] = BigInt.Int[1];  
    do {  
        ; // nothing  
    } while (_InterlockedCompareExchange128(BigInt.Int,  
                                            Comparand.Int[0] + Comparand.Int[1],  
                                            Comparand.Int[0] + 1,  
                                            Comparand.Int) == 0);  
}  
  
// In a real application, several threads contend for the value  
// of BigInt.  
// Here we focus on the compare and exchange for simplicity.  
int main(void)  
{  
   BigInt.Int[1] = 23;  
   BigInt.Int[0] = 11;  
   AtomicOp();  
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",  
      BigInt.Int[1],BigInt.Int[0]);  
}  
```  
  
  **BigInt.Int\[1\] \= 34，BigInt.Int\[0\] \= 12**   
## 結束 Microsoft 特定  
 藉由收益進階微裝置，及版權 2007年.人所有之商標。  重製與收益進階微裝置，及來自的使用權限.  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_InterlockedCompareExchange 內建函式](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)