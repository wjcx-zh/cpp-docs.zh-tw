---
title: 編譯器錯誤 C2557 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2557
dev_langs:
- C++
helpviewer_keywords:
- C2557
ms.assetid: 48a33d82-aa16-4658-b346-2311fcb39864
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5402cb98d2cf315861ccb27aad3233b3bd370f8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2557"></a>編譯器錯誤 C2557
'identifier': 沒有建構函式無法初始化 private 和 protected 成員  
  
 只有成員和 Friend 才能將值指派給 private 和 protected 成員。 應該在類別建構函式中初始化非公用成員。