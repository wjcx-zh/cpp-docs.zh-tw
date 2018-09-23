---
title: 常數和全域變數對應 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
dev_langs:
- C++
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94cee77f82f850560cc5fe50e13b85c58b7187ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077840"
---
# <a name="constant-and-global-variable-mappings"></a>常數和全域變數對應

這些泛型文字常數、全域變數和標準類型對應都是在 TCHAR.H 中定義，並視程式中是否定義常數 `_UNICODE` 或 `_MBCS` 而定。

### <a name="generic-text-constant-and-global-variable-mappings"></a>泛型文字常數和全域變數對應

|泛型文字 - 物件名稱|SBCS (_UNICODE、_MBCS 未定義)|_MBCS 已定義|_UNICODE 已定義|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TEOF`|`EOF`|`EOF`|`WEOF`|
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="see-also"></a>請參閱

[泛型文字對應](../c-runtime-library/generic-text-mappings.md)<br/>
[資料類型對應](../c-runtime-library/data-type-mappings.md)<br/>
[常式對應](../c-runtime-library/routine-mappings.md)<br/>
[泛型文字程式範例](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[使用泛型文字對應](../c-runtime-library/using-generic-text-mappings.md)