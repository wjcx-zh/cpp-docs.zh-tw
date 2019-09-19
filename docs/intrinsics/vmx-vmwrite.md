---
title: __vmx_vmwrite
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: cdc5590858f160db24bf75ef11c8f20b204a3152
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219401"
---
# <a name="__vmx_vmwrite"></a>__vmx_vmwrite

**Microsoft 專屬**

將指定的值寫入目前虛擬機器控制結構 (VMCS) 中的指定欄位。

## <a name="syntax"></a>語法

```C
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

### <a name="parameters"></a>參數

*欄位*\
在要寫入的 VMCS 欄位。

*FieldValue*\
在要寫入 VMCS 欄位的值。

## <a name="return-value"></a>傳回值

0\
作業成功。

1\
作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。

2\
作業失敗，無可用的狀態。

## <a name="remarks"></a>備註

`__vmx_vmwrite` 函式相當於 `VMWRITE` 機器指令。 `Field`參數的值是 Intel 檔中所述的編碼欄位索引。 如需詳細資訊, 請在[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站搜尋「適用于 IA-32 intel 架構的 Intel 虛擬化技術規格」的附錄 C。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmread](../intrinsics/vmx-vmread.md)
