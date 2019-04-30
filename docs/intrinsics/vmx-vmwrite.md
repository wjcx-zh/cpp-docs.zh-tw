---
title: __vmx_vmwrite
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: e52b1f181f00ce013a111d1a5a62abeff544e20a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389979"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite

**Microsoft 專屬**

將指定的值寫入目前的虛擬機器控制結構 (VMCS) 中指定的欄位。

## <a name="syntax"></a>語法

```
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*欄位*|[in]要寫入的 VMCS 欄位。|
|*FieldValue*|[in]要寫入的 VMCS 欄位的值。|

## <a name="return-value"></a>傳回值

作業成功的 0。

1 的作業失敗中可用的擴充狀態`VM-instruction error field`在目前 vmcs。

2 無可用的狀態，，作業失敗。

## <a name="remarks"></a>備註

`__vmx_vmwrite` 函式相當於 `VMWRITE` 機器指令。 值`Field`參數是 Intel 文件中所述的編碼的欄位索引。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站的 url，並請參考 旓紵 C 的文件。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmread](../intrinsics/vmx-vmread.md)