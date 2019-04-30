---
title: 連結器工具警告 LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: c6a5a0714e070e6cf3aee8efcdfbdfa07fa9ee69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399926"
---
# <a name="linker-tools-warning-lnk4086"></a>連結器工具警告 LNK4086

進入點 'function' 不是 'number' 個位元組的引數; __stdcall映像可能無法執行

DLL 的進入點必須是`__stdcall`。 請重新編譯函式搭配[/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)選項，或指定`__stdcall`或 WINAPI，當您定義的函式。