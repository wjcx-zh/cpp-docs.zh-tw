---
title: __vmx_on
ms.date: 09/02/2019
f1_keywords:
- __vmx_on
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
ms.openlocfilehash: b6041711d9b6806362b856475151f2c4f63750cb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219571"
---
# <a name="__vmx_on"></a>__vmx_on

**Microsoft 專屬**

在處理器中啟用虛擬機器擴充功能 (VMX) 作業。

## <a name="syntax"></a>語法

```C
unsigned char __vmx_on(
   unsigned __int64 *VmsSupportPhysicalAddress
);
```

### <a name="parameters"></a>參數

*VmsSupportPhysicalAddress*\
[in]指標，指向虛擬機器控制結構 (VMCS) 的 64 位元實體位址。

## <a name="return-value"></a>傳回值

|值|意義|
|-----------|-------------|
|0|作業成功。|
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|
|2|作業失敗，無可用的狀態。|

## <a name="remarks"></a>備註

函式會對應`VMXON`至機器指令。 `__vmx_on` 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請在[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站搜尋「適用于 IA-32 intel 架構的 Intel 虛擬化技術規格」檔 (檔編號 C97063-002)。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_on`|X64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
