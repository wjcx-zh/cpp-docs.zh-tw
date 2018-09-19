---
title: 編譯器錯誤 C3552 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd9f7ae37500e115fa33fa61298cab800c88f9c7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081256"
---
# <a name="compiler-error-c3552"></a>編譯器錯誤 C3552

'typename': 晚期指定的傳回類型不能包含 'auto'

如果您使用 `auto` 關鍵字作為函式之傳回類型的預留位置，則必須提供晚期指定的傳回類型。 不過，您無法使用另一個 `auto` 關鍵字來指定晚期指定的傳回類型。 例如，下列程式碼片段會產生錯誤 C3552。

`auto myFunction->auto; // C3552`