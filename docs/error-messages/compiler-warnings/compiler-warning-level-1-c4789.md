---
title: 編譯器警告 (層級 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36278615631d017db1d1c2fc4eecf8c1612892de
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518396"
---
# <a name="compiler-warning-level-1-c4789"></a>編譯器警告 (層級 1) C4789

> 大小*N*個位元組的緩衝區 '*identifier*' 將會溢出;會從 offset *L*開始寫入*M*個位元組

## <a name="remarks"></a>備註

使用特定的 C 執行時間（CRT）函式時， **C4789**會警告緩衝區溢位。 當傳遞參數或進行指派時，它也可以報告大小不符的情況。 如果在編譯時期已知資料大小，可能會出現警告。 這項警告是針對可能逃避一般的資料大小不符偵測的情況。

將資料複製到已知在編譯時期太小的資料區塊時， **C4789**會發出警告。

如果複製使用下列其中一個 CRT 函式的內建形式，就會發生警告：

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)、 [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

當您將參數轉換成較大的資料類型，然後從左值參考進行複製指派時，也會出現警告。

視覺C++效果可能會針對永遠不會執行的程式碼路徑產生此警告。 您可以使用 `#pragma` (如這個範例所示) 以暫時停用警告：

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

這個用法會防止C++視覺效果產生該特定程式碼區塊的警告。 `#pragma warning(push)` 會先保留現有的狀態，直到 `#pragma warning(disable: 4789)` 變更它。 `#pragma warning(pop)` 還原推入的狀態，並移除 `#pragma warning(disable:4789)` 的效果。 如需預處理器指示C++詞 `#pragma`的詳細資訊，請參閱[warning](../../preprocessor/warning.md)和 Pragma 指示詞[和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

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

int main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```
