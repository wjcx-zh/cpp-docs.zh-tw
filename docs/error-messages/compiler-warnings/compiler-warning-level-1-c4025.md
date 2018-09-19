---
title: 編譯器警告 （層級 1） C4025 |Microsoft Docs
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
ms.openlocfilehash: 109f1694f63488c167e51c7c2c89675411b6d269
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045571"
---
# <a name="compiler-warning-level-1-c4025"></a>編譯器警告 (層級 1) C4025

'number': 基底指標傳遞至擁有變數引數的函式: 參數號碼

將基底指標傳遞至具有變數引數的函式會導致指標正規化，但結果無法預期。 請不要將基底指標傳遞至具有變數引數的函式。