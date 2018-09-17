---
title: -volatile （volatile 關鍵字轉譯） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
dev_langs:
- C++
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4204d602d1390bf30080a800174426513faf0467
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723628"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (volatile 關鍵字轉譯)

指定如何[volatile](../../cpp/volatile-cpp.md)關鍵字是解譯。

## <a name="syntax"></a>語法

> **/volatile:**{**iso**|**ms**}

## <a name="arguments"></a>引數

**/volatile:iso**<br/>
選取嚴格`volatile`ISO 標準 c + + 語言所定義的語意。 暫時性存取時不保證 acquire/release 語意。 如果編譯器以 ARM 為目標，這是預設解譯`volatile`。

**/volatile: ms**<br/>
選取 Microsoft 擴充`volatile`記憶體順序保證超越 ISO 標準 c + + 語言的語意。 暫時性存取時保證 acquire/release 語意。 不過，此選項也會強制編譯器產生硬體記憶體屏障，可能會在 ARM 和其他弱式記憶體順序架構增加重大額外負荷。 如果編譯器以除了 ARM 以外的任何平台為目標，這是預設解譯`volatile`。

## <a name="remarks"></a>備註

我們強烈建議您改用 **/volatile:iso**以及明確的同步處理原始物件和編譯器內建時您正在處理跨執行緒共用的記憶體。 如需詳細資訊，請參閱 < [volatile](../../cpp/volatile-cpp.md)。

如果您移植現有的程式碼，或變更這個選項的專案，它可能有助於啟用警告[C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)識別受語意差異的程式碼位置。

沒有任何`#pragma`等於控制這個選項。

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>若要設定 /volatile 編譯器選項在 Visual Studio 中

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 在 **其他選項**方塊中，加入 **/volatile:iso**或 **/volatile: ms** ，然後選擇 **確定**或**套用**以儲存變更。

## <a name="see-also"></a>另請參閱

[volatile](../../cpp/volatile-cpp.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
