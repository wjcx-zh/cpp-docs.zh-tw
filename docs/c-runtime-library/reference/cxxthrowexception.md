---
title: _CxxThrowException
ms.date: 11/04/2016
api_name:
- _CxxThrowException
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: a5b614d25502ddd5a58aedcf2ec843b2b1ab9d47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942030"
---
# <a name="_cxxthrowexception"></a>_CxxThrowException

建立例外狀況記錄，並呼叫執行階段環境以開始處理例外狀況。

## <a name="syntax"></a>語法

```C
extern "C" void __stdcall _CxxThrowException(
   void* pExceptionObject
   _ThrowInfo* pThrowInfo
);
```

### <a name="parameters"></a>參數

*pExceptionObject*<br/>
產生例外狀況的物件。

*pThrowInfo*<br/>
處理例外狀況所需的資訊。

## <a name="remarks"></a>備註

此方法包含在編譯器用來處理例外狀況的僅限編譯器檔案中。 請勿從您的程式碼直接呼叫此方法。

## <a name="requirements"></a>需求

**來源**Throw .cpp

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
