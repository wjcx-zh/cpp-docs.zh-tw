---
title: 運算錯誤 M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: b8a3a4ab87a410c4cee8f7e4a1a0517c169d0364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173656"
---
# <a name="math-error-m6202"></a>運算錯誤 M6202

' function '： _SING 錯誤

給定函式的引數是此函式的 singularity 值。 未定義該引數的函式。

此錯誤會使用函式名稱、其引數和錯誤類型來呼叫 `_matherr` 函式。 您可以重寫 `_matherr` 函式，以自訂特定執行時間浮點運算錯誤的處理。
