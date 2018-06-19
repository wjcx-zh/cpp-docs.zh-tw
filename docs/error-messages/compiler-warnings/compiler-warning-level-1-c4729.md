---
title: 編譯器警告 (層級 1) C4729 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02ccbb80a44123498a231c1909c9c2c6fca72a24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281738"
---
# <a name="compiler-warning-level-1-c4729"></a>編譯器警告 (層級 1) C4729
依據 flow graph 產生的警告，發現函式太大  
  
 如果要編譯的函式太大，無法可靠地檢查將產生警告的情況，則會產生這個警告。 使用 [/Od](../../build/reference/od-disable-debug.md) 編譯器選項時，才會產生這個警告。  
  
 若要解決這個警告，請將函式分為較小的函式。