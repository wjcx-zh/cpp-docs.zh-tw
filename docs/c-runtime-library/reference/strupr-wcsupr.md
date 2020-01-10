---
title: strupr、wcsupr
ms.date: 12/16/2019
api_name:
- strupr
- wcsupr
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
- strupr
- wcsupr
helpviewer_keywords:
- strupr function
- wcsupr function
ms.assetid: 17dfe1cd-3b09-4702-9f89-2207f44953e6
ms.openlocfilehash: ce51eb4f7eeb80766e19cfdb4a39a3a7dd50d85a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300452"
---
# <a name="strupr-wcsupr"></a>strupr、wcsupr

Microsoft 特有的函式名稱 `strupr` 和 `wcsupr` 已取代[_strupr 和 _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)函數的別名。 根據預設，它們會產生[編譯器警告（層級3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名稱已被取代，因為它們不會遵循執行特定名稱的標準 C 規則。 不過，仍然支援函數。

我們建議您改用[_strupr 和 _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)或增強安全性的[_strupr_s 和 _wcsupr_s](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)功能。 或者，您可以繼續使用這些函數名稱，並停用警告。 如需詳細資訊，請參閱[關閉警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函數名稱](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
