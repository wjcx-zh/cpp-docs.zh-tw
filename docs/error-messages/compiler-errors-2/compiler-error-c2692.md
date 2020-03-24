---
title: 編譯器錯誤 C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 7ce57cd50e9ec83cf80ec64e14f49eb9714f9208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177088"
---
# <a name="compiler-error-c2692"></a>編譯器錯誤 C2692

' function_name '：具有 '/clr ' 選項之 C 編譯器所需的完整原型函式

針對 .NET managed 程式碼進行編譯時，C 編譯器需要 ANSI 函式宣告。 此外，如果函式不接受任何參數，則必須明確地將 `void` 宣告為參數類型。
