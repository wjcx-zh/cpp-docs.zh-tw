---
title: 編譯器警告 (層級 1) C4711
ms.date: 11/04/2016
f1_keywords:
- C4711
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
ms.openlocfilehash: 9e2adf3583012a670f936c2b86a9ddc393fe53c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175333"
---
# <a name="compiler-warning-level-1-c4711"></a>編譯器警告 (層級 1) C4711

函式 'function' 被指定為自動內嵌展開

編譯器會在指定的函式上執行內嵌作業，但未標示為內嵌。

如果已指定[/Ob2](../../build/reference/ob-inline-function-expansion.md) ，則會啟用 C4711。

內嵌是以編譯器的判斷來執行。 這個警告僅供參考。

此警告預設為關閉。 若要啟用警告，請使用[#pragma 警告](../../preprocessor/warning.md)。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。
