---
title: 編譯器錯誤 C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: d2d3a60fcd4a26238cd6cf330f47b48c5b3198ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230827"
---
# <a name="compiler-error-c3552"></a>編譯器錯誤 C3552

'typename': 晚期指定的傳回類型不能包含 'auto'

如果您使用關鍵字做為函式 **`auto`** 之傳回型別的預留位置，則必須提供晚期指定的傳回型別。 不過，您不能使用另一個 **`auto`** 關鍵字來指定晚期指定的傳回型別。 例如，下列程式碼片段會產生錯誤 C3552。

`auto myFunction->auto; // C3552`
