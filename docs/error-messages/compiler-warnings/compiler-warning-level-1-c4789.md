---
title: 編譯器警告 (層級 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36a5032098c5caabb1b050833e487fd58679a782
ms.sourcegitcommit: 6e4dd21759caaed262a7255735cf8d6e8fb9f4d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476847"
---
# <a name="compiler-warning-level-1-c4789"></a>編譯器警告 (層級 1) C4789

> 緩衝區 '*識別碼*' 的大小*N*位元組會溢位;*M*將位移處開始寫入位元組*L*

## <a name="remarks"></a>備註

**C4789**時使用特定的 C 執行階段 (CRT) 函式會警告緩衝區溢位。 傳遞的參數，或進行指派時，它也會報告大小不符。 如果在編譯時期已知的資料大小可以警告。 這項警告是針對可能逃避一般的資料大小不符偵測的情況。

**C4789**警告時資料複製到得太小，在編譯時期已知的資料區塊。

如果該複本會使用其中一個 CRT 函式的內建形式，就會發生警告：

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)， [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

當您轉換為較大的資料類型的參數，然後再進行從 lvalue 參考複製指派時，也會出現警告。

Visual c + + 可能會產生這個警告，永遠不會執行的程式碼路徑。 您可以使用 `#pragma` (如這個範例所示) 以暫時停用警告：

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

這個慣用語可避免 Visual c + + 產生該特定程式碼區段的警告。 `#pragma warning(push)` 會先保留現有的狀態，直到 `#pragma warning(disable: 4789)` 變更它。 `#pragma warning(pop)` 還原推入的狀態，並移除 `#pragma warning(disable:4789)` 的效果。 如需 c + + 前置處理器指示詞`#pragma`，請參閱 <<c2> [ 警告](../../preprocessor/warning.md)並[Pragma 指示詞和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

## <a name="example"></a>範例

下列範例會產生 C4789。

```cpp
// C4789.cpp
// compile with: /Oi /W1 /c
#include <string.h>
#include <stdio.h>

int main()
{
    char a[20];
    strcpy(a, "0000000000000000000000000\n");   // C4789

    char buf2[20];
    memset(buf2, 'a', 21);   // C4789

    char c;
    wchar_t w = 0;
    memcpy(&c, &w, sizeof(wchar_t));
}
```

## <a name="example"></a>範例

下列範例也會產生 C4789。

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

void main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```