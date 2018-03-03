---
title: "編譯器警告 （層級 1） C4651 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dce099d657341ebc957c95ab0cd14f508f9e36ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4651"></a>編譯器警告 (層級 1) C4651
指定先行編譯標頭，但不適用於目前的編譯 ' 定義 '  
  
 當產生先行編譯標頭，但不是在這個編譯中，未指定的定義。  
  
 定義將會生效先行編譯標頭，但是不在程式碼的其餘部分。  
  
 如果使用 /DSYMBOL 建置先行編譯標頭時，編譯器會產生這個警告，如果 /Yu 編譯沒有 /DSYMBOL。  /Yu 命令列中加入 /DSYMBOL 解決這個警告。