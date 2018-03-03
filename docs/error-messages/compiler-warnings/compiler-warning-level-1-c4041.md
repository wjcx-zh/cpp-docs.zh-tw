---
title: "編譯器警告 （層級 1） C4041 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 42779d33cad8fc867b08b412d2ded294360a0812
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4041"></a>編譯器警告 (層級 1) C4041
編譯器限制 : 瀏覽器資訊超出編譯器上限，已終止輸出  
  
 瀏覽器資訊超過編譯器限制。  
  
 這個警告可能是使用 [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (包含區域變數的瀏覽器資訊) 進行編譯所造成。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  使用 /Fr (未含區域變數的瀏覽器資訊) 進行編譯。  
  
2.  停用瀏覽器輸出 (不使用 /FR 或 /Fr 進行編譯)。