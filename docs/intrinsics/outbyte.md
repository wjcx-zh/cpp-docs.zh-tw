---
title: __outbyte
ms.date: 11/04/2016
f1_keywords:
- __outbyte
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
ms.openlocfilehash: 8695fafb25be730ebe84828527d0689211c7801b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479012"
---
# <a name="outbyte"></a>__outbyte

**Microsoft 專屬**

會產生`out`會傳送 1 個位元組所指定的指令`Data`出所指定的 I/O 連接埠`Port`。

## <a name="syntax"></a>語法

```
void __outbyte( 
   unsigned short Port, 
   unsigned char Data 
);
```

#### <a name="parameters"></a>參數

*連接埠*<br/>
[in]若要將資料傳送至連接埠。

*Data*<br/>
[in]送出指定的連接埠位元組。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__outbyte`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)