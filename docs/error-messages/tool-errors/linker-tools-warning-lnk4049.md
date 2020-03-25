---
title: 連結器工具警告 LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: a8e4416eafd47f584de4ab1c83aa7303cab0440a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194131"
---
# <a name="linker-tools-warning-lnk4049"></a>連結器工具警告 LNK4049

> 已匯入在 '*filename .obj*' 中定義的符號 '*symbol*'

已為*符號*指定[__declspec （dllimport）](../../cpp/dllexport-dllimport.md) ，即使符號是在相同影像中的物件檔*filename .obj*中定義也一樣。 請移除 `__declspec(dllimport)` 修飾詞，以解決這個警告。

## <a name="remarks"></a>備註

當您在一個目的檔中定義符號，並使用另一個物件檔案中的 `__declspec(dllimport)` 宣告修飾詞來參考它時，連結器就會產生此警告。

警告 LNK4049 是[連結器工具警告 LNK4217](linker-tools-warning-lnk4217.md)的較通用版本。 當連結器無法判斷參考匯入符號的函式或物件檔案時，會產生警告 LNK4049。

產生 LNK4049 而不是 LNK4217 的常見情況如下：

- 使用[/INCREMENTAL](../../build/reference/incremental-link-incrementally.md)選項時。

- 使用[/ltcg](../../build/reference/ltcg-link-time-code-generation.md)選項時。

若要解決 LNK4049，請嘗試下列其中一個程式：

- 從觸發 LNK4049 之符號的向前宣告中移除 `__declspec(dllimport)` 修飾詞。 您可以使用**DUMPBIN**公用程式，在二進位影像中搜尋符號。 **DUMPBIN/SYMBOLS**參數會顯示影像的 COFF 符號表。 如需**DUMPBIN**公用程式的詳細資訊，請參閱[DUMPBIN 參考](../../build/reference/dumpbin-reference.md)。

- 暫時停用增量連結和整個程式優化。 重新編譯時，應用程式會產生警告 LNK4217，其中包含參考已匯入符號之函式的名稱。 從匯入的符號中移除 `__declspec(dllimport)` 的宣告修飾詞，並視需要重新啟用累加連結或整個程式優化。

雖然最後產生的程式碼會正確運作，但是為了呼叫匯入的函式所產生的程式碼，比直接呼叫函式的效率更低。 當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項進行編譯時，不會出現這個警告。

如需匯入和匯出資料宣告的詳細資訊，請參閱[dllexport、dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="example"></a>範例

連結下列兩個模組將會產生 LNK4049。 第一個模組會產生一個包含單一匯出函數的物件檔案。

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

第二個模組會產生一個物件檔案，其中包含第一個模組中所匯出函式的向前宣告，以及在 `main` 函式內呼叫此函式。 將此模組與第一個模組連結，將會產生 LNK4049。 請從宣告中移除 `__declspec(dllimport)` 修飾詞，以解決警告。

```cpp
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>另請參閱

[連結器工具警告 LNK4217](linker-tools-warning-lnk4217.md) \
[連結器工具警告 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)
