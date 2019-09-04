---
title: __svm_vmload
ms.date: 09/02/2019
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: da6ca9786b9c7e5041b9a8ca908d567b16176436
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219807"
---
# <a name="__svm_vmload"></a>__svm_vmload

**Microsoft 專屬**

從指定的虛擬機器控制區塊 (VMCB) 載入處理器狀態的子集。

## <a name="syntax"></a>語法

```C
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>參數

*VmcbPhysicalAddress*\
在VMCB 的實體位址。

## <a name="remarks"></a>備註

`__svm_vmload` 函式相當於 `VMLOAD` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請搜尋檔「AMD64 架構程式設計人員手冊第2卷:系統程式設計, 位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)網站的「檔編號 24593, 修訂3.11」。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_vmload`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)
