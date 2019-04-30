---
title: 編譯器錯誤 C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 5730102371d00ebaf3ae05fdefb70184b58d7c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400327"
---
# <a name="compiler-error-c3505"></a>編譯器錯誤 C3505

> 無法載入類型程式庫 '*guid*'

如果您正在執行 32 位元、 x86 裝載跨編譯器的 64 位元，可能會造成 C3505，x64 上的 64 位元目標電腦，因為編譯器會在 WOW64 下執行，而且只能讀取 32 位元登錄區。

您可以藉由建置 32 位元和 64 位元版本的型別程式庫，您嘗試匯入，請解決這個錯誤，然後再進行登錄，讓兩者。  或者您可以使用原生的 64 位元編譯器，因此您必須變更您**VC + + 目錄**屬性在 IDE 中指向的 64 位元編譯器。

如需詳細資訊，請參閱：

- [如何：在命令列啟用 64 位元 Visual C++ 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [如何：將 Visual C++ 專案設定為以 64 位元 x64 平台為目標](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)