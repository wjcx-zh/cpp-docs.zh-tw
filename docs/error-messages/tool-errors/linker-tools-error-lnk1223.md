---
title: 連結器工具錯誤 LNK1223 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e50d29af6ac563fadd3a52e5b1d3d15201289083
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298648"
---
# <a name="linker-tools-error-lnk1223"></a>連結器工具錯誤 LNK1223
檔案無效或損毀：檔案包含無效的 .pdata 比重  
  
 針對使用 pdata 的 RISC 平台，如果編譯器發出的 .pdata 區段具有未排序的項目，會發生這個錯誤。  
  
 若要修正這個問題，請嘗試編譯而不[/GL （整個程式最佳化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)啟用。 空白的函式主體也可能在某些情況下導致此錯誤。