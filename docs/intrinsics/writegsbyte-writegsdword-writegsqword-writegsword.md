---
title: "__writegsbyte、 __writegsdword、 __writegsqword、 __writegsword |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
dev_langs: C++
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a51a8351cc4acffb3ba73283627adb911e84922
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="writegsbyte-writegsdword-writegsqword-writegsword"></a>__writegsbyte、__writegsdword、__writegsqword、__writegsword
**Microsoft 特定的**  
  
 寫入記憶體相對於 GS 區段開頭的位移所指定的位置。  
  
## <a name="syntax"></a>語法  
  
```  
void __writegsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writegsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writegsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writegsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `Offset`  
 要寫入的 GS 開頭位移。  
  
 [in] `Data`  
 要寫入的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__writegsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 這些內建函式僅適用於核心模式，而這些常式只可做為內建函式。  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__readgsbyte、 \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)