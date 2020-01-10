---
title: strdup、wcsdup
ms.date: 12/16/2019
api_name:
- wcsdup
- strdup
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
- wcsdup
- strdup
helpviewer_keywords:
- wcsdup function
- strdup function
ms.assetid: c9ac0935-b525-4e95-8a64-396fc7e34ee9
ms.openlocfilehash: e381a1933a6b657108a66053bad1c7ff795c1a29
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300517"
---
# <a name="strdup-wcsdup"></a>strdup、wcsdup

Microsoft 所實行的 POSIX 函式名稱 `strdup` 和 `wcsdup` 已取代[_strdup 和 _wcsdup](strdup-wcsdup-mbsdup.md)函數的別名。 根據預設，它們會產生[編譯器警告（層級3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名稱已被取代，因為它們不會遵循執行特定名稱的標準 C 規則。 不過，仍然支援函數。

我們建議您改用[_strdup 並 _wcsdup](strdup-wcsdup-mbsdup.md) 。 或者，您可以繼續使用這些函數名稱，並停用警告。 如需詳細資訊，請參閱[關閉警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函數名稱](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
