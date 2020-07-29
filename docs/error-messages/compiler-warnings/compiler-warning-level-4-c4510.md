---
title: 編譯器警告 (層級 4) C4510
description: 編譯器警告 C4510 描述和解決方案。
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: e4bb688266d9fe638978d2d3fa2666b83b3e6cc9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225250"
---
# <a name="compiler-warning-level-4-c4510"></a>編譯器警告 (層級 4) C4510

> '*class*'：無法產生預設的構造函式

編譯器無法針對指定的類別產生預設的函式，因為沒有任何使用者定義的函數。 無法建立此類型的物件。

有幾種情況會讓編譯器無法產生預設的程式，包括：

- **`const`** 資料成員。

- 參考的資料成員。

若要修正此問題，請為初始化這些成員的類別建立使用者定義的預設函式。
