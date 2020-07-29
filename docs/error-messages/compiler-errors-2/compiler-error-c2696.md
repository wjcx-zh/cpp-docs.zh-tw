---
title: 編譯器錯誤 C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: f6af217dbcd871ac4edd1852042144802388545b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216085"
---
# <a name="compiler-error-c2696"></a>編譯器錯誤 C2696

無法建立 managed 類型 ' type ' 的暫存物件

**`const`** 在非受控程式中的參考會導致編譯器呼叫此函式，並在堆疊上建立暫存物件。 不過，無法在堆疊上建立 managed 類別。

C2696 只能使用過時的編譯器選項 **/clr： oldSyntax**來連線。
