---
title: __svm_stgi
ms.date: 09/02/2019
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 6bd731951b440d3d2597d54c9a52d9f8640a5c5f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219841"
---
# <a name="__svm_stgi"></a>__svm_stgi

**Microsoft 專屬**

設定全域中斷旗標。

## <a name="syntax"></a>語法

```C
void __svm_stgi(void);
```

## <a name="remarks"></a>備註

`__svm_stgi` 函式相當於 `STGI` 機器指令。 全域中斷旗標會根據事件 (例如 i/o 完成、硬體溫度警示或偵錯工具例外狀況), 判斷微處理器是否忽略、延後或處理中斷。

這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請搜尋「AMD64 架構程式設計人員手冊第2卷:系統程式設計, 位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)網站。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_stgi`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__svm_clgi](../intrinsics/svm-clgi.md)
