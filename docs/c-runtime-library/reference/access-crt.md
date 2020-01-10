---
title: access (CRT)
ms.date: 12/16/2019
api_name:
- access
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
- access
helpviewer_keywords:
- access function
ms.assetid: 65197793-bd0a-41c3-9c29-18de2d95d9a6
ms.openlocfilehash: 0f218b8de79ea174d935097c6ecbe4cf303db7a2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300114"
---
# <a name="access-crt"></a>access (CRT)

Microsoft 所實行的 POSIX 函數名稱 `access` 是[_access](access-waccess.md)函式的已被取代別名。 根據預設，它會產生[編譯器警告（層級3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名稱已被取代，因為它不會遵循執行特定名稱的標準 C 規則。 不過，仍支援函數。

我們建議您改用[_access](access-waccess.md)或增強安全性的[_access_s](access-s-waccess-s.md)函數。 或者，您可以繼續使用此函數名稱，並停用警告。 如需詳細資訊，請參閱[關閉警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函數名稱](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。
