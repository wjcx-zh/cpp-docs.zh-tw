---
title: _open_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _open_osfhandle
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs: C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff05c99180ff8933316e1db9366da3b985c10305
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="openosfhandle"></a>_open_osfhandle

將 C 執行階段檔案描述項與現有的作業系統檔案控制代碼建立關聯。

## <a name="syntax"></a>語法

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>參數

*osfhandle*  
作業系統檔案控制代碼。

*flags*  
允許的作業類型。

## <a name="return-value"></a>傳回值

如果成功，`_open_osfhandle` 會傳回 C 執行階段檔案描述項。 否則，它會傳回-1。

## <a name="remarks"></a>備註

`_open_osfhandle`函式配置的 C 執行階段檔案描述元，並將其與所指定的作業系統檔案控制代碼相關聯*osfhandle*。 *旗標*引數是由一或多個.h 中定義的資訊清單常數形成的整數運算式。 當兩個或多個資訊清單常數用於表單*旗標*引數，會使用位元 OR 運算子結合常數 ( **&#124;** )。

.H 會定義下列資訊清單常數：

**\_O\_附加**  
在每次寫入作業之前，將檔案指標置放到檔案的結尾。

**\_O\_RDONLY**  
開啟檔案為僅供讀取。

**\_O\_文字**  
以文字 (已轉譯) 模式開啟檔案。

**\_O\_WTEXT**  
以 Unicode (已轉譯 UTF-16) 模式開啟檔案。

若要關閉檔案，以開啟`_open_osfhandle`，呼叫[\_關閉](../../c-runtime-library/reference/close.md)。 藉由呼叫也會關閉基礎的作業系統檔案控制代碼`_close`，因此不需要呼叫 Win32 函式`CloseHandle`原始的控制代碼上。 如果所擁有的檔案描述項`FILE *`資料流，然後呼叫[fclose](../../c-runtime-library/reference/fclose-fcloseall.md)上`FILE *`的檔案描述項和基礎控制代碼，也會關閉資料流。 在此情況下，請勿呼叫`_close`上的檔案描述項。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_open_osfhandle`|\<io.h>|

如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)  
