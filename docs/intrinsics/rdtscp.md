---
title: __rdtscp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __rdtscp
dev_langs:
- C++
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea7e8089f0678b89976a4c1e58ab6f3a364ac695
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="rdtscp"></a>__rdtscp
**Microsoft 特定的**  
  
 會產生`rdtscp`指令，將寫入`TSC_AUX[31:0`] 記憶體，並傳回 64 位元時間戳記計數器 (`TSC)`結果。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned __int64 __rdtscp(  
   unsigned int * Aux  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `Aux`  
 將包含特定電腦的暫存器內容的位置指標`TSC_AUX[31:0]`。  
  
## <a name="return-value"></a>傳回值  
 64 位元不帶正負號的整數的滴答計數。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__rdtscp`|AMD NPT 系列 0Fh 或更新版本|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建函式會產生`rdtscp`指令。 若要判斷硬體支援此指示，請呼叫`__cpuid`與內建`InfoType=0x80000001`並檢查的 27 位元`CPUInfo[3] (EDX)`。 此位元否則就會支援該指令，則為 1 和 0。  如果您執行程式碼會使用此內建物件不支援的硬體上`rdtscp`指令，結果會產生無法預測。  
  
> [!CAUTION]
>  不同於`rdtsc`，`rdtscp`是序列化的指示; 不過，編譯器可以移動解決這個問題的程式碼內建函式。  
  
 在這個層代的硬體 TSC 值的解譯不同於在舊版的[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]。  請參閱硬體手冊，如需詳細資訊。  
  
 中值的意義`TSC_AUX[31:0]`作業系統而定。  
  
## <a name="example"></a>範例  
  
```  
#include <intrin.h>   
#include <stdio.h>  
int main()   
{  
 unsigned __int64 i;  
 unsigned int ui;  
 i = __rdtscp(&ui);  
 printf_s("%I64d ticks\n", i);  
 printf_s("TSC_AUX was %x\n", ui);  
}  
```  
  
```Output  
3363423610155519 ticks  
TSC_AUX was 0  
```  
  
**結束 Microsoft 特定的**  
 進階微裝置，inc.著作權 2007著作權所有，並保留一切權利。 重製進階微裝置，Inc.的權限。  
  
## <a name="see-also"></a>請參閱  
 [__rdtsc](../intrinsics/rdtsc.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)