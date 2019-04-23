---
title: __svm_vmload
ms.date: 11/04/2016
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: 282f1c005c7eb59b2c590c70b38233c88c664e07
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031150"
---
# <a name="svmvmload"></a>__svm_vmload

**Microsoft 專屬**

從指定的虛擬機器控制區塊 (VMCB) 中載入處理器狀態的子集。

## <a name="syntax"></a>語法

```
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in]VMCB 實體位址。|

## <a name="remarks"></a>備註

`__svm_vmload` 函式相當於 `VMLOAD` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2:系統程式設計，> 文件數目 24593，修訂 3.11，位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_vmload`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmrun](../intrinsics/svm-vmrun.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)