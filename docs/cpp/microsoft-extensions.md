---
title: Microsoft 擴充功能
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592201"
---
# <a name="microsoft-extensions"></a>Microsoft 擴充功能

*asm 陳述式*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm***組譯碼指令* **;**<sub>選擇  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {***組件指示清單***};**<sub>選擇    </sub>

*組件指示清單*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*組譯碼指令* **;**<sub>選擇</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*組譯碼指令* **;***組件指示清單* **;**<sub>選擇</sub>

*ms 修飾詞清單*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms 修飾詞* *ms 修飾詞清單*<sub>選擇</sub>

*ms 修飾詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__syscall** （保留供未來實作）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__oldcall** （保留供未來實作）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__unaligned** （保留供未來實作）<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*基礎修飾詞*

*基礎修飾詞*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *型別* **)**

*型別*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*名稱*