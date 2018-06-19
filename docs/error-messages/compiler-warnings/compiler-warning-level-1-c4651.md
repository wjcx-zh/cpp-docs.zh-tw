---
title: 編譯器警告 （層級 1） C4651 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0015102a44b71f342b125532d20849590157ee0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283363"
---
# <a name="compiler-warning-level-1-c4651"></a>編譯器警告 (層級 1) C4651
指定先行編譯標頭，但不適用於目前的編譯 ' 定義 '  
  
 當產生先行編譯標頭，但不是在這個編譯中，未指定的定義。  
  
 定義將會生效先行編譯標頭，但是不在程式碼的其餘部分。  
  
 如果使用 /DSYMBOL 建置先行編譯標頭時，編譯器會產生這個警告，如果 /Yu 編譯沒有 /DSYMBOL。  /Yu 命令列中加入 /DSYMBOL 解決這個警告。