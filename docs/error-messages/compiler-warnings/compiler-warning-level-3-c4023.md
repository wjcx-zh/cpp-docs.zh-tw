---
title: 編譯器警告 （層級 3） C4023 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4023
dev_langs:
- C++
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 213d72e39575b447787c3e0ead7910baedc8e815
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289993"
---
# <a name="compiler-warning-level-3-c4023"></a>編譯器警告 (層級 3) C4023
'symbol' : 基底指標傳送至沒有原型的函式 : 參數號碼  
  
 將基底指標傳送至沒有原型的函式會導致指標正規化，但結果無法預期。  
  
 如果您針對要傳送的基底指標使用原型函式，則可以修正這個警告。