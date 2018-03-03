---
title: "連結器工具錯誤 LNK1223 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c330077e8de73b8eeb71b0a418eb89d2ec0ebfdc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1223"></a>連結器工具錯誤 LNK1223
檔案無效或損毀：檔案包含無效的 .pdata 比重  
  
 針對使用 pdata 的 RISC 平台，如果編譯器發出的 .pdata 區段具有未排序的項目，會發生這個錯誤。  
  
 若要修正這個問題，請嘗試編譯而不[/GL （整個程式最佳化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)啟用。 空白的函式主體也可能在某些情況下導致此錯誤。