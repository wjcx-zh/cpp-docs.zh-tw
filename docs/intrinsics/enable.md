---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: e1ece6d6f4040b81b55d8400407d46f165b56b53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349026"
---
# <a name="enable"></a>_enable

**Microsoft 專屬**

啟用中斷。

## <a name="syntax"></a>語法

```
void _enable(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_enable`|x86、 x64、 ARM|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`_enable` 指示處理器設定中斷旗標。 在 x86 系統中，這個函式會產生設定中斷旗標 (`sti`) 指令。

這個函式只適用於核心模式。 如果在使用者模式中使用，會擲回有權限指令例外狀況。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)