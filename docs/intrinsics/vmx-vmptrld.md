---
title: __vmx_vmptrld |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrld
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7126dc3b6a0ece4a5b7627859d0b80abf962d88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429098"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld

**Microsoft 專屬**

載入至目前的虛擬機器控制結構 (VMCS) 的指標，從指定的位址。

## <a name="syntax"></a>語法

```
int __vmx_vmptrld( 
   unsigned __int64 *VmcsPhysicalAddress 
);
```

#### <a name="parameters"></a>參數

[in] *`VmcsPhysicalAddress` VMCS 指標的儲存位置的位址。

## <a name="return-value"></a>傳回值

作業成功的 0。

1 的作業失敗中可用的擴充狀態`VM-instruction error field`在目前 vmcs。

2 無可用的狀態，，作業失敗。

## <a name="remarks"></a>備註

VMCS 指標是 64 位元的實體位址。

`__vmx_vmptrld`函式相當於`VMPTRLD`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)