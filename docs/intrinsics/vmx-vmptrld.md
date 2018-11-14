---
title: __vmx_vmptrld
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 4f74a69bf0a4a780834dc9669c1266c82f7038e6
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325905"
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

### <a name="parameters"></a>參數

*VmcsPhysicalAddress*<br/>
[in]儲存 VMCS 指標位址。

## <a name="return-value"></a>傳回值

0<br/>
作業成功。

1<br/>
作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。

2<br/>
作業失敗，無可用的狀態。

## <a name="remarks"></a>備註

VMCS 指標是 64 位元的實體位址。

`__vmx_vmptrld` 函式相當於 `VMPTRLD` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)