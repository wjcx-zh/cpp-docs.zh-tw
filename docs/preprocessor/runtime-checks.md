---
title: runtime_checks pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: a1c8e6cca27e157818e6ec80182f8fefa112daf1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216615"
---
# <a name="runtime_checks-pragma"></a>runtime_checks pragma

停用或還原 [/RTC](../build/reference/rtc-run-time-error-checks.md) 設定。

## <a name="syntax"></a>語法

> **#pragma runtime_checks ("** [ *runtime_checks* ] **",** { **restore**  |  **off** } **)**

## <a name="remarks"></a>備註

您無法啟用編譯器選項未啟用的執行時間檢查。 例如, 如果您未在命令`/RTCs`行上指定, 指定`#pragma runtime_checks( "s", restore)`將不會啟用堆疊框架驗證。

**Runtime_checks** pragma 必須出現在函式之外, 並且會在看到 pragma 之後定義的第一個函式生效。 **restore** 和 **off** 引數可開啟或關閉在 **runtime_checks** 中指定的選項。

**runtime_checks** 可以是下表所示的零個或多個參數。

### <a name="parameters-of-the-runtime_checks-pragma"></a>runtime_checks Pragma 的參數

| 參數 | 執行階段檢查的類型 |
|--------------------|-----------------------------|
| **秒** | 啟用堆疊 (框架) 驗證。 |
| **C** | 將值指派給會造成資料損失的較小資料類型時回報。 |
| **u** | 在定義變數之前使用它的報表。 |

這些參數與`/RTC`編譯器選項所使用的參數相同。 例如：

```cpp
#pragma runtime_checks( "sc", restore )
```

使用 **runtime_checks** pragma 搭配空字串 ( **""** ) 是一種特殊形式的指示詞：

- 當您使用**off**參數時, 它會將上表所列的執行階段錯誤檢查關閉。

- 當您使用**restore**參數時, 它會將執行階段錯誤檢查重設為您使用`/RTC`編譯器選項所指定的檔案。

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
