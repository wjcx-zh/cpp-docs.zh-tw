---
title: __svm_invlpga
ms.date: 09/02/2019
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: e0f8ef02efdb64f70bb65f6f017449fcc03beca1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219894"
---
# <a name="__svm_invlpga"></a>__svm_invlpga

**Microsoft 專屬**

使電腦的轉譯後端緩衝區中的位址對應專案失效。 參數會指定要使其失效之頁面的虛擬位址和位址空間識別碼。

## <a name="syntax"></a>語法

```C
void __svm_invlpga(void *Vaddr, int as_id);
```

### <a name="parameters"></a>參數

*Vaddr*\
在要使其失效之頁面的虛擬位址。

*as_id*\
在要使其失效之頁面的位址空間識別碼 (ASID)。

## <a name="remarks"></a>備註

`__svm_invlpga` 函式相當於 `INVLPGA` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請搜尋檔「AMD64 架構程式設計人員手冊第2卷:系統程式設計, 位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)網站的「檔編號 24593, 修訂3.11」。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_invlpga`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
