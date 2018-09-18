---
title: 連結器工具警告 LNK4102 |Microsoft Docs
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
ms.openlocfilehash: 9daaffc4ddfa9a869c2e60e2c05dc2b7e296d94b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031849"
---
# <a name="linker-tools-warning-lnk4102"></a>連結器工具警告 LNK4102

刪除解構函式 'name;' 的匯出映像可能無法正確執行

程式已嘗試匯出刪除解構函式。 產生的刪除可能會發生跨 DLL 界限，使得處理程序可以釋放它沒有自己的記憶體。 確定指定的符號不在.def 檔案中，所列，而且符號未列為的引數 **/ 匯入**或是 **/匯出**連結器命令列中的選項。

如果您重建 C 執行階段程式庫，您可以忽略此訊息。