---
title: /volatile (volatile 關鍵字轉譯)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: 7c2c1cd477b424f56e66bd9246e7bde76ad06120
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223781"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (volatile 關鍵字轉譯)

指定如何解讀[volatile](../../cpp/volatile-cpp.md)關鍵字。

## <a name="syntax"></a>語法

> **/volatile：**{**iso** | **ms**}

## <a name="arguments"></a>引數

**/volatile： iso**<br/>
選取 **`volatile`** ISO 標準 c + + 語言所定義的嚴格語義。 取得/釋放語義不保證在 volatile 存取上。 如果編譯器以 ARM 為目標，這是的預設轉譯 **`volatile`** 。

**/volatile： ms**<br/>
選取 Microsoft 擴充 **`volatile`** 的語義，這會新增高於 ISO Standard c + + 語言的記憶體排序保證。 取得/發行的語義會保證在變動性存取上。 不過，此選項也會強制編譯器產生硬體記憶體屏障，這可能會增加 ARM 和其他弱式記憶體排序架構的嚴重負擔。 如果編譯器以 ARM 以外的任何平臺為目標，這是的預設轉譯 **`volatile`** 。

## <a name="remarks"></a>備註

當您處理跨執行緒共用的記憶體時，強烈建議您搭配使用 **/volatile： iso**和明確的同步處理原始物件和編譯器內建函式。 如需詳細資訊，請參閱[volatile](../../cpp/volatile-cpp.md)。

如果您在專案的中間移植現有的程式碼或變更此選項，啟用警告[C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)可能有助於識別受到語義差異影響的程式碼位置。

沒有 `#pragma` 對等的可控制此選項。

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定/volatile 編譯器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，新增 **/volatile： iso**或 **/volatile： Ms** ，然後選擇 **[確定]** 或 [套用]**以儲存**變更。

## <a name="see-also"></a>另請參閱

[volatile](../../cpp/volatile-cpp.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
