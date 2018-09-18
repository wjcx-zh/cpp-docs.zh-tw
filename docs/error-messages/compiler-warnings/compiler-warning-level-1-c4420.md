---
title: 編譯器警告 （層級 1） C4420 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1ba4ef4c4fc006e1a5950d0d16dc530ccc06a1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049744"
---
# <a name="compiler-warning-level-1-c4420"></a>編譯器警告 (層級 1) C4420

'operator': 無法使用運算子，改用 'operator';執行階段檢查可能無法執行

當您使用時，會產生這個警告[/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector 檢查新增/刪除)，且當找到沒有向量格式。 在此情況下，使用非向量格式。

為了讓 /RTCv 才能正常運作，編譯器一定要呼叫的向量形式[新](../../cpp/new-operator-cpp.md)/[刪除](../../cpp/delete-operator-cpp.md)就如同已在使用向量語法。