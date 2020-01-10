---
title: __vmx_vmclear
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 3b5807402cf0a9d8a9ef1ded1d112d22a801633e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219535"
---
# <a name="__vmx_vmclear"></a>__vmx_vmclear

**Microsoft 專屬**

初始化指定的虛擬機器控制結構 (VMCS), 並將其啟動狀態`Clear`設定為。

## <a name="syntax"></a>語法

```C
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>參數

*VmcsPhysicalAddress*\
在64位記憶體位置的指標, 其中包含要清除之 VMCS 的實體位址。

## <a name="return-value"></a>傳回值

|值|意義|
|-----------|-------------|
|0|作業成功。|
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|
|2|作業失敗，無可用的狀態。|

## <a name="remarks"></a>備註

應用程式可以使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函數來執行 VM 輸入作業。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函數只能用於啟動狀態為`Clear`的 VMCS, 而[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函式只能搭配啟動狀態為`Launched`的 VMCS 使用。 因此, 請使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函數將 VMCS 的啟動狀態設定為`Clear`。 針對您的第一個 VM 輸入作業使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函式, 並針對後續的 vm 輸入操作使用[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函數。

`__vmx_vmclear` 函式相當於 `VMCLEAR` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請在[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站搜尋「適用于 IA-32 intel 架構的 Intel 虛擬化技術規格」檔 (檔編號 C97063-002)。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmclear`|X64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
