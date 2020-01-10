---
title: stricmp、wcsicmp
ms.date: 12/16/2019
api_name:
- stricmp
- wcsicmp
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
- stricmp
- wcsicmp
helpviewer_keywords:
- stricmp function
- wcsicmp function
ms.assetid: 2e3c6703-2635-4961-a253-e2c4c5029ed8
ms.openlocfilehash: d47249a3b41c76bf87ece8ed2e8a0fbbfc05ff09
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300504"
---
# <a name="stricmp-wcsicmp"></a>stricmp、wcsicmp

Microsoft 特有的函式名稱 `stricmp` 和 `wcsicmp` 已取代[_stricmp 和 _wcsicmp](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)函數的別名。 根據預設，它們會產生[編譯器警告（層級3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名稱已被取代，因為它們不會遵循執行特定名稱的標準 C 規則。 不過，仍然支援函數。

我們建議您改用[_stricmp 或 _wcsicmp](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md) 。 或者，您可以繼續使用這些函數名稱，並停用警告。 如需詳細資訊，請參閱[關閉警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函數名稱](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
