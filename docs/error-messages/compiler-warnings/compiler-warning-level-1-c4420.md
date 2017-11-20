---
title: "編譯器警告 （層級 1） C4420 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4420
dev_langs: C++
helpviewer_keywords: C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 646e87243e6901827fb2d36076a95e6bcb63c3ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4420"></a>編譯器警告 (層級 1) C4420
'operator': 無法使用運算子，改用 'operator';執行階段檢查可能無法執行  
  
 當您使用時，會產生這個警告[/RTCv](../../build/reference/rtc-run-time-error-checks.md) （向量檢查新增/刪除），且當找到沒有向量格式。 在此情況下，使用非向量格式。  
  
 為了讓 /RTCv 正常運作，則編譯器應該一律呼叫向量形式的[新](../../cpp/new-operator-cpp.md)/[刪除](../../cpp/delete-operator-cpp.md)就如同已在使用向量語法。