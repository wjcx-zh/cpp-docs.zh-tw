---
title: 編譯器錯誤 C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: c92a95b97cb4c57d3ad5cfbf8fe1d9980d5362cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221207"
---
# <a name="compiler-error-c2338"></a>編譯器錯誤 C2338

> *錯誤訊息*

此錯誤可能是 **`static_assert`** 在編譯期間發生錯誤所造成。 此訊息是由參數所提供 **`static_assert`** 。

外部提供者也可以產生此錯誤訊息給編譯器。 在大部分的情況下，屬性提供者 DLL （例如 ATLPROV）會報告這些錯誤。 此訊息的一些常見形式包括：

- '*attribute*' Atl 屬性提供者：錯誤 atl*數位**訊息*

- 屬性 '*attribute*' 的使用不正確

- '*usage*'：屬性 ' usage ' 的格式不正確

這些錯誤通常無法復原，而且後面可能會發生嚴重的編譯器錯誤。

若要修正這些問題，請更正屬性使用方式。 例如，在某些情況下，必須先宣告屬性參數，才能使用它們。 如果提供了 ATL 錯誤號碼，請查看該錯誤的檔，以取得更具體的資訊。
