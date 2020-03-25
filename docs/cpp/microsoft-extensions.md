---
title: Microsoft 擴充功能
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: a2d0846e55122f177b4868c2e80c4f1d27267f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179402"
---
# <a name="microsoft-extensions"></a>Microsoft 擴充功能

*asm-語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm***assembly-指示* **;** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *assembly-指令清單* **};** <sub>opt</sub>

*元件-指令清單*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-指示* **;** <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-指令* **;** *元件指令清單* **;** <sub>opt</sub>

*毫秒-修飾詞清單*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms-修飾*詞 *--修飾詞清單*<sub>opt</sub>

*毫秒-修飾*詞：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__syscall** （保留供未來的實施）<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__oldcall** （保留供未來的實施）<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__unaligned** （保留供未來的實施）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*為基礎的修飾*詞

以*為基礎的修飾*詞：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__based （** *根據*型別 **）**

*型別：*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*名稱*
