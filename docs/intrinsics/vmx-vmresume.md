---
title: __vmx_vmresume
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: 34d0e6814dd00da07076e644513400bd5be36bd3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219446"
---
# <a name="__vmx_vmresume"></a>__vmx_vmresume

**Microsoft 專屬**

使用目前的虛擬機器控制結構 (VMCS) 繼續 VMX 非根作業。

## <a name="syntax"></a>語法

```C
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>傳回值

|值|意義|
|-----------|-------------|
|0|作業成功。|
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|
|2|作業失敗，無可用的狀態。|

## <a name="remarks"></a>備註

應用程式可以使用 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) 或 `__vmx_vmresume` 函式執行 VM 輸入作業。 `__vmx_vmlaunch` 函式只能搭配啟動狀態為 `Clear`的 VMCS，而 `__vmx_vmresume` 函式只能搭配啟動狀態為 `Launched`的 VMCS。 因此，使用 [__vmx_vmclear](../intrinsics/vmx-vmclear.md) 函式可將 VMCS 的啟動狀態設為 `Clear`，然後第一個 VM 輸入作業使用 `__vmx_vmlaunch` 函式，後續的 VM 輸入作業使用 `__vmx_vmresume` 函式。

`__vmx_vmresume` 函式相當於 `VMRESUME` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，請搜尋 PDF 文件＜IA-32 Intel 架構的 Intel 虛擬化技術規格＞，文件編號 C97063-002，位於 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmresume`|X64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
