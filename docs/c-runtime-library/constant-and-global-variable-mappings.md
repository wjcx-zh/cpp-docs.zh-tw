---
title: 常數和全域變數對應
ms.date: 11/04/2016
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
ms.openlocfilehash: 0f4e41e652cc1154b3bbc1ae3ca20c143e2745ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646182"
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