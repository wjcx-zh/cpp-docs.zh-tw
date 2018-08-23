---
title: __addgsbyte、 __addgsword、 __addgsdword、 __addgsqword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50c0025e561c86fc18bbf5c4554c9f894fe32ec7
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541193"
---
# <a name="addgsbyte-addgsword-addgsdword-addgsqword"></a>__addgsbyte、__addgsword、__addgsdword、__addgsqword
**Microsoft 專屬**  
  
 將值新增至相對於開頭的位移所指定的記憶體位置`GS`區段。  
  
## <a name="syntax"></a>語法  
  
```  
void __addgsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __addgsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __addgsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __addgsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `Offset`  
 從開頭的位移`GS`。  
  
 [輸入] `Data`  
 要加入之記憶體位置的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__addgsbyte`|X64|  
|`__addgsword`|X64|  
|`__addgsdword`|X64|  
|`__addgsqword`|X64|  
  
## <a name="remarks"></a>備註  
 這些內建函式僅適用於核心模式，而這些常式僅可作為內建函式。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [__incgsbyte、 \__incgsword， \__incgsdword， \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)   
 [__readgsbyte、 \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [__writegsbyte、 \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)