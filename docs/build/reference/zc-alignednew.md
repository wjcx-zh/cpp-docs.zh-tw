---
title: /Zc:alignedNew （c + + 17 過度對齊配置）
ms.date: 02/28/2018
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 0e6cf408e56dd6e5bc262c39dda460253a32dfc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662458"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew （c + + 17 過度對齊配置）

啟用支援 C + + 17 過度對齊**新**，在大於最大大小標準對齊類型的預設值的界限上對齊的動態記憶體配置**max\_對齊\_t**.

## <a name="syntax"></a>語法

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>備註

Visual Studio 15.5 版可讓編譯器和 C + + 17 標準過度對齊的動態記憶體配置的程式庫支援。 時 **/Zc:alignedNew**指定選項，例如動態配置`new Example;`遵守的對齊方式*範例*甚至是當它大於`max_align_t`，最大的對齊所需的任何基本類型。 已配置類型的對齊方式時不會超過所保證的原始運算子**新**，可做為預先定義的巨集值 **\_ \_STDCPP\_預設\_的新\_對齊\_\_**，陳述式`new Example;`的呼叫會導致`::operator new(size_t)`在 c++14 中所顯示的一樣。 當對齊大於 **\_ \_STDCPP\_預設\_新增\_對齊\_\_**，改為取得實作使用記憶體`::operator new(size_t, align_val_t)`。 同樣地，刪除過度對齊類型的叫用`::operator delete(void*, align_val_t)`大小的刪除簽章或`::operator delete(void*, size_t, align_val_t)`。

**/Zc:alignedNew**選項時，才可用[/std: c + + 17](std-specify-language-standard-version.md)或[/std: c + + 最新](std-specify-language-standard-version.md)已啟用。 底下 **/std: c + + 17**或 **/std: c + + 最新**， **/Zc:alignedNew**預設會啟用它以符合 ISO C + + 17 標準。 如果您的唯一原因實作運算子**新**並**刪除**是為了支援過度對齊的配置，您可能不再需要此 c++17 模式中的程式碼。 若要關閉此選項，並還原至 C + + 14 的行為**新**和**刪除**時 **/std::c + + 17**或 **/std: c + + 最新**指定時，指定**類型**。 如果您實作運算子**新**並**刪除**但是您不準備好要實作過度對齊的運算子**新**並**刪除**多載`align_val_t`參數，請使用**類型**過度對齊的多載的呼叫選項可防止產生的編譯器和標準程式庫。 [/Permissive--](permissive-standards-conformance.md)選項不會變更預設值 **/Zc:alignedNew**。

## <a name="example"></a>範例

這個範例會示範如何運算子**新**and 運算子**刪除**時，行為模式 **/Zc:alignedNew**選項設定。

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

此輸出是典型的 32 位元的組建。 在記憶體中執行應用程式根據的指標的值可能不同。

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

如需 Visual c + + 中一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/Zc:alignedNew**或是**類型**，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)
