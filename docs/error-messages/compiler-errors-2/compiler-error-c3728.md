---
title: 編譯器錯誤 C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 8aec3ae1ff629ef7fa000182cde29e306a471315
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165870"
---
# <a name="compiler-error-c3728"></a>編譯器錯誤 C3728

' event '：事件沒有 raise 方法

以語言建立的中繼資料（例如C#）不允許從其定義所在的類別外引發事件、包含在[#using](../../preprocessor/hash-using-directive-cpp.md)指示詞中，以及使用 CLR 程式設計的視覺化C++程式嘗試引發事件。

若要在以語言（例如C#）開發的程式中引發事件，包含事件的類別也必須定義引發事件的公用方法。
