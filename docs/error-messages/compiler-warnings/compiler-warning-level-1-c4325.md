---
title: 編譯器警告 （層級 1） C4325 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 936433987f823ae7d5d22cfd075f188dd5d4b1e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277640"
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
  
## <a name="see-also"></a>另請參閱  
 [section](../../preprocessor/section.md)