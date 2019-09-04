---
title: __vmx_vmptrst
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: e559746be9e2a3fe5e81afa4d290265394db3e36
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219480"
---
# <a name="__vmx_vmptrst"></a>__vmx_vmptrst

**Microsoft 專屬**

將目前虛擬機器控制結構 (VMCS) 的指標儲存在指定的位址。

## <a name="syntax"></a>語法

```C
void __vmx_vmptrst(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>參數

*VmcsPhysicalAddress*\
在儲存目前 VMCS 指標的位址。

## <a name="remarks"></a>備註

VMCS 指標是64位的實體位址。

`__vmx_vmptrst` 函式相當於 `VMPTRST` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請在[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站搜尋「適用于 IA-32 intel 架構的 Intel 虛擬化技術規格」檔 (檔編號 C97063-002)。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmptrst`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)
