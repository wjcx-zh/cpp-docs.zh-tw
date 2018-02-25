---
title: "__lzcnt16，__lzcnt，__lzcnt64 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
dev_langs:
- C++
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85af6534ccf578bccabcd0f7b517234b2b560b6f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="lzcnt16-lzcnt-lzcnt64"></a>__lzcnt16，__lzcnt，__lzcnt64
**Microsoft 特定的**  
  
 計數數目的前置零的 16 位、 32 或 64 位元的整數。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned short __lzcnt16(  
   unsigned short value  
);  
unsigned int __lzcnt(  
   unsigned int value  
);  
unsigned __int64 __lzcnt64(  
   unsigned __int64 value  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `value`  
 16-、 32 或 64 位元不帶正負號的整數掃描前置零。  
  
## <a name="return-value"></a>傳回值  
 數目的前置零位元中的`value`參數。 如果`value`為零，則傳回值是輸入運算元 （16、 32 或 64） 的大小。 如果最高有效位元`value`，傳回的值為零。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__lzcnt16`|AMD： 進階的位元操作 (ABM)<br /><br /> Intel: Haswell|  
|`__lzcnt`|AMD： 進階的位元操作 (ABM)<br /><br /> Intel: Haswell|  
|`__lzcnt64`|AMD： 進階 64 位元模式中的位元操作 (ABM)。<br /><br /> Intel: Haswell|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 每個這些內建函式會產生`lzcnt`指令。  值的大小，`lzcnt`指令會傳回等同於其引數的大小。  在 32 位元模式中有沒有 64 位元一般用途的暫存器，因此沒有 64 位元`lzcnt`。  
  
 若要判斷硬體支援`lzcnt`指令呼叫`__cpuid`與內建`InfoType=0x80000001`並檢查位元 5 的`CPUInfo[2] (ECX)`。 此位元會支援該指令，則為 1 和 0 否則。 如果您執行程式碼會使用此內建物件不支援的硬體上`lzcnt`指令，結果會產生無法預測。  
  
 不支援的 Intel 處理器上`lzcnt`指令位元組編碼方式為執行指令， `bsr` （位元掃描反向）。 如果程式碼可攜性問題，請考慮使用`_BitScanReverse`內建改為。 如需詳細資訊，請參閱[_BitScanReverse，_BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md)。  
  
## <a name="example"></a>範例  
  
```  
// Compile this test with: /EHsc  
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
    usr = __lzcnt16(us[i]);  
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __lzcnt(ui[i]);  
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
```Output  
__lzcnt16(0x0) = 16  
__lzcnt16(0xff) = 8  
__lzcnt16(0xffff) = 0  
__lzcnt(0x0) = 32  
__lzcnt(0xff) = 24  
__lzcnt(0xffff) = 16  
__lzcnt(0xffffffff) = 0  
```  
  
**結束 Microsoft 特定的**  
 本文部分內容是由進階微裝置，Inc.著作權 2007著作權所有，並保留一切權利。 重製進階微裝置，Inc.的權限。  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)