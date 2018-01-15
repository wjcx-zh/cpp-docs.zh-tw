---
title: "Varargs |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3d22a5c3f20480d1e904ec8e087114385ba7ee9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="varargs"></a>Varargs
如果將參數傳遞透過 varargs （例如，省略引數），基本上是正常的參數傳遞適用於包括溢出的第五個和後續引數。 它負責再次被呼叫端的傾印的引數，其位址。 只有浮點數值整數和浮點暫存器將會包含浮點值萬一被呼叫端必須是整數暫存器中的數值。  
  
## <a name="see-also"></a>請參閱  
 [呼叫慣例](../build/calling-convention.md)