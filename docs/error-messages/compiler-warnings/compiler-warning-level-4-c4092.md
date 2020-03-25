---
title: 編譯器警告（層級4） C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 6786d692785dbca575d4b241b7b3e3d40575b686
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198545"
---
# <a name="compiler-warning-level-4-c4092"></a>編譯器警告（層級4） C4092

sizeof 會傳回「不帶正負號的長」

`sizeof` 運算子的運算元非常大，因此 `sizeof` 傳回不帶正負號的**長**整數。 此警告會出現在 Microsoft extensions （[/ze](../../build/reference/za-ze-disable-language-extensions.md)）底下。 在 ANSI 相容性（/Za）底下，會改為截斷結果。
