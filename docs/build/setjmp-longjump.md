---
title: setjmp longjump |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55cf6a2503367777464f09f92e3e3614c3d9f11b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379831"
---
# <a name="setjmplongjump"></a>setjmp/longjump
當您包含 setjmpex.h 或 setjmp.h 時，所有呼叫[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)會導致叫用解構函式，最後會呼叫回溯。  這不同於 x86、 finally 子句中包括 setjmp.h 結果並不被叫用解構函式所示。  
  
 呼叫`setjmp`會保留目前的堆疊指標、 非靜態暫存器，與 MxCsr 暫存器。  呼叫`longjmp`傳回最新`setjmp`呼叫站台重設堆疊指標、 非暫時性暫存器和 MxCsr 暫存器和回到狀態為保留的最新`setjmp`呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../build/calling-convention.md)