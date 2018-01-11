---
title: "NMAKE 嚴重錯誤 U1070 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1070
dev_langs: C++
helpviewer_keywords: U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5adf5321c96341cfce633a2329a52360be8a45da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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