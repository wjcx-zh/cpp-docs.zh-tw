---
title: __readpmc
ms.date: 09/02/2019
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: af0f1874d991771423ddebfedd4624cd0b71760f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221030"
---
# <a name="__readpmc"></a>__readpmc

**Microsoft 專屬**

產生指令, 它會讀取 counter 所指定的效能監視計數器。 `rdpmc`

## <a name="syntax"></a>語法

```C
unsigned __int64 __readpmc(
   unsigned long counter
);
```

### <a name="parameters"></a>參數

*抵禦*\
在要讀取的效能計數器。

## <a name="return-value"></a>傳回值

指定效能計數器的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readpmc`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

內建函式僅適用于核心模式, 而常式僅以內建函式的形式提供。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
