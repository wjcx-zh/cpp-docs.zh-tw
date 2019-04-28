---
title: /sdl （啟用協同程式支援）
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: c0c8c0183c356900ba8f95d39e427d56eb1ec96b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294996"
---
# <a name="await-enable-coroutine-support"></a>/sdl （啟用協同程式支援）

使用 **/await**編譯器選項，啟用協同程式的編譯器支援。

## <a name="syntax"></a>語法

> /await

## <a name="remarks"></a>備註

**/Await**編譯器選項可讓編譯器支援C++協同程式和關鍵字**co_await**， **co_yield**，並**co_return**. 根據預設，這個選項為關閉狀態。 在 Visual Studio 中的協同程式支援的相關資訊，請參閱[Visual Studio 小組部落格](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/)。 如需詳細的協同程式的標準提案的詳細資訊，請參閱[N4628 Working Draft、 技術規格C++協同程式的延伸模組](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf)。

**/Await**選項是在 Visual Studio 2015 開始提供。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟您的專案**屬性頁** 對話方塊。

1. 底下**組態屬性**，展開**C /C++** 資料夾，然後選擇 [**命令列**] 屬性頁。

1. 請輸入 **/await**中的編譯器選項**其他選項** 方塊中。 選擇 **[確定]** 或是**套用**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
