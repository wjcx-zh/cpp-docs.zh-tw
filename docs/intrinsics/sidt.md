---
title: __sidt |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbfb0b50e31cc51c7ea860fbd7b78c89a652ac64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429368"
---
# <a name="sidt"></a>__sidt

**Microsoft 專屬**

會中斷描述項表登錄 (IDTR) 的值儲存在指定的記憶體位置。

## <a name="syntax"></a>語法

```
void __sidt(void * Destination);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*目的地*|[in]IDTR 儲存所在之記憶體位置指標。|

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__sidt`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`__sidt`函式相當於`SIDT`機器指令。 如需詳細資訊，搜尋文件中，「 Intel 架構軟體開發人員的手動、 磁碟區 2： 指令集參考，「 在[Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm)站台。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__lidt](../intrinsics/lidt.md)