---
title: "連結器工具警告 LNK4102 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80efad60da9f6742110811a5cf4c12f07c7def67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4102"></a>連結器工具警告 LNK4102
刪除解構函式 'name;' 的匯出映像可能無法正確執行  
  
 程式已嘗試匯出刪除解構函式。 產生刪除可能會發生跨 DLL 界限，使得處理程序可以釋放並未擁有的記憶體。 請確定指定的符號未列出在.def 檔案中，而且符號並未列為引數的**/匯入**或**/EXPORT**連結器命令列中的選項。  
  
 如果您要重建 C 執行階段程式庫，您可以忽略此訊息。