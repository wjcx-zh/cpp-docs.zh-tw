---
title: __outbytestring
ms.date: 09/02/2019
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: 31caf17db5d56efccd6b30200994b1080356b4c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217166"
---
# <a name="__outbytestring"></a>__outbytestring

**Microsoft 專屬**

產生指示, 此指令會將所`Count`指向`Buffer`的前幾個位元組傳送至所指定`Port`的埠。 `rep outsb`

## <a name="syntax"></a>語法

```C
void __outbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>參數

*移植*\
在要將資料傳送至其中的通訊埠。

*緩衝區*\
在要從指定的埠送出的資料。

*計數*\
在要傳送的資料位元組數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__outbytestring`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
