---
title: "連結器工具警告 LNK4219 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4219
dev_langs: C++
helpviewer_keywords: LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1331931ba2fa7219a27b8f60b185dc3ab9310328
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4219"></a>連結器工具警告 LNK4219
修復名稱修復溢位。 目標 '目標 symbol name' 超出範圍，插入 thunk  
  
 連結器的情況下，其中位址或位移無法納入給定指令，因為目標符號太遠從指示的位置，插入 thunk。  
  
 您可能想要重新排列映像 (使用[/](../../build/reference/order-put-functions-in-order.md)選項，例如) 以避免額外的層級的間接取值。