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
ms.openlocfilehash: 02871622242930d7419fda16f4d106fccb2056f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316635"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (volatile 關鍵字轉譯)

指定如何[volatile](../../cpp/volatile-cpp.md)關鍵字是解譯。

## <a name="syntax"></a>語法

> **/volatile:**{**iso**|**ms**}

## <a name="arguments"></a>引數

**/volatile:iso**<br/>
選取嚴格`volatile`ISO 標準所定義的語意C++語言。 暫時性存取時不保證 acquire/release 語意。 如果編譯器以 ARM 為目標，這是預設解譯`volatile`。

**/volatile:ms**<br/>
選取 Microsoft 擴充`volatile`語意，記憶體順序保證超越 ISO 標準C++語言。 暫時性存取時保證 acquire/release 語意。 不過，此選項也會強制編譯器產生硬體記憶體屏障，可能會在 ARM 和其他弱式記憶體順序架構增加重大額外負荷。 如果編譯器以除了 ARM 以外的任何平台為目標，這是預設解譯`volatile`。

## <a name="remarks"></a>備註

我們強烈建議您改用 **/volatile:iso**以及明確的同步處理原始物件和編譯器內建時您正在處理跨執行緒共用的記憶體。 如需詳細資訊，請參閱 < [volatile](../../cpp/volatile-cpp.md)。

如果您移植現有的程式碼，或變更這個選項的專案，它可能有助於啟用警告[C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)識別受語意差異的程式碼位置。

沒有任何`#pragma`等於控制這個選項。

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>若要設定 /volatile 編譯器選項在 Visual Studio 中

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **C /C++** > **命令列**屬性頁。

1. 在 **其他選項**方塊中，加入 **/volatile:iso**或 **/volatile: ms** ，然後選擇 **確定**或**套用**以儲存變更。

## <a name="see-also"></a>另請參閱

[volatile](../../cpp/volatile-cpp.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
