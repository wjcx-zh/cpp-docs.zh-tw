---
title: __popcnt16、 __popcnt、 __popcnt64 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
dev_langs:
- C++
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a639091bd7c5c263a3f09067858cd0fe4ac631cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="popcnt16-popcnt-popcnt64"></a>__popcnt16、__popcnt、__popcnt64
**Microsoft 特定的**  
  
 計算其中數字的 16 位、 32 或 64 位元不帶正負號的整數中的位元 （母體擴展計數）。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned short __popcnt16(  
   unsigned short value  
);  
unsigned int __popcnt(  
   unsigned int value  
);  
unsigned __int64 __popcnt64(  
   unsigned __int64 value  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `value`  
 16-、 32 或 64 位元不帶正負號的整數，我們想要擴展計數。  
  
## <a name="return-value"></a>傳回值  
 中的一個位元數`value`參數。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__popcnt16`|進階的位元操作|  
|`__popcnt`|進階的位元操作|  
|`__popcnt64`|在 64 位元模式中的進階位元操作。|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 每個這些內建函式會產生`popcnt`指令。  值的大小，`popcnt`指令會傳回等同於其引數的大小。  在 32 位元模式中有沒有 64 位元一般用途的暫存器，因此沒有 64 位元`popcnt`。  
  
 若要決定硬體支援的`popcnt`指示，請呼叫`__cpuid`與內建`InfoType=0x00000001`並檢查位元 23 的`CPUInfo[2] (ECX)`。 此位元否則就會支援該指令，則為 1 和 0。 如果您執行程式碼會使用此內建物件不支援的硬體上`popcnt`指令，結果會產生無法預測。  
  
## <a name="example"></a>範例  
  
```  
#include <iostream>   
#include <intrin.h>   
using namespace std;   
  
int main()   
{  
  unsigned short us[3] = {0, 0xFF, 0xFFFF};  
  unsigned short usr;  
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};  
  unsigned int   uir;  
  
  for (int i=0; i<3; i++) {  
    usr = __popcnt16(us[i]);  
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __popcnt(ui[i]);  
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
```Output  
__popcnt16(0x0) = 0  
__popcnt16(0xff) = 8  
__popcnt16(0xffff) = 16  
__popcnt(0x0) = 0  
__popcnt(0xff) = 8  
__popcnt(0xffff) = 16  
__popcnt(0xffffffff) = 32  
```  
  
**結束 Microsoft 特定的**  
 進階微裝置，inc.著作權 2007著作權所有，並保留一切權利。 重製進階微裝置，Inc.的權限。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
