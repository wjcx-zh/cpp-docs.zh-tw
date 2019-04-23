---
title: __outdword
ms.date: 11/04/2016
f1_keywords:
- __outdword
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
ms.openlocfilehash: 236c4812f62cb092876b400051248425ee1b13e7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034219"
---
# <a name="outdword"></a>__outdword

**Microsoft 專屬**

會產生`out`指示傳送 doubleword`Data`出連接埠`Port`。

## <a name="syntax"></a>語法

```
void __outdword(
   unsigned short Port,
   unsigned long Data
);
```

#### <a name="parameters"></a>參數

*連接埠*<br/>
[in]若要將資料傳送至連接埠。

*Data*<br/>
[in]要傳送 doubleword。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__outdword`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)