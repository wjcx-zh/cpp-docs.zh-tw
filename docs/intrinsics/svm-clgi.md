---
title: __svm_clgi
ms.date: 11/04/2016
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: fe25141499a19a265e2ac3ec746664ecd6cc9a2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390304"
---
# <a name="svmclgi"></a>__svm_clgi

**Microsoft 專屬**

清除全域中斷旗標。

## <a name="syntax"></a>語法

```
void __svm_clgi( void );
```

## <a name="remarks"></a>備註

`__svm_clgi` 函式相當於 `CLGI` 機器指令。 全域中斷旗標會判斷微處理器忽略、 延後，或處理等 I/O 完成、 硬體溫度警示或偵錯例外狀況事件，而中斷。

這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2:系統程式設計，> 文件數目 24593，修訂 3.11，位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_clgi`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_stgi](../intrinsics/svm-stgi.md)