---
title: 編譯器錯誤 C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: f6e33d0e0ee139138df7d8e11357100b3ec3a1a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593436"
---
# <a name="compiler-error-c2818"></a>編譯器錯誤 C2818

多載 'operator ->' 透過類型 'type' 遞迴應用

類別成員存取運算子的重複定義包含遞迴`return`陳述式。 若要重新定義`->`運算子進行遞迴時，您必須移動到個別函式呼叫運算子的遞迴常式覆寫函式。