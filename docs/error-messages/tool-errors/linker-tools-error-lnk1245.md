---
title: 連結器工具錯誤 LNK1245 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47a1c2e5f7bf66946dcc5816d7a20fd485b59b45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299236"
---
# <a name="linker-tools-error-lnk1245"></a>連結器工具錯誤 LNK1245
無效的子系統 '' 指定子系統;/SUBSYSTEM 必須是 WINDOWS、 WINDOWSCE 或 CONSOLE  
  
 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)用於編譯的物件和其中一種下列情況為真：  
  
-   定義自訂的進入點 ([/ENTRY](../../build/reference/entry-entry-point-symbol.md))，例如，連結器無法推斷子系統。  
  
-   值已傳遞給[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) /clr 物件無效的連結器選項。  
  
 這兩種情況下，解決方式是指定有效的值以 /SUBSYSTEM 連結器選項。