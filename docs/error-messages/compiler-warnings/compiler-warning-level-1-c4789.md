---
title: 編譯器警告 (層級 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 1e089c45598a53ff337e389feb2a6983a2997041
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684621"
---
# <a name="compiler-warning-level-1-c4789"></a>編譯器警告 (層級 1) C4789

> 大小*N*個位元組的緩衝區 '*identifier*' 將會被溢出;*M*位元組將會從位移*L*開始寫入

## <a name="remarks"></a>備註

使用特定的 C 執行時間 (CRT) 函數時， **C4789**會警告緩衝區溢位。 它也可以在傳遞或指派參數時報告大小不符的情況。 如果資料大小在編譯時期是已知的，則可能會出現警告。 這項警告是針對可能逃避一般的資料大小不符偵測的情況。

當資料複製到已知在編譯時期太小的資料區塊時， **C4789**會發出警告。

如果複製使用下列其中一個 CRT 函式的內建格式，就會發生警告：

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)、 [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

當您將參數轉換成較大的資料類型，然後從左值參考進行複製指派時，也會出現警告。

Visual C++ 可能會為永遠不會執行的程式碼路徑產生此警告。 您可以使用 `#pragma` (如這個範例所示) 以暫時停用警告：

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

這種用法會讓 Visual C++ 不會產生該特定程式碼區塊的警告。 `#pragma warning(push)` 會先保留現有的狀態，直到 `#pragma warning(disable: 4789)` 變更它。 `#pragma warning(pop)` 還原推入的狀態，並移除 `#pragma warning(disable:4789)` 的效果。 如需 c + + 預處理器指示詞的詳細資訊 `#pragma` ，請參閱 [Warning](../../preprocessor/warning.md) 和 Pragma 指示詞 [和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

## <a name="examples"></a>範例

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
