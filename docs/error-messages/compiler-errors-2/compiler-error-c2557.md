---
title: "編譯器錯誤 C2557 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2557
dev_langs:
- C++
helpviewer_keywords:
- C2557
ms.assetid: 48a33d82-aa16-4658-b346-2311fcb39864
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 044bfcaeb70a2a1ab3b4a349bf9019879210e82b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2557"></a>編譯器錯誤 C2557
'identifier': 沒有建構函式無法初始化 private 和 protected 成員  
  
 只有成員和 Friend 才能將值指派給 private 和 protected 成員。 應該在類別建構函式中初始化非公用成員。