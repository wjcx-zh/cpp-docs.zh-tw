---
title: _CxxThrowException
ms.date: 11/04/2016
apiname:
- _CxxThrowException
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
apitype: DLLExport
f1_keywords:
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: 925b72a120b31029b76fa38bee73eea003511cd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288569"
---
# <a name="cxxthrowexception"></a>_CxxThrowException

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

**來源：** Throw.cpp

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
