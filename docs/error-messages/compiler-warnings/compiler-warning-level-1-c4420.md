---
title: 編譯器警告 (層級 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: a4a7e91e7845cc0fc25d5a6fad16ae7b7e327952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408169"
---
# <a name="compiler-warning-level-1-c4420"></a>編譯器警告 (層級 1) C4420

'operator': 無法使用運算子，改用 'operator';執行階段檢查可能無法執行

當您使用時，會產生這個警告[/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector 檢查新增/刪除)，且當找到沒有向量格式。 在此情況下，使用非向量格式。

為了讓 /RTCv 才能正常運作，編譯器一定要呼叫的向量形式[新](../../cpp/new-operator-cpp.md)/[刪除](../../cpp/delete-operator-cpp.md)就如同已在使用向量語法。