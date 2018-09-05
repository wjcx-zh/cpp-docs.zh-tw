---
title: Microsoft 擴充功能 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5699ce82a6e8537f12da50fdcb8288da167ecca3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752235"
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