---
title: __svm_vmrun
ms.date: 09/02/2019
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: f23df894cc8ad1c270c4c0acbc97cab727e47d93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219830"
---
# <a name="__svm_vmrun"></a>__svm_vmrun

**Microsoft 專屬**

開始執行與指定的虛擬機器控制區塊 (VMCB) 相對應的虛擬機器來賓程式碼。

## <a name="syntax"></a>語法

```C
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>參數

*VmcbPhysicalAddress*\
在VMCB 的實體位址。

## <a name="remarks"></a>備註

`__svm_vmrun`函式會在 VMCB 中使用最少量的資訊, 開始執行虛擬機器來賓程式碼。 如果您需要更多的資訊來處理複雜的中斷, 或切換到其他來賓, 請使用[__svm_vmsave](../intrinsics/svm-vmsave.md)或[__svm_vmload](../intrinsics/svm-vmload.md)函數。

`__svm_vmrun` 函式相當於 `VMRUN` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請搜尋檔「AMD64 架構程式設計人員手冊第2卷:系統程式設計: 「檔編號24593、修訂版3.11 或更新版本, 位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)網站。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_vmrun`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
