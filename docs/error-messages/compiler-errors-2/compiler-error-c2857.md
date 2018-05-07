---
title: 編譯器錯誤 C2857 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bb2ec5047646bea420bf109f18a72d87a8f7c44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2857"></a>編譯器錯誤 C2857
'#include' 的原始程式檔中找不到與 /Ycfilename 命令列選項指定的陳述式  
  
 [/Yc](../../build/reference/yc-create-precompiled-header-file.md)選項指定未包含所要編譯原始程式檔中的包含檔案名稱。  
  
 這個錯誤可能因`#include`未編譯的條件式編譯區塊中的陳述式。