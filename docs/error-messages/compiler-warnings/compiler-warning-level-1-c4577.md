---
title: 編譯器警告 C4577
description: 編譯器警告 C4577 描述和解決方案。
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: e29e47b2a268d86f7f6a280b79a1604fe6eff8a4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810566"
---
# <a name="compiler-warning-level-1-c4577"></a>編譯器警告（層級1） C4577

> 使用了 ' noexcept '，但未指定例外狀況處理模式;不保證例外狀況的終止。 指定/EHsc

編譯器偵測到 `noexcept` 規格，但未指定C++標準例外狀況處理。 除非指定了[/ehsc](../../build/reference/eh-exception-handling-model.md)編譯器選項，否則編譯器不C++會完全支援根據標準的例外狀況處理。 若要解決此問題，請設定 **/ehsc**編譯器選項。

這項警告是 Visual Studio 2015 中的新功能，預設為關閉。 如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
