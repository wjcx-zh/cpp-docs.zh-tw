---
title: "setjmp longjump |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 744b855d1b867507b54973f17e2a4f98b63e2b67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setjmplongjump"></a>setjmp/longjump
當您包含 setjmpex.h 或 setjmp.h 時，所有呼叫[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)會導致叫用解構函式，最後會呼叫回溯。  這不同於 x86、 finally 子句中包括 setjmp.h 結果並不被叫用解構函式所示。  
  
 呼叫`setjmp`會保留目前的堆疊指標、 非靜態暫存器，與 MxCsr 暫存器。  呼叫`longjmp`傳回最新`setjmp`呼叫站台重設堆疊指標、 非暫時性暫存器和 MxCsr 暫存器和回到狀態為保留的最新`setjmp`呼叫。  
  
## <a name="see-also"></a>請參閱  
 [呼叫慣例](../build/calling-convention.md)