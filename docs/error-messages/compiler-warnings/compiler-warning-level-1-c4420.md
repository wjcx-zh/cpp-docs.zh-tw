---
title: 編譯器警告 (層級 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 72ab87b34e07717112f5af1727a216b4f786ae0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186786"
---
# <a name="compiler-warning-level-1-c4420"></a>編譯器警告 (層級 1) C4420

' operator '：無法使用運算子，請改用 ' operator ';執行時間檢查可能會受到危害

當您使用[/RTCv](../../build/reference/rtc-run-time-error-checks.md) （向量新增/刪除檢查）時，如果找不到向量形式，就會產生這個警告。 在此情況下，會使用非向量形式。

若要讓/RTCv 正確運作，編譯器應一律呼叫向量形式的[new](../../cpp/new-operator-cpp.md)/[delete](../../cpp/delete-operator-cpp.md) （如果已使用向量語法）。
