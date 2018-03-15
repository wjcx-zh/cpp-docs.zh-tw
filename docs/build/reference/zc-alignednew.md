---
title: "/Zc:alignedNew （c + + 17 過度對齊的配置） |Microsoft 文件"
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:alignedNew
dev_langs:
- C++
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d645534c398628afa533770d44094d23ca0325a5
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew （c + + 17 過度對齊的配置）

啟用支援 C + + 17 過度對齊**新**，動態記憶體配置類型的預設大小最大值的標準對齊，大於界限上對齊**max\_對齊\_t**.

## <a name="syntax"></a>語法

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>備註

Visual Studio 版本 15.5 可讓編譯器和 C + + 17 標準過度對齊動態記憶體配置的程式庫支援。 當**/Zc:alignedNew**指定選項，例如動態配置`new Example;`遵守的對齊方式*範例*即使它是大於`max_align_t`，最大的對齊所需的任何基本類型。 配置類型的對齊方式時不會超過由原始運算子保證**新**可用做為預先定義的巨集的值、  **\_ \_STDCPP\_預設\_新增\_對齊\_\_**，陳述式`new Example;`呼叫會導致`::operator new(size_t)`在 C + + 14 中所顯示的一樣。 當對齊大於 **\_ \_STDCPP\_預設\_新增\_對齊\_\_**，實作改為取得使用記憶體`::operator new(size_t, align_val_t)`。 同樣地，刪除過度對齊類型會叫用`::operator delete(void*, align_val_t)`或可調整大小的刪除簽章`::operator delete(void*, size_t, align_val_t)`。

**/Zc:alignedNew**選項時，才可以使用[/std:c + + 17](std-specify-language-standard-version.md)或[/std:c + + 最新](std-specify-language-standard-version.md)已啟用。 在下**/std:c + + 17**或**/std:c + + 最新**， **/Zc:alignedNew**以符合 ISO C + + 17 標準預設會啟用。 如果您的唯一原因實作運算子**新**和**刪除**是為了支援過度對齊的配置，您可能不再需要這個程式碼的 C + + 17 模式。 若要關閉此選項，並還原至 C + + 14 的行為**新**和**刪除**時**/std::c + + 17**或**/std:c + + 最新**指定時，指定**/Zc:alignedNew-**。 如果您實作運算子**新**和**刪除**，但是您不準備好要實作過度對齊的運算子**新**和**刪除**具有多載，`align_val_t`參數，使用**/Zc:alignedNew-**過度對齊的多載的呼叫選項可防止編譯器和標準程式庫產生。 [/ 寬鬆-](permissive-standards-conformance.md)選項不會變更預設值為**/Zc:alignedNew**。

## <a name="example"></a>範例

這個範例示範如何運算子**新**和運算子**刪除**時，行為模式**/Zc:alignedNew**選項設定。

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

此輸出是常見的 32 位元的組建。 在記憶體中執行應用程式基礎的指標的值不同。

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

如需 Visual c + + 中一致性問題的資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括**/Zc:alignedNew**或**/Zc:alignedNew-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)  
