---
title: 編譯器警告 （層級 4） C4152 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4152
dev_langs:
- C++
helpviewer_keywords:
- C4152
ms.assetid: 6025ab70-d7cf-4730-913a-3ca0b1186a3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faa258b7dbd965f0aaa76d4b60bb5c043df1187f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291160"
---
# <a name="compiler-warning-level-4-c4152"></a>編譯器警告 (層級 4) C4152
非標準的擴充，運算式中函式/資料的指標轉換  
  
 函式指標會轉換成資料指標，反之亦然。 Microsoft 擴充功能 (/Ze) 下允許這項轉換，但 ANSI C 下則不允許。