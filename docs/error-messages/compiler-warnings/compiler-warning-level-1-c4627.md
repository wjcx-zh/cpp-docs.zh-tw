---
title: "編譯器警告 （層級 1） C4627 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 66d199b8dede21f94a963113341eb6426f66a807
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4627"></a>編譯器警告 (層級 1) C4627
'\<識別項 >': 尋找先行編譯標頭使用時略過  
  
 當搜尋時使用先行編譯標頭位置，編譯器遇到`#include`指示詞*\<識別碼 >* include 檔。 編譯器會忽略`#include`指示詞，但發出警告**C4627**如果先行編譯標頭尚未包含*\<識別碼 >* include 檔。  
  
## <a name="see-also"></a>請參閱  
 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)