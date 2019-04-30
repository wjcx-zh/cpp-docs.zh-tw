---
title: 編譯器錯誤 C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: f6e33d0e0ee139138df7d8e11357100b3ec3a1a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388692"
---
# <a name="compiler-error-c2818"></a>編譯器錯誤 C2818

應用程式的多載 'operator->' 是遞迴式，透過類型 'type'

類別成員存取運算子的重複定義包含遞迴`return`陳述式。 若要重新定義`->`運算子進行遞迴時，您必須移動到個別函式呼叫運算子的遞迴常式覆寫函式。