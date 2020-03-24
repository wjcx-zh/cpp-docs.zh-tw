---
title: 運算錯誤 M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 371a6c673826c6ce71d7a0eb3b9e08d9488f53f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193689"
---
# <a name="math-error-m6203"></a>運算錯誤 M6203

' function '： _OVERFLOW 錯誤

給定的函式結果太大而無法表示。

此錯誤會使用函式名稱、其引數和錯誤類型來呼叫 `_matherr` 函式。 您可以重寫 `_matherr` 函式，以自訂特定執行時間浮點運算錯誤的處理。
