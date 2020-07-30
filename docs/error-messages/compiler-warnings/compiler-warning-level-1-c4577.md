---
title: 編譯器警告 C4577
description: 編譯器警告 C4577 描述和解決方案。
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: fb9d412196e7764326a397a4bf6e76c8723ac2ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196249"
---
# <a name="compiler-warning-level-1-c4577"></a>編譯器警告（層級1） C4577

> 使用了 ' noexcept '，但未指定例外狀況處理模式;不保證例外狀況的終止。 指定/EHsc

編譯器偵測到 **`noexcept`** 規格，但未指定標準 c + + 例外狀況處理。 除非指定了[/ehsc](../../build/reference/eh-exception-handling-model.md)編譯器選項，否則編譯器不會完全支援根據 c + + 標準的例外狀況處理。 若要解決此問題，請設定 **/ehsc**編譯器選項。

這項警告是 Visual Studio 2015 中的新功能，預設為關閉。 如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
