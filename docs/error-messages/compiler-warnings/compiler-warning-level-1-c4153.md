---
title: 編譯器警告 （層級 1） C4153 |Microsoft 文件
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
ms.openlocfilehash: 1193bc56b7de45675eb1d09e7c48c19d681119d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276236"
---
# <a name="compiler-warning-level-1-c4153"></a>編譯器警告 (層級 1) C4153
運算式中函式/資料的指標轉換  
  
 函式指標會轉換成資料指標，反之亦然。 Microsoft 擴充功能 (/Ze) 下允許這項轉換，但 ANSI C 下則不允許。