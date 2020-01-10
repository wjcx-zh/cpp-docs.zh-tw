---
title: spawnve
ms.date: 12/16/2019
api_name:
- spawnve
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
- spawnve
helpviewer_keywords:
- spawnve function
ms.assetid: 39507df8-f15f-45fb-b2b6-01359272b147
ms.openlocfilehash: 0b4171a4e10eb390f901c1246d3a2207da2513c4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300660"
---
# <a name="spawnve"></a>spawnve

Microsoft 特有的函式名稱 `spawnve` 是[_spawnve](spawnve-wspawnve.md)函數的已被取代別名。 根據預設，它會產生[編譯器警告（層級3） C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 名稱已被取代，因為它不會遵循執行特定名稱的標準 C 規則。 不過，仍支援函數。

我們建議您改用[_spawnve](spawnve-wspawnve.md) 。 或者，您可以繼續使用此函數名稱，並停用警告。 如需詳細資訊，請參閱[關閉警告](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)和[POSIX 函數名稱](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。
