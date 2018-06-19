---
title: 編譯器警告 （層級 1） C4627 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcde9e6707465fd95dbcb10e073a852624f0de0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284182"
---
# <a name="compiler-warning-level-1-c4627"></a>編譯器警告 (層級 1) C4627
'\<識別項 >': 尋找先行編譯標頭使用時略過  
  
 當搜尋時使用先行編譯標頭位置，編譯器遇到`#include`指示詞*\<識別碼 >* include 檔。 編譯器會忽略`#include`指示詞，但發出警告**C4627**如果先行編譯標頭尚未包含*\<識別碼 >* include 檔。  
  
## <a name="see-also"></a>另請參閱  
 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)