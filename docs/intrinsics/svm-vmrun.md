---
title: __svm_vmrun
ms.date: 11/04/2016
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: 40e53b2ebd54fc109b47f3067e5f89ce50b327de
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041055"
---
# <a name="svmvmrun"></a>__svm_vmrun

**Microsoft 特定的**

開始執行的虛擬機器客體程式碼對應至指定的虛擬機器控制區塊 (VMCB)。

## <a name="syntax"></a>語法

```
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in]VMCB 實體位址。|

## <a name="remarks"></a>備註

`__svm_vmrun`函式使用 VMCB 中最少量的資訊，開始執行的虛擬機器客體程式碼。 使用[__svm_vmsave](../intrinsics/svm-vmsave.md)或是[__svm_vmload](../intrinsics/svm-vmload.md)函式，如果您需要處理複雜的中斷，或切換至另一個客體的詳細資訊。

`__svm_vmrun` 函式相當於 `VMRUN` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2:系統程式設計，> 文件數目 24593，修訂 3.11 或更新版本，在[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_vmrun`|x86、x64|

**標頭檔** \<intrin.h >

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)<br/>
[__svm_vmload](../intrinsics/svm-vmload.md)