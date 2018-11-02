---
title: '/Zc: sizeddealloc （啟用全域調整大小解除配置函式）'
ms.date: 03/06/2018
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
ms.openlocfilehash: 160e90f0b068da6fe8330ac97dfd8bda52f05a38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536600"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc: sizeddealloc （啟用全域調整大小解除配置函式）

**/Zc: sizeddealloc**編譯器選項會告訴編譯器將優先呼叫 全域`operator delete`或是`operator delete[]`具有第二個類型參數的函式`size_t`時可用的物件大小。 這些函式可能會使用`size_t`參數來最佳化效能的解除配置器。

## <a name="syntax"></a>語法

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>備註

C + + 11 標準，您可以定義靜態成員函式`operator delete`並`operator delete[]`會採用第二個，`size_t`參數。 這些通常用來結合[new 運算子](../../cpp/new-operator-cpp.md)函式以實作更有效率的配置和解除配置器物件。 不過，C + + 11 未定義在全域範圍的解除配置函式的對等集合。 在 C + + 11，全域解除配置函式具有類型的第二個參數`size_t`會被視為 placement delete 函式。 他們必須藉由傳遞大小引數明確呼叫。

C + + 14 標準變更編譯器的行為。 當您定義全域`operator delete`並`operator delete[]`會採用第二個類型參數的`size_t`，編譯器不會叫用成員範圍版本和物件的大小是可用時，呼叫這些函式會優先。 編譯器會隱含地傳遞大小引數。 當編譯器無法判斷已解除配置物件的大小，會呼叫單一引數版本。 否則，請選擇解除配置函式，來叫用的版本一般的規則仍適用。 全域函式的呼叫可能會明確地指定前面加上範圍解析運算子 (`::`) 的解除配置函式呼叫。

根據預設，開始在 Visual Studio 2015 的 Visual c + + 會實作此 C + + 14 標準行為。 您可以藉由設定，明確指定這 **/zc: sizeddealloc**編譯器選項。 這表示可能最新變更。 使用  **/zc: sizeddealloc-** 選項，可保留的舊行為，例如，當您的程式碼會定義使用類型的第二個參數的位置 delete 運算子`size_t`。 具有類型的第二個參數的全域解除配置函式的預設 Visual Studio 程式庫實作`size_t`叫用的單一參數的版本。 如果您的程式碼提供只有單一參數全域 delete 運算子和 delete 運算子 []，全域大小的解除配置函式的預設程式庫實作叫用您的全域函式。

**/Zc: sizeddealloc**編譯器選項預設為開啟。 [/Permissive--](permissive-standards-conformance.md)選項並不會影響 **/zc: sizeddealloc**。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 從**組態**下拉式功能表中，選擇**所有組態**。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/zc: sizeddealloc**或是 **/zc: sizeddealloc-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
