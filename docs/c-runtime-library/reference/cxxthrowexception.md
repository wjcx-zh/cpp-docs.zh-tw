---
title: _CxxThrowException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd3ab2994359e99e490422fbb2f11cf28a05d6e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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

*pExceptionObject*產生例外狀況的物件。

*pThrowInfo*處理例外狀況所需的資訊。

## <a name="remarks"></a>備註

此方法包含在編譯器用來處理例外狀況的僅限編譯器檔案中。 請勿從您的程式碼直接呼叫此方法。

## <a name="requirements"></a>需求

**來源︰**Throw.cpp

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
