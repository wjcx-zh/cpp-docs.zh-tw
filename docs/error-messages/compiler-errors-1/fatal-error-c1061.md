---
title: 嚴重錯誤 C1061
ms.date: 11/04/2016
f1_keywords:
- C1061
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
ms.openlocfilehash: 049adb38dd8f33de7dbdd02d8420eba284ca2ca1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204408"
---
# <a name="fatal-error-c1061"></a>嚴重錯誤 C1061

編譯器限制：區塊巢狀結構太深

程式碼區塊的巢狀結構超過 128 層的限制。 這是在 32 位元和 64 位元工具集中，C 和 C++ 編譯器的一種硬性限制。 任何建立範圍或區塊的項目皆會增加巢狀層次的計數。 例如，命名空間、using 指示詞、前置處理器展開、範本展開、例外狀況處理、迴圈建構及 else-if 子句，皆可能呼叫增加編譯器所看到的巢狀層次。

若要更正這個錯誤，您必須重構程式碼。 在任何情況下，深度巢狀程式碼都不容易了解及說明。 重構程式碼以減少巢狀層次，如可改善程式碼品質，並簡化維護工作。 將深度巢狀程式碼分為從原始內容呼叫的函式。 限制區塊中迴圈數目或鏈結的 else-if 子句。
