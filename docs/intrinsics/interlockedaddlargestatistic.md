---
title: "_InterlockedAddLargeStatistic |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs: C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7930f1411c419fbf5f47164029fe42dd82455ff8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic
**Microsoft 特定的**  
  
 執行連鎖的相加的第一個運算元中是 64 位元值。  
  
## <a name="syntax"></a>語法  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in、out] `Addend`  
 若要加入作業的第一個運算元指標。 指向的值取代相加的結果。  
  
 [in] `Value`  
 第二個運算元中。若要加入的第一個運算元的值。  
  
## <a name="return-value"></a>傳回值  
 第二個運算元的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建物件不是不可部分完成因為它會執行為兩個不同的鎖定的指示。 不可部分完成的 64 位元讀取另一個執行緒上執行期間發生這個內建函式可能會導致不一致所讀取的值。  
  
 此函式的行為為讀寫屏障。 如需詳細資訊，請參閱[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)。  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)