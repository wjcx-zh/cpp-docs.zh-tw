---
title: __vmx_vmlaunch
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 8d78e5181fdd43e10431e12d0cf540c8c9c2e719
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219557"
---
# <a name="__vmx_vmlaunch"></a>__vmx_vmlaunch

**Microsoft 專屬**

使用目前的虛擬機器控制結構 (VMCS), 將呼叫應用程式放在 VMX 非根作業狀態 (VM enter) 中。

## <a name="syntax"></a>語法

```C
unsigned char __vmx_vmlaunch(void);
```

## <a name="return-value"></a>傳回值

|值|意義|
|-----------|-------------|
|0|作業成功。|
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|
|2|作業失敗，無可用的狀態。|

## <a name="remarks"></a>備註

應用程式可以使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函數來執行 VM 輸入作業。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函數只能用於啟動狀態為`Clear`的 VMCS, 而[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函式只能搭配啟動狀態為`Launched`的 VMCS 使用。 因此, 請使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函式將 VMCS 的啟動狀態設定為`Clear`, 然後將[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函式用於第一個 vm 輸入作業, 並將[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函數用於後續的 vm-enter業務.

`__vmx_vmlaunch` 函式相當於 `VMLAUNCH` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請在[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站搜尋「適用于 IA-32 intel 架構的 Intel 虛擬化技術規格」檔 (檔編號 C97063-002)。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmlaunch`|X64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
