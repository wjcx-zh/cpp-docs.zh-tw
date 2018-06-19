---
title: 編譯器警告 （層級 3） C4622 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4622
dev_langs:
- C++
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b82e87f37b50b8df727d043889cb35ca02d3f78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291537"
---
# <a name="compiler-warning-level-3-c4622"></a>編譯器警告 (層級 3) C4622
覆寫在目的檔中建立先行編譯標頭檔期間產生的偵錯資訊: 'file'  
  
 所指定檔案中的 CodeView 資訊在使用 [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (使用先行編譯標頭檔) 選項編譯時遺失。  
  
 建立或使用先行編譯標頭檔時，請重新命名物件檔案 (使用 [/Fo](../../build/reference/fo-object-file-name.md))，或者使用新的物件檔案進行連結。