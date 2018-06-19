---
title: Varargs |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7b71cd426bc89570f9d394f3e38dc7a002f6e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380504"
---
# <a name="varargs"></a>Varargs
如果將參數傳遞透過 varargs （例如，省略引數），基本上是正常的參數傳遞適用於包括溢出的第五個和後續引數。 它負責再次被呼叫端的傾印的引數，其位址。 只有浮點數值整數和浮點暫存器將會包含浮點值萬一被呼叫端必須是整數暫存器中的數值。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../build/calling-convention.md)