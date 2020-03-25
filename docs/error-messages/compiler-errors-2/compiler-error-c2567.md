---
title: 編譯器錯誤 C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 921992c678c1de0b74f99f544173478ebe809b2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177452"
---
# <a name="compiler-error-c2567"></a>編譯器錯誤 C2567

無法開啟 ' file ' 中的中繼資料，檔案可能已被刪除或移動

編譯器後端進程在相同的目錄中找不到來源（具有 `#using`）所參考的中繼資料檔，如同編譯器前端進程一樣。 如需詳細資訊，請參閱[#using](../../preprocessor/hash-using-directive-cpp.md)指示詞。

如果您在一部電腦上使用 **/c**進行編譯，然後在另一部電腦上嘗試產生連結時程式碼，可能會導致 C2567。 如需詳細資訊，請參閱[/ltcg （連結時產生程式碼）](../../build/reference/ltcg-link-time-code-generation.md)）。

這也可能表示您的電腦沒有足夠的記憶體。

若要更正這個錯誤，請確定中繼資料檔案位於相同的目錄位置，以用於建立程式的所有階段。
