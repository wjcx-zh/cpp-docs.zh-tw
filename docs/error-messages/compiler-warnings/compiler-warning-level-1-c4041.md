---
title: 編譯器警告 （層級 1） C4041 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd8c933522e523329c41ebe666a5a7e3c198cb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4041"></a>編譯器警告 (層級 1) C4041
編譯器限制 : 瀏覽器資訊超出編譯器上限，已終止輸出  
  
 瀏覽器資訊超過編譯器限制。  
  
 這個警告可能是使用 [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (包含區域變數的瀏覽器資訊) 進行編譯所造成。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  使用 /Fr (未含區域變數的瀏覽器資訊) 進行編譯。  
  
2.  停用瀏覽器輸出 (不使用 /FR 或 /Fr 進行編譯)。