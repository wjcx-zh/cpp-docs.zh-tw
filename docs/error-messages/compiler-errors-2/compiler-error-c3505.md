---
title: 編譯器錯誤 C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 0c67eb46208c35c1b11a74898107ad3c0e6e570d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200845"
---
# <a name="compiler-error-c3505"></a>編譯器錯誤 C3505

> 無法載入類型程式庫 '*guid*'

如果您是在64位電腦上執行32位、x86 裝載的跨編譯器以進行64位的 x64 目標，因為編譯器是在 WOW64 下執行，而且只能從32位登錄區讀取，可能會導致 C3505。

若要解決此錯誤，您可以建立您嘗試匯入之類型程式庫的32位和64位版本，然後再註冊兩者。  或者，您可以使用原生64位編譯器，這會要求您在 IDE 中變更**VC + + 目錄**屬性，以指向64位編譯器。

如需詳細資訊，請參閱：

- [如何：在命令列啟用 64 位元 Visual C++ 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [如何：將 Visual C++ 專案設定成以 64 位元 x64 平台為目標](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)
