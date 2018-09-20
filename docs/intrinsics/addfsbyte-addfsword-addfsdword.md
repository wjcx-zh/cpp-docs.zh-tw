---
title: __addfsbyte、 __addfsword、 __addfsdword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __addfsbyte_cpp
- __addfsdword
- __addfsword_cpp
- __addfsbyte
- __addfsword
- __addfsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __addfsdword intrinsic
- __addfsword intrinsic
- __addfsbyte intrinsic
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5831d109301fe400cf75110221c3c37204bf5b26
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414962"
---
# <a name="addfsbyte-addfsword-addfsdword"></a>__addfsbyte、__addfsword、__addfsdword

**Microsoft 專屬**

將值新增至相對於開頭的位移所指定的記憶體位置`FS`區段。

## <a name="syntax"></a>語法

```
void __addfsbyte( 
   unsigned long Offset, 
   unsigned char Data 
);
void __addfsword( 
   unsigned long Offset, 
   unsigned short Data 
);
void __addfsdword( 
   unsigned long Offset, 
   unsigned long Data 
);
```

#### <a name="parameters"></a>參數

*位移*<br/>
[in]從開頭的位移`FS`。

*Data*<br/>
[in]要加入之記憶體位置的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__addfsbyte`|x86|
|`__addfsword`|x86|
|`__addfsdword`|x86|

## <a name="remarks"></a>備註

這些常式都僅有內建函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__incfsbyte、 \__incfsword， \__incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)<br/>
[__readfsbyte、 \__readfsdword， \__readfsqword， \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[__writefsbyte、 \__writefsdword， \__writefsqword， \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)