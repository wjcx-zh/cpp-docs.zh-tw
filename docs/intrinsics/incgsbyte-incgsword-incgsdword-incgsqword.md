---
title: __incgsbyte、__incgsword、__incgsdword、__incgsqword
ms.date: 09/02/2019
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
ms.openlocfilehash: 8b4e88b4ccd2cf1d2a3130e3a535de1c9a434320
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217790"
---
# <a name="__incgsbyte-__incgsword-__incgsdword-__incgsqword"></a>__incgsbyte、__incgsword、__incgsdword、__incgsqword

**Microsoft 專屬**

在相對於`GS`區段開頭的位移所指定的記憶體位置, 將一個值加一。

## <a name="syntax"></a>語法

```C
void __incgsbyte(
   unsigned long Offset
);
void __incgsword(
   unsigned long Offset
);
void __incgsdword(
   unsigned long Offset
);
void __incgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>參數

*投影*\
在從開頭算起`GS`的位移。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__incgsbyte`|X64|
|`__incgsword`|X64|
|`__incgsdword`|X64|
|`__incgsqword`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

這些常式僅以內建函式的形式提供。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[\__addgsbyte、 \__addgsword、 \__addgsdword、 \__addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)\
[\__readgsbyte、 \__readgsdword、 \__readgsqword、 \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[\__writegsbyte、 \__writegsdword、 \__writegsqword、 \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
