---
title: "保留字 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
dev_langs: C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35f9a3e907b72b4b8cf8e673e771832ba3fc0527
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="reserved-words"></a>保留字
連結器會保留下列文字。 這些名稱可以當做引數中[模組定義陳述式](../../build/reference/module-definition-dot-def-files.md)才以雙引號括住的名稱 ("")。  
  
||||  
|-|-|-|  
|**APPLOADER**1|**INITINSTANCE**2|**預先載入**|  
|**基底**|**IOPL**|**私用**|  
|**程式碼**|**程式庫**1|**PROTMODE**2|  
|**不符合**|**LOADONCALL**1|**純**1|  
|**資料**|**LONGNAMES**2|**READONLY**|  
|**描述**|**可移動**1|**READWRITE**|  
|**DEV386**|**可移動**1|**REALMODE**1|  
|**可捨棄**|**多個**|**內建**|  
|**動態**|**名稱**|**RESIDENTNAME**1|  
|**僅執行**|**NEWFILES**2|**區段**|  
|**EXECUTEONLY**|**為 NODATA**1|**區段**|  
|**執行讀取**|**NOIOPL**1|**共用**|  
|**EXETYPE**|**NONAME**|**單一**|  
|**EXPORTS**|**不合格**1|**STACKSIZE**|  
|**固定**1|**NONDISCARDABLE**|**STUB**|  
|**函式**2|**無**|**版本**|  
|**HEAPSIZE**|**非共用**|**WINDOWAPI**|  
|**匯入**|**NOTWINDOWCOMPAT**1|**WINDOWCOMPAT**|  
|**非純虛擬**1|**物件**|**WINDOWS**|  
|**包含**2|**舊**1||  
  
 1 當它遇到這個詞彙，，連結器就會發出警告 （「 忽略 」）。 不過，word 會仍保留。  
  
 2 連結器會忽略這個字，但不會發出警告。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)