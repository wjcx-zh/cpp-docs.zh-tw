---
title: __argc、__argv、__wargv
ms.date: 11/04/2016
api_name:
- __wargv
- __argv
- __argc
api_location:
- msvcrt120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
ms.openlocfilehash: 59ab1f5ba52e6dc84d44e8cb5465cfa412d01895
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940629"
---
# <a name="__argc-__argv-__wargv"></a>__argc、__argv、__wargv

`__argc` 全域變數是傳遞至程式之命令列引數數目的計數。 `__argv` 是單一位元組字元陣列，或包含程式引數的多位元組字元字串陣列的指標，`__wargv` 是包含程式引數之寬字元字串陣列的指標。 這些全域變數會提供引數給 `main` 或 `wmain`。

## <a name="syntax"></a>語法

```
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>備註

在使用 `main` 函式的程式中，會使用啟動程式所用的命令列，在程式啟動時初始化 `__argc` 和 `__argv`。 此命令列會剖析成各個引數，且會展開萬用字元。 引數的計數會指派至 `__argc` 且引數字串會配置到堆積上，而引數陣列的指標會指派至 `__argv`。 在編譯為使用寬字元及 `wmain` 函式的程式中，會剖析引數並將萬用字元展開為寬字元字串，且引數字串陣列的指標會指派至 `__wargv`。

我們建議您針對可攜式程式碼使用傳遞至 `main` 的引數，以在程式中取得命令列引數。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|_UNICODE 未定義|_UNICODE 已定義|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>需求

|全域變數|必要的標頭|
|---------------------|---------------------|
|`__argc`、`__argv`、`__wargv`|\<stdlib.h>、\<cstdlib> (C++)|

`__argc`、`__argv` 和 `__wargv` 是 Microsoft 擴充功能。 如需相容性資訊，請參閱 [相容性](../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[全域變數](../c-runtime-library/global-variables.md)<br/>
[主要：程式啟動](../cpp/main-program-startup.md)<br/>
[使用 wmain 取代 main](../cpp/using-wmain-instead-of-main.md)
