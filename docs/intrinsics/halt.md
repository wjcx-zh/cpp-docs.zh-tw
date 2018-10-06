---
title: __halt |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __halt
- __halt_cpp
dev_langs:
- C++
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a42575b25040b0dc78bd0199089aaf9575e8de47
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820618"
---
# <a name="halt"></a>__halt

**Microsoft 專屬**

啟用插斷、 非遮罩式插斷 （nmi） 傳送或重設發生之前，暫止微處理器。

## <a name="syntax"></a>語法

```
void __halt( void );
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__halt`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`__halt`函式相當於`HLT`機器指令，且只適用於核心模式。 如需詳細資訊，搜尋文件中，「 Intel 架構軟體開發人員的手動、 磁碟區 2： 指令集參考，「 在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站台。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)