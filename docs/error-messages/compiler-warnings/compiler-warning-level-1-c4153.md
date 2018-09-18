---
title: 編譯器警告 （層級 1） C4153 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4153
dev_langs:
- C++
helpviewer_keywords:
- C4153
ms.assetid: 37a15754-9dba-470b-adda-c4b888064b3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99aa207c550004eee1db906acf5dc567e9859f7c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074080"
---
# <a name="compiler-warning-level-1-c4153"></a>編譯器警告 (層級 1) C4153

運算式中函式/資料的指標轉換

函式指標會轉換成資料指標，反之亦然。 Microsoft 擴充功能 (/Ze) 下允許這項轉換，但 ANSI C 下則不允許。