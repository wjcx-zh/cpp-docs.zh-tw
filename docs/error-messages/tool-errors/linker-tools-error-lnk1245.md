---
title: "連結器工具錯誤 LNK1245 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 142d88489748f30308395d64f3db78178a9b856f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1245"></a>連結器工具錯誤 LNK1245
無效的子系統 '' 指定子系統;/SUBSYSTEM 必須是 WINDOWS、 WINDOWSCE 或 CONSOLE  
  
 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)用於編譯的物件和其中一種下列情況為真：  
  
-   定義自訂的進入點 ([/ENTRY](../../build/reference/entry-entry-point-symbol.md))，例如，連結器無法推斷子系統。  
  
-   值已傳遞給[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) /clr 物件無效的連結器選項。  
  
 這兩種情況下，解決方式是指定有效的值以 /SUBSYSTEM 連結器選項。