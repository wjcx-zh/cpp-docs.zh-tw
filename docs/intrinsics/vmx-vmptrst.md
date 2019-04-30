---
title: __vmx_vmptrst
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: 5ef02dd4401e0c10a84be008d7cb25841e0359cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389992"
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst

**Microsoft 專屬**

儲存目前的虛擬機器控制結構 (VMCS) 在指定的位址指標。

## <a name="syntax"></a>語法

```
void __vmx_vmptrst(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>參數

*VmcsPhysicalAddress*<br/>
[in]儲存目前 VMCS 指標位址。

## <a name="remarks"></a>備註

VMCS 指標是 64 位元的實體位址。

`__vmx_vmptrst` 函式相當於 `VMPTRST` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmptrst`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)