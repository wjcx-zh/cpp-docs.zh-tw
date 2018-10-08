---
title: __vmx_on |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_on
dev_langs:
- C++
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 807abab1d87c8f8bad996e103b4043d70e140172
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820532"
---
# <a name="vmxon"></a>__vmx_on

**Microsoft 專屬**

啟動處理器中的虛擬機器擴充功能 (VMX) 作業。

## <a name="syntax"></a>語法

```
unsigned char __vmx_on(
   unsigned __int64 *VmsSupportPhysicalAddress
);
```

#### <a name="parameters"></a>參數

*VmsSupportPhysicalAddress*<br/>
[in]指標，指向 [虛擬機器控制結構 (VMCS) 的 64 位元實體位址。

## <a name="return-value"></a>傳回值

|值|意義|
|-----------|-------------|
|0|作業成功。|
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|
|2|作業失敗，無可用的狀態。|

## <a name="remarks"></a>備註

`__vmx_on`函式對應至`VMXON`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_on`|X64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)