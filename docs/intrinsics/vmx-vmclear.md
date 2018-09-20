---
title: __vmx_vmclear |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmclear
dev_langs:
- C++
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d0b584172a95fc388893c276b05b311365ad109
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441781"
---
# <a name="vmxvmclear"></a>__vmx_vmclear

**Microsoft 專屬**

初始化指定的虛擬機器控制結構 (VMCS)，並將其啟動狀態設為`Clear`。

## <a name="syntax"></a>語法

```
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*VmcsPhysicalAddress*|[in]包含要清除 VMCS 的實體位址的 64 位元記憶體位置指標。|

## <a name="return-value"></a>傳回值

|值|意義|
|-----------|-------------|
|0|作業成功。|
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|
|2|作業失敗，無可用的狀態。|

## <a name="remarks"></a>備註

應用程式可以執行 VM 輸入作業使用其中一種[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或是[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函式。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函式只能搭配的 VMCS 的啟動狀態`Clear`，而[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函式只能搭配的 VMCS 的啟動狀態是`Launched`。 因此，使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函式設定至 VMCS 的啟動狀態`Clear`。 使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)第一個 VM 輸入作業的函式並[__vmx_vmresume](../intrinsics/vmx-vmresume.md)後續的 VM 輸入作業的函式。

`__vmx_vmclear`函式相當於`VMCLEAR`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmclear`|X64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)<br/>
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)