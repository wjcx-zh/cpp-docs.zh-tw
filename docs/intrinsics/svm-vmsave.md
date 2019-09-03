---
title: __svm_vmsave
ms.date: 09/02/2019
f1_keywords:
- __svm_vmsave
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
ms.openlocfilehash: f91efa7116a8a8e9ebe27c7e5e4e64c4f1533e9d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219790"
---
# <a name="__svm_vmsave"></a>__svm_vmsave

**Microsoft 專屬**

將處理器狀態子集儲存在指定的虛擬機器控制區塊 (VMCB) 中。

## <a name="syntax"></a>語法

```C
void __svm_vmsave(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>參數

*VmcbPhysicalAddress*\
在VMCB 的實體位址。

## <a name="remarks"></a>備註

`__svm_vmsave` 函式相當於 `VMSAVE` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請搜尋檔「AMD64 架構程式設計人員手冊第2卷:系統程式設計: 「檔編號24593、修訂版3.11 或更新版本, 位於[AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/)網站。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_vmsave`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
