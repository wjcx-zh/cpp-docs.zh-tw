---
title: 連結器工具警告 LNK4219 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4219
dev_langs:
- C++
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59cb7376957b7985b7ae2335ea472171d490ff42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4219"></a>連結器工具警告 LNK4219
修復名稱修復溢位。 目標 '目標 symbol name' 超出範圍，插入 thunk  
  
 連結器的情況下，其中位址或位移無法納入給定指令，因為目標符號太遠從指示的位置，插入 thunk。  
  
 您可能想要重新排列映像 (使用[/](../../build/reference/order-put-functions-in-order.md)選項，例如) 以避免額外的層級的間接取值。