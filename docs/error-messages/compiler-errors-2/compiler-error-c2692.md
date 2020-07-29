---
title: 編譯器錯誤 C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: a82ee0bead9e4e7a92c16df89eee86288f562de9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216098"
---
# <a name="compiler-error-c2692"></a>編譯器錯誤 C2692

' function_name '：具有 '/clr ' 選項之 C 編譯器所需的完整原型函式

針對 .NET managed 程式碼進行編譯時，C 編譯器需要 ANSI 函式宣告。 此外，如果函式不接受任何參數，則必須明確宣告 **`void`** 為參數類型。
