---
title: 連結器工具警告 LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: d0205ba065f6e410383c38a0f1c2eaa0da55fe93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173864"
---
# <a name="linker-tools-warning-lnk4286"></a>連結器工具警告 LNK4286

> '*filename_1 .obj*' 中定義的符號 '*symbol*' 由 '*filename_2 .obj*' 匯入

已為*符號*指定[__declspec （dllimport）](../../cpp/dllexport-dllimport.md) ，即使在相同影像中的物件檔*filename_1*中定義符號也一樣。 請移除 `__declspec(dllimport)` 修飾詞，以解決這個警告。

## <a name="remarks"></a>備註

警告 LNK4286 是[連結器工具警告 LNK4217](linker-tools-warning-lnk4217.md)的較通用版本。 當連結器可以分辨哪個物件檔案參考符號，但不是哪一個函式時，就會產生警告 LNK4286。

若要解析 LNK4286，請從*filename_2*中參考之*符號*的向前宣告中移除 `__declspec(dllimport)` 的宣告修飾詞。

雖然最後產生的程式碼會正確運作，但是為了呼叫匯入函式所產生的程式碼，比直接呼叫函數的效率更低。 當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項進行編譯時，不會出現這個警告。

如需匯入和匯出資料宣告的詳細資訊，請參閱[dllexport、dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="see-also"></a>另請參閱

[連結器工具警告 LNK4049](linker-tools-warning-lnk4049.md) \
[連結器工具警告 LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)
