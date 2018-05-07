---
title: 編譯器警告 （層級 1） C4025 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4025
dev_langs:
- C++
helpviewer_keywords:
- C4025
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e84ba11c7bed7420a9a1c699361612ef2002d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4025"></a>編譯器警告 (層級 1) C4025
'number': 基底指標傳遞至擁有變數引數的函式: 參數號碼  
  
 將基底指標傳遞至具有變數引數的函式會導致指標正規化，但結果無法預期。 請不要將基底指標傳遞至具有變數引數的函式。