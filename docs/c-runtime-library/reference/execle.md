---
title: execle
ms.date: 12/16/2019
api_name:
- execle
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
- execle
helpviewer_keywords:
- execle function
ms.assetid: 5985b615-fe90-4d1c-9c1d-13ec87c8e306
ms.openlocfilehash: 1d97d847ae16c0f0224eca9fba42ad1ab5452b10
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299776"
---
# <a name="execle"></a>execle

Microsoft 所實行的 POSIX 函數名稱 `execle` 是[_execle](execle-wexecle.md)函式的已被取代別名。 根據預設，它會產生[編譯器警告（層級3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名稱已被取代，因為它不會遵循執行特定名稱的標準 C 規則。 不過，仍支援函數。

我們建議您改用[_execle](execle-wexecle.md) 。 或者，您可以繼續使用此函數名稱，並停用警告。 如需詳細資訊，請參閱[關閉警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函數名稱](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。
