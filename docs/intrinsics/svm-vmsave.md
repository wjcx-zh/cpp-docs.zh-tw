---
title: __svm_vmsave |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmsave
dev_langs:
- C++
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f543fa6c1b1f41040cc6cf13bf2c97cda5b69daf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383340"
---
# <a name="svmvmsave"></a>__svm_vmsave

**Microsoft 專屬**

儲存在指定的虛擬機器控制區塊 (VMCB) 的處理器狀態的子集。

## <a name="syntax"></a>語法

```
void __svm_vmsave(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in]VMCB 實體位址。|

## <a name="remarks"></a>備註

`__svm_vmsave`函式相當於`VMSAVE`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計中，「 文件編號 24593、 修訂 3.11 或更新版本，在[AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_vmsave`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmrun](../intrinsics/svm-vmrun.md)<br/>
[__svm_vmload](../intrinsics/svm-vmload.md)