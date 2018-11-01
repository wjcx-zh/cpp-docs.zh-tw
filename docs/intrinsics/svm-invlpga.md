---
title: __svm_invlpga
ms.date: 11/04/2016
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: 2d356cf7426c558c8ac0312eff02c0cb9de9c859
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544296"
---
# <a name="svminvlpga"></a>__svm_invlpga

**Microsoft 專屬**

失效的電腦轉譯旁觀緩衝區中的位址對應項目。 參數會指定虛擬位址和位址空間識別項的頁面，即可使其失效。

## <a name="syntax"></a>語法

```
void __svm_invlpga(void *Va, int ASID);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Va*|[in]要使其失效之頁面的虛擬位址。|
|*ASID*|[in]位址空間的識別項 (ASID) 頁面，即可使其失效。|

## <a name="remarks"></a>備註

`__svm_invlpga` 函式相當於 `INVLPGA` 機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計中，「 文件數目 24593，修訂 3.11，位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站台。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_invlpga`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)