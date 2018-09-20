---
title: __svm_stgi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_stgi
dev_langs:
- C++
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd4d2593621c7c2cc36f84580a757e98f5e48c92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431249"
---
# <a name="svmstgi"></a>__svm_stgi

**Microsoft 專屬**

設定全域中斷旗標。

## <a name="syntax"></a>語法

```
void __svm_stgi(void);
```

## <a name="remarks"></a>備註

`__svm_stgi`函式相當於`STGI`機器指令。 全域中斷旗標會判斷微處理器忽略、 延後，或處理等 I/O 完成、 硬體溫度警示或偵錯例外狀況事件，而中斷。

這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計中，「 文件數目 24593，修訂 3.11，位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_stgi`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_clgi](../intrinsics/svm-clgi.md)