---
title: __vmx_vmptrld
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 79b5a8b34b652ae1f011e89c793a7157c9e435ee
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219502"
---
# <a name="__vmx_vmptrld"></a>__vmx_vmptrld

**Microsoft 專屬**

從指定的位址載入目前虛擬機器控制結構 (VMCS) 的指標。

## <a name="syntax"></a>語法

```C
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>參數

*VmcsPhysicalAddress*\
在儲存 VMCS 指標的位址。

## <a name="return-value"></a>傳回值

0\
作業成功。

1\
作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。

2\
作業失敗，無可用的狀態。

## <a name="remarks"></a>備註

VMCS 指標是64位的實體位址。

`__vmx_vmptrld` 函式相當於 `VMPTRLD` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請在[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站搜尋「適用于 IA-32 intel 架構的 Intel 虛擬化技術規格」檔 (檔編號 C97063-002)。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)
