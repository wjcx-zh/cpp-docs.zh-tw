---
title: 連結器工具警告 LNK4086 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a2ee7660f0ad78d04f7edb191929296c8d47a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079228"
---
# <a name="linker-tools-warning-lnk4086"></a>連結器工具警告 LNK4086

進入點 'function' 不是 'number' 個位元組的引數; __stdcall映像可能無法執行

DLL 的進入點必須是`__stdcall`。 請重新編譯函式搭配[/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)選項，或指定`__stdcall`或 WINAPI，當您定義的函式。