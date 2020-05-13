---
title: /Zc:alignedNew (C++17 溢出對齊配置)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 041f62bbbf5f7a2750960d21d1534cf6daf4b874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335689"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (C++17 溢出對齊配置)

支援 C++17 溢出對齊的 **new**、動態記憶體配置，其對齊的邊界超過標準對齊類型 **max\_align\_t** 最大大小的預設。

## <a name="syntax"></a>語法

> **/Zc:對齊新**\[-*

## <a name="remarks"></a>備註

MSVC 編譯器與程式庫支援 C++17 標準溢出對齊的動態記憶體配置。 指定 **/Zc:對齊New**選項時,動態分配(如`new Example;`如表示 *)表示"示例*"的對齊方式,`max_align_t`即使它大於 ,則表示任何基本類型所需的最大對齊方式。 當分配的類型的對齊不超過原始運算符**new**保證的對齊方式時,該語句作為預定義的宏**\_\_STDCPP\_DEFAULT\_NEW\_對齊\_** 的值可用,該語句`new Example;`會導致調用`::operator new(size_t)`,就像在 C++14 中所做的那樣。 當對齊大於**\_\_STDCPP\_DEFAULT\_新\_對齊\_時**,實現將改為使用`::operator new(size_t, align_val_t)`獲取記憶體。 同樣地，刪除溢出對齊的類型會叫用 `::operator delete(void*, align_val_t)` 或有大小的 delete 特徵標記 `::operator delete(void*, size_t, align_val_t)`。

**/Zc:alignedNew** 選項只能在 [/std:c++17](std-specify-language-standard-version.md) 或 [/std:c++latest](std-specify-language-standard-version.md) 啟用時使用。 在 **/std:c++17** 或 **/std:c++latest** 下，根據預設，會啟用 **/Zc:alignedNew** 以遵循 ISO C++17 標準。 若您實作運算子 **new** 和 **delete** 的唯一理由是要支援溢出對齊的配置，在 C++17 模式中就不再需要這個程式碼。 若要在使用 **/std::c++17** 或 **/std:c++latest** 時關閉此選項，及還原 **new** 與 **delete** 的 C++14 行為，請指定 **/Zc:alignedNew-**。 若您在實作 **new** 和 **delete**，但還沒準備好實作具有 `align_val_t`參數的溢出對齊運算子 **new** 和 **delete** 多載，請使用 **/Zc:alignedNew-** 選項，避免編譯器和標準程式庫對溢出對齊多載產生呼叫。 [/permissive-](permissive-standards-conformance.md) 選項不會變更 **/Zc:alignedNew** 的預設設定。

自 Visual Studio 2017 15.5 版開始，提供 **/Zc:alignedNew** 的支援。

## <a name="example"></a>範例

本範例示範當設定了 **/Zc:alignedNew** 選項時，運算子 **new** 和運算子 **delete** 會有何行為。

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

1. 選擇**配置屬性** > **C/C++** > **命令列**屬性頁。

1. 修改 [其他選項]**** 屬性，使其包含 **/Zc:alignedNew** 或 **/Zc:alignedNew-**，然後選擇 [確定]****。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
