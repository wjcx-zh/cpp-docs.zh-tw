---
title: "編譯器警告 （層級 4） C4092 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4092
dev_langs:
- C++
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6eec21584ec56567b818f23e7dfcf5fb708369ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4092"></a>編譯器警告 （層級 4） C4092
sizeof 傳回 'unsigned long'  
  
 運算元`sizeof`運算子是非常大，因此`sizeof`傳回不帶正負號**長**。 Microsoft 擴充功能下會發生這個警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 在 ANSI 相容性 (/Za)，結果會改為截斷。