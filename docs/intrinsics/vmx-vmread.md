---
title: __vmx_vmread
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 409835ac29d6f2e839de62291cc5b142166a465c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219428"
---
# <a name="__vmx_vmread"></a>__vmx_vmread

**Microsoft 專屬**

從目前的虛擬機器控制結構 (VMCS) 讀取指定的欄位, 並將它放在指定的位置。

## <a name="syntax"></a>語法

```C
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

### <a name="parameters"></a>參數

*欄位*\
在要讀取的 VMCS 欄位。

*FieldValue*\
在位置的指標, 用來儲存從`Field`參數所指定的 VMCS 欄位讀取的值。

## <a name="return-value"></a>傳回值

|值|意義|
|-----------|-------------|
|0|作業成功。|
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|
|2|作業失敗，無可用的狀態。|

## <a name="remarks"></a>備註

`__vmx_vmread` 函式相當於 `VMREAD` 機器指令。 `Field`參數的值是 Intel 檔中所述的編碼欄位索引。 如需詳細資訊, 請在[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站搜尋「適用于 IA-32 intel 架構的 Intel 虛擬化技術規格」的附錄 C。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmread`|X64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)
