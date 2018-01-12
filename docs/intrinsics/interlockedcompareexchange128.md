---
title: "_InterlockedCompareExchange128 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
dev_langs: C++
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0cbf4e29e02670b4532a4be82864cf3cf040df73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128
**Microsoft 特定的**  
  
 執行 128 位元連鎖的比較和交換。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned char _InterlockedCompareExchange128(  
   __int64 volatile * Destination,  
   __int64 ExchangeHigh,  
   __int64 ExchangeLow,  
   __int64 * ComparandResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in、out] `Destination`  
 目的地，也就是兩個 64 位元整數的陣列指標會視為 128 位元欄位。 目的地資料必須是 16 位元組對齊，以避免一般性保護錯誤。  
  
 [輸入] `ExchangeHigh`  
 可能會與目的地的較高部份交換 64 位元整數。  
  
 [輸入] `ExchangeLow`  
 可能會與目的地的較低部份交換 64 位元整數。  
  
 [in、out] `ComparandResult`  
 （被視為與 128 位元欄位） 的兩個 64 位元整數的陣列指標要與目的地比較。  在輸出時，這會覆寫目的地的原始值。  
  
## <a name="return-value"></a>傳回值  
 1，表示 128 位元比較元等於目的端的原始值。 `ExchangeHigh`和`ExchangeLow`覆寫 128 位元的目的地。  
  
 如果目的地的原始值不等於比較元是 0。 目的地的值不變，並比較元的值會覆寫目的地的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_InterlockedCompareExchange128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建函式會產生`cmpxchg16b`指示 (使用`lock`前置詞) 來執行的 128 位元鎖定的比較和交換。 AMD 64 位元硬體的早期版本不支援此指示。 若要檢查是否有硬體支援`cmpxchg16b`指示，請呼叫`__cpuid`與內建`InfoType=0x00000001 (standard function 1)`。 位元 13 的`CPUInfo[2]`(ECX) 為 1，指示是否支援。  
  
> [!NOTE]
>  值`ComparandResult`一定會覆寫。 之後`lock`指令時，此內建物件會立即將複製的初始值`Destination`至`ComparandResult`。 基於這個理由，`ComparandResult`和`Destination`應該指向不同的記憶體位置，以避免非預期的行為。  
  
 雖然您可以使用`_InterlockedCompareExchange128`針對低層級執行緒同步處理，您不需要同步處理超過 128 位元，如果您可以使用較小的同步處理函式 (例如另`_InterlockedCompareExchange`內建函式) 而。 使用`_InterlockedCompareExchange128`如果您想要在記憶體中的 128 位元值不可部分完成的存取。  
  
 如果您執行程式碼會使用此內建物件不支援的硬體上`cmpxchg16b`指令，結果會產生無法預測。  
  
 這個常式可只做為內建函式。  
  
## <a name="example"></a>範例  
 這個範例會使用`_InterlockedCompareExchange128`高的兩個 64 位元整數陣列的文字取代其高低字的總和，並遞增低的字。 存取 BigInt.Int 陣列是不可部分完成，但此範例會使用單一執行緒，並忽略為了簡單起見鎖定。  
  
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
  
```Output  
BigInt.Int[1] = 34, BigInt.Int[0] = 12  
```  
  
**結束 Microsoft 特定的**  
 進階微裝置，inc.著作權 2007著作權所有，並保留一切權利。 重製進階微裝置，Inc.的權限。  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [_InterlockedCompareExchange 內建函式](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)