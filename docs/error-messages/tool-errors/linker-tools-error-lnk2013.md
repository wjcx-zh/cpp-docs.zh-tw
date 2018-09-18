---
title: 連結器工具錯誤 LNK2013 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04ce4ca8079317da090cf05d43f41e4e40a6b19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041736"
---
# <a name="linker-tools-error-lnk2013"></a>連結器工具錯誤 LNK2013

修復類型修復溢位。 目標 'symbol name' je mimo rozsah

連結器無法容納所需的位址或 offset 成指定的指示，因為目標符號太遠而從指示的位置。

您可以解決這個問題，藉由建立多個映像或使用[/order](../../build/reference/order-put-functions-in-order.md)選項使指令和目標更接近。

符號名稱的使用者定義的符號 （和不是編譯器所產生的符號） 時，您也可以嘗試下列動作來解決這個錯誤：

- 變更靜態的函式為非靜態。

- 重新命名包含靜態的函式，呼叫端相同的程式碼區段。

使用`DUMPBIN /SYMBOLS`、 函式是否為靜態。