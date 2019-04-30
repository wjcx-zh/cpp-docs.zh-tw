---
title: __halt
ms.date: 11/04/2016
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: dd68c88a13035ca25f89304bcd84267a73978420
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344443"
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

`__halt`函式相當於`HLT`機器指令，且只適用於核心模式。 如需詳細資訊，搜尋文件中，「 Intel 架構軟體開發人員的手動、 磁碟區 2:指令集參考，「 在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站台。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)