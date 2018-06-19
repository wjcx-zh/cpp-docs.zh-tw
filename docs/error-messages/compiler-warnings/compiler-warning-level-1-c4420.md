---
title: 編譯器警告 （層級 1） C4420 |Microsoft 文件
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
ms.openlocfilehash: 98336a30e7174b62df48e93a04ba9ee7ddcc919a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279106"
---
# <a name="compiler-warning-level-1-c4420"></a>編譯器警告 (層級 1) C4420
'operator': 無法使用運算子，改用 'operator';執行階段檢查可能無法執行  
  
 當您使用時，會產生這個警告[/RTCv](../../build/reference/rtc-run-time-error-checks.md) （向量檢查新增/刪除），且當找到沒有向量格式。 在此情況下，使用非向量格式。  
  
 為了讓 /RTCv 正常運作，則編譯器應該一律呼叫向量形式的[新](../../cpp/new-operator-cpp.md)/[刪除](../../cpp/delete-operator-cpp.md)就如同已在使用向量語法。