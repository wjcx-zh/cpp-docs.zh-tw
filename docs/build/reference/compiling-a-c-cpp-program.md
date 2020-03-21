---
title: MSVC C/C++編譯器參考-Visual Studio
description: MSVC 編譯器工具組選項。
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: c75176b139895d7b00d88aca1c58604b47386894
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077369"
---
# <a name="compiling-a-cc-project"></a>編譯 C/C++專案

C 和C++編譯器選項可以在 Visual Studio IDE 或命令列中設定。

## <a name="in-visual-studio"></a>在 Visual Studio 中

您可以在 [Visual Studio**屬性頁**] 對話方塊中，設定每個專案的編譯器選項。 在左窗格中，依序選取 [設定] [**屬性**] 和 [ **C/C++**  ]，然後選擇 [編譯器選項] 分類。 每個編譯器選項的主題都會描述設定方式，以及各選項位於開發環境中的位置。 如需完整清單，請參閱[MSVC 編譯器選項](compiler-options.md)。

## <a name="from-the-command-line"></a>從命令列

您可以在下列位置設定編譯器 (CL.exe) 選項：

- [在命令列上](compiler-command-line-syntax.md)

- [在命令檔中](cl-command-files.md)

- [在 CL 環境變數中](cl-environment-variables.md)

每次叫用 CL 時，都會使用 CL 環境變數中指定的選項。 如果在 CL 環境變數或命令列中指名了某個命令檔，則會使用這個命令檔中所指定的選項。 與命令列或 CL 環境變數不同的是，命令檔可讓您使用多行選項和檔名。

編譯器選項是「由左至右」處理，而且在偵測到衝突時，會採用最後 (最右邊) 的選項。 CL 環境變數會在命令列之前處理，所以當 CL 與命令列之間發生任何衝突時，命令列具有優先權。

## <a name="additional-compiler-topics"></a>其他編譯器主題

- [MSVC 編譯器選項](compiler-options.md)

- [先行編譯標頭檔](../creating-precompiled-header-files.md)

- [CL 叫用連結器](cl-invokes-the-linker.md)

如需選擇編譯器主機和目標架構的詳細資訊，請參閱[ C++設定64位、x64 目標的專案](../configuring-programs-for-64-bit-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)
