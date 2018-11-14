---
title: __outdwordstring
ms.date: 11/04/2016
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: 5579258c813850cdb8f29758bb4bd5d87270467f
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330277"
---
# <a name="outdwordstring"></a>__outdwordstring

**Microsoft 專屬**

會產生`rep outsd`指示，會傳送`Count`雙字組開頭`Buffer`出所指定的 I/O 連接埠`Port`。

## <a name="syntax"></a>語法

```
void __outdwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>參數

*連接埠*<br/>
[in]若要將資料傳送至連接埠。

*Buffer*<br/>
[in]指定的連接埠傳送資料的指標。

*計數*<br/>
[in]若要傳送的雙字組數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__outdwordstring`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)