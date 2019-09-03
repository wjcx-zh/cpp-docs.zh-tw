---
title: __svm_skinit
ms.date: 09/02/2019
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 6657921d647a23bf027a5800702527951f7f6831
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219864"
---
# <a name="__svm_skinit"></a>__svm_skinit

**Microsoft 專屬**

起始載入可驗證的安全軟體, 例如虛擬機器監視器。

## <a name="syntax"></a>語法

```C
void __svm_skinit(
   int block_address
);
```

### <a name="parameters"></a>參數

*block_address*\
64K 位元組安全載入器區塊 (SLB) 的32位實體位址。

## <a name="remarks"></a>備註

`__svm_skinit` 函式相當於 `SKINIT` 機器指令。 此函式是使用處理器和信賴平臺模組 (TPM) 的安全性系統的一部分, 用來驗證和載入受信任的軟體, 稱為*安全性核心*(SK)。 虛擬機器監視是安全性核心的範例。 安全性系統會驗證在初始化過程中載入的程式元件。 如果電腦是多處理器, 它會保護元件不受中斷、裝置存取或其他程式的篡改。

*Block_address*參數會指定64個記憶體區塊的實體位址, 稱為*安全載入器區塊*(SLB)。 SLB 包含稱為「*安全載入*器」的程式。 它會為電腦建立操作環境, 然後載入安全性核心。

這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊, 請搜尋「AMD64 架構程式設計人員手冊第2卷:系統程式設計, 位於[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)網站。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__svm_skinit`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
