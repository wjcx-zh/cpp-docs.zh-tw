---
title: 編譯器警告 （層級 4） C4092 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4092
dev_langs:
- C++
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca145addc16306d613817643e363ecd9c95069a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4092"></a>編譯器警告 （層級 4） C4092
sizeof 傳回 'unsigned long'  
  
 運算元`sizeof`運算子是非常大，因此`sizeof`傳回不帶正負號**長**。 Microsoft 擴充功能下會發生這個警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 在 ANSI 相容性 (/Za)，結果會改為截斷。