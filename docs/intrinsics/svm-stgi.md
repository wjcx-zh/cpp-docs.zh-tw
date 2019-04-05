---
title: __svm_stgi
ms.date: 11/04/2016
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: ea138f17a24af21afa937991f77bd1e2a689c3f7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024786"
---
# <a name="svmstgi"></a>__svm_stgi

**Microsoft 特定的**

設定全域中斷旗標。

## <a name="syntax"></a>語法

```
void __svm_stgi(void);
```

## <a name="remarks"></a>備註

`__svm_stgi` 函式相當於 `STGI` 機器指令。 全域中斷旗標會判斷微處理器忽略、 延後，或處理等 I/O 完成、 硬體溫度警示或偵錯例外狀況事件，而中斷。

這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2:系統程式設計，> 文件數目 24593，修訂 3.11，位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_stgi`|x86、x64|

**標頭檔** \<intrin.h >

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_clgi](../intrinsics/svm-clgi.md)