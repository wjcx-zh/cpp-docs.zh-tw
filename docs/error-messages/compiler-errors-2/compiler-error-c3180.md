---
title: 編譯器錯誤 C3180 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3180
dev_langs:
- C++
helpviewer_keywords:
- C3180
ms.assetid: 5281f583-7df7-418a-8507-d4da67ed6572
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e200a75164c0d7fdb0c6804d084630cc6e6007e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048366"
---
# <a name="compiler-error-c3180"></a>編譯器錯誤 C3180

'type name': 名稱超過中繼資料 'limit' 個字元的限制

編譯器會截斷在中繼資料中的 managed 類型的名稱。 截斷會造成類型無法使用`#using`指示詞 （或另一種語言的對等項目）。

類型名稱限制包含任何命名空間限定性條件。