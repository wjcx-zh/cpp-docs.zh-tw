---
title: 連結器工具警告 LNK4102 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16d13dcbc6d15efd7cf3a7ea0a310de4ab7b0c93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302642"
---
# <a name="linker-tools-warning-lnk4102"></a>連結器工具警告 LNK4102
刪除解構函式 'name;' 的匯出映像可能無法正確執行  
  
 程式已嘗試匯出刪除解構函式。 產生刪除可能會發生跨 DLL 界限，使得處理程序可以釋放並未擁有的記憶體。 請確定指定的符號未列出在.def 檔案中，而且符號並未列為引數的 **/匯入**或 **/EXPORT**連結器命令列中的選項。  
  
 如果您要重建 C 執行階段程式庫，您可以忽略此訊息。