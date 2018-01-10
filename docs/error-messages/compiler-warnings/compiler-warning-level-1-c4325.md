---
title: "編譯器警告 （層級 1） C4325 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4325
dev_langs: C++
helpviewer_keywords: C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab31150efc02601d7392470198e162e979ac4917
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4325"></a>編譯器警告 (層級 1) C4325
**忽略標準區段 '**   
 ***區段*' 忽略**  
  
 您可能不會變更標準區段的屬性。 例如:   
  
```  
#pragma section(".sdata", long)  
```  
  
 這會覆寫`.sdata`使用標準區段**簡短**資料型別有**長**資料型別。  
  
 包含標準區段不能變更其屬性，  
  
-   .data  
  
-   .sdata  
  
-   .bss  
  
-   .sbss  
  
-   .text  
  
-   .const  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 稍後可能會加入額外的區段。  
  
## <a name="see-also"></a>請參閱  
 [section](../../preprocessor/section.md)