---
title: 嚴重錯誤 C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 110fbfe984ee7714e0c8ee2e2cb4deec4f43905a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207923"
---
# <a name="fatal-error-c1126"></a>嚴重錯誤 C1126

' identifier '：自動設定超過大小

為函式的區域變數（加上編譯器所使用的空間數量限制）所配置的空間（例如，用於交換函式的額外20個位元組）超過限制。

若要更正此錯誤，請使用 `malloc` 或 **`new`** 來配置大量資料。
