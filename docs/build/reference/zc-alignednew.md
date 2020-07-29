---
title: /Zc:alignedNew (C++17 溢出對齊配置)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: f036c2d7bc4619685d2763702f447476e8e1a1e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217190"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (C++17 溢出對齊配置)

啟用 c + + 17 過度對齊的易失 **`new`** 儲存體配置，大於大小上限標準對齊類型的預設值，**最大 \_ 對齊 \_ t**。

## <a name="syntax"></a>語法

> **/Zc： alignedNew** \[-]

## <a name="remarks"></a>備註

MSVC 編譯器與程式庫支援 C++17 標準溢出對齊的動態記憶體配置。 當您指定 **/zc： alignedNew**選項時，動態配置（例如）會 `new Example;` 遵循*範例*的對齊方式，即使大於，也會影響 `max_align_t` 任何基本類型所需的最大對齊。 當配置的類型對齊不超過原始運算子所保證的對齊時 **`new`** （可做為預先定義的宏** \_ \_ STDCPP \_ 預設 \_ 新 \_ \_ \_ 對齊**的值），語句 `new Example;` 會導致呼叫， `::operator new(size_t)` 如同在 c + + 14 中的一樣。 當對齊大於** \_ \_ STDCPP \_ 預設的 \_ 新 \_ 對齊 \_ \_ **時，執行會改為使用取得記憶體 `::operator new(size_t, align_val_t)` 。 同樣地，刪除溢出對齊的類型會叫用 `::operator delete(void*, align_val_t)` 或有大小的 delete 特徵標記 `::operator delete(void*, size_t, align_val_t)`。

**/Zc:alignedNew** 選項只能在 [/std:c++17](std-specify-language-standard-version.md) 或 [/std:c++latest](std-specify-language-standard-version.md) 啟用時使用。 在 **/std:c++17** 或 **/std:c++latest** 下，根據預設，會啟用 **/Zc:alignedNew** 以遵循 ISO C++17 標準。 如果您執行運算子的唯一理由 **`new`** **`delete`** 是要支援過度對齊的配置，您可能不再需要此程式碼以 c + + 17 模式。 **`new`** **`delete`** 當您使用 **/std：： c + + 17**或 **/std： c + + 最新版本**時，若要關閉此選項，並還原為 c + + 14 的行為，請指定 **/zc： alignedNew-**。 如果您執行運算子 **`new`** ， **`delete`** 但尚未準備好要執行具有參數的過度對齊運算子 **`new`** 和多載 **`delete`** `align_val_t` ，請使用 **/zc： alignedNew-** 選項，以防止編譯器和標準程式庫產生過度對齊多載的呼叫。 [/permissive-](permissive-standards-conformance.md) 選項不會變更 **/Zc:alignedNew** 的預設設定。

自 Visual Studio 2017 15.5 版開始，提供 **/Zc:alignedNew** 的支援。

## <a name="example"></a>範例

這個範例 **`new`** **`delete`** 會顯示當設定 **/zc： alignedNew**選項時，運算子和運算子的行為。

```cpp
// alignedNew.cpp
// Compile by using: cl /EHsc /std:c++17 /W4 alignedNew.cpp
#include <iostream>
#include <malloc.h>
#include <new>

// "old" unaligned overloads
void* operator new(std::size_t size) {
    auto ptr = malloc(size);
    std::cout << "unaligned new(" << size << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size) {
    std::cout << "unaligned sized delete(" << ptr << ", " << size << ")\n";
    free(ptr);
}

void operator delete(void* ptr) {
    std::cout << "unaligned unsized delete(" << ptr << ")\n";
    free(ptr);
}

// "new" over-aligned overloads
void* operator new(std::size_t size, std::align_val_t align) {
    auto ptr = _aligned_malloc(size, static_cast<std::size_t>(align));
    std::cout << "aligned new(" << size << ", " <<
        static_cast<std::size_t>(align) << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size, std::align_val_t align) {
    std::cout << "aligned sized delete(" << ptr << ", " << size <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

void operator delete(void* ptr, std::align_val_t align) {
    std::cout << "aligned unsized delete(" << ptr <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

struct alignas(256) OverAligned {}; // warning C4324, structure is padded

int main() {
    delete new int;
    delete new OverAligned;
}
```

此輸出通常適用於 32 位元的組建。 指標值會依據應用程式在記憶體中執行的位置而不同。

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

如需 Visual C++ 中一致性問題的相關資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md) (非標準行為)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 修改 [其他選項]**** 屬性，使其包含 **/Zc:alignedNew** 或 **/Zc:alignedNew-**，然後選擇 [確定]****。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
