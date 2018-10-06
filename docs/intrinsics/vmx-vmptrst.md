---
title: __vmx_vmptrst |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrst
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f9cd2ebdbcf2ad2feb3b66412fbcd5687e85dce
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820564"
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

#### <a name="parameters"></a>參數

[in] *`VmcsPhysicalAddress`儲存目前 VMCS 指標的位址。

## <a name="remarks"></a>備註

VMCS 指標是 64 位元的實體位址。

`__vmx_vmptrst`函式相當於`VMPTRST`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmptrst`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)