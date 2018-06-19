---
title: NMAKE 嚴重錯誤 U1070 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1070
dev_langs:
- C++
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe39a5d6f6074596561cd8e32f7b9428bc60f6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327037"
---
# <a name="nmake-fatal-error-u1070"></a>NMAKE 嚴重錯誤 U1070
在巨集定義 '巨集名稱' 循環  
  
 給定的巨集定義包含巨集的定義包含指定的巨集。 循環的巨集不正確。  
  
## <a name="example"></a>範例  
 下列巨集定義  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 會導致下列錯誤：  
  
```  
cycle in macro definition 'TWO'  
```